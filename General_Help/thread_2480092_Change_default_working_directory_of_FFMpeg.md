---
title: "Change default working directory of FFMpeg?"
date: 2022-10-18
forum: General Help
---

### Post by xanizen on 2022-10-18
It seems to default to /home/[Username] directory.
I'd like it to default to a 'mounted partition', located under /media/parition1

In Microfsoft Windows, the ffmpeg file is a stand alone 60 MB file I can freely copy and paste to my 'working directory' of choice.
The ffmpeg file located in /usr/bin is a mere 300 KB in size. 
The largest file with ffmpeg in its name, at 10MB: /opt/XnView/lib/libffmpeg.so.5

Specifying 'default working directory' saves me the trouble of having to write out the full save/output path of the processed video file.

The closest 'solution' I found was performing: vim ~/.profile
But I'm not sure what to specify.

---

### Post by TheFu on 2022-10-18
Open a terminal, 
cd /media/parition1
ffmpeg ..... 

BTW, this works exactly the same in Windows, OSX, BSD, AIX, Solaris, HP-UX, DigitalUnix, Irix, and 20 other OSes ... plus Linux and Android.

---

