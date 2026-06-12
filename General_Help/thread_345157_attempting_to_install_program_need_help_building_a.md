---
title: "attempting to install program need help building a tar.gz asap plz"
date: 2007-01-23
forum: General Help
---

### Post by shickidyshade on 2007-01-23
previous thread 
[http://ubuntuforums.org/showthread.php?t=344308](http://ubuntuforums.org/showthread.php?t=344308)

Hey guy the link that got me to here is above now i need different help 
the below is from and install file that  was packed in the tar.gz 
>   1) Type './configure' create the configuration (use './configure
--help' to have the configure options). 

'configure' can be launched from another directory than the ffmpeg
sources to put the objects at that place. In that case, use an
absolute path when launching 'configure',
e.g. /ffmpegdir/ffmpeg/configure.

2) Then type 'make' to build ffmpeg.

3) Type 'make install' to install ffmpeg and ffserver in
/usr/local/bin.
   


Ive never been able to build from scratch and i need this for a poject for school the location is on the desktop and the file name is
 ```
'/home/shade/Desktop/ffmpeg-0.4.9-pre1.tar.gz' 
```

any and all help is appreciated i hope to run this before i go to bed in four hours if not early tomorrow morning

---

### Post by bodhi.zazen on 2007-01-23
```
sudo aptitude install build-essential checkinstall
cd ~/Desktop
tar xzf ffmpeg-0.4.9-pre1.tar.gz
cd ffmpeg-0.4.9-pre1
./configure
make
sudo checkinstall
```

---

