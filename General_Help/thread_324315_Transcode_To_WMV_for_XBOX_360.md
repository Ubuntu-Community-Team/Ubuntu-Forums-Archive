---
title: "Transcode To WMV for XBOX 360"
date: 2006-12-23
forum: General Help
---

### Post by Ramorous on 2006-12-23
I've tried VLC with the proper sout string, however I cannot get the WMA encoding to work. I've also tried VLC through WINE and still the same persists.

The video does transcode, but the audio is not.

Anyone have any suggestions how to get this done?

```
AVIFILE=$1
vlc -vvv "$AVIFILE" --sout-ffmpeg-qscale 1 ':sout=#transcode{vcodec=WMV2,scale=1,acodec=wma,ab=96,channels=2}:duplicate{dst=std{access=file,mux=asf,dst="/shared/videos/tmpfile.wmv"}}' vlc:quit
mv /shared/videos/tmpfile.wmv /shared/videos/$AVIFILE.wmv
rm $AVIFILE
```

---

