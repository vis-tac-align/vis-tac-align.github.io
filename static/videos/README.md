Drop rollout clips here, then uncomment the Rollouts section in index.html.

Encode for web (small, seekable, autoplays on iOS):

  ffmpeg -i IN.MOV -vf "scale=1280:-2" -c:v libx264 -preset slow -crf 26 \
         -pix_fmt yuv420p -movflags +faststart -an OUT.mp4

Notes:
  -an            strip audio; muted autoplay needs no track
  +faststart     moves the index to the front so playback starts before download
  yuv420p        required for Safari and for 10-bit phone footage
  crf 26         ~1-3 MB for a 10 s clip at 1280 wide

Keep the whole page under ~25 MB so it stays fast on a conference network.
