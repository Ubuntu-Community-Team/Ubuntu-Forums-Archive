---
title: "recursive video conversion?"
date: 2012-10-24
forum: General Help
---

### Post by sohlinux on 2012-10-24
I have a folder of videos avis, I want to make a preview of each video and copy the preview in to a new folder of the same name as the original folder (recursively)

I can make individual video previews ok with the following command
ffmpeg -i video.avi -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy video_copy.avi

but I need to create the same folder name and copy the video in to that folder

so if the original video is located in /videos/video_A01/video.avi the preview needs to be copied to a new folder called /videos_previews/video_A01/


thanks

---

### Post by danielbauwens on 2012-10-24
So if I understand correctly, you want, a folder "videos", and a new folder called "videos_preview" and in both folders the video?

Just make in the folder that holds the folder "videos" a new folder called "videos_preview" and copy your videos in there.

---

### Post by sohlinux on 2012-10-24
> **danielbauwens said:**
> So if I understand correctly, you want, a folder "videos", and a new folder called "videos_preview" and in both folders the video?

Just make in the folder that holds the folder "videos" a new folder called "videos_preview" and copy your videos in there.

but I want to do it recursively, the folder has 100 different folders inside it, in each folder there is a video

I want to make a preview video of all 100 videos and automatically copy them to a new folder called /video_previews/sub_folder but the new sub folder names must be the same names as the original folder

original folder /videos/video_A01/video.avi

make video preview
make folder with same name
copy video preview in to new folder
/videos_previews/video_A01/video.avi

the result will be 100 new folders in /videos_previews/, the same folder structure as the original but only containing the preview videos

some folders may have spaces and not all video names are the same

---

### Post by danielbauwens on 2012-10-24
Sorry I do not know how to automatically copy files and make folders :/

Wish you good luck finding an answer that helps.

---

### Post by Vaphell on 2012-10-24
```
#!/bin/bash

videos="$HOME/test/preview/videos/"
previews="$HOME/test/preview/previews/"

while IFS= read -rd '' f
do
  dest="$previews${f#$videos}"
  echo "file: '$f'"
  mkdir -pv "${dest%/*}"
  echo "target: '${dest}'"
  echo "command:"
  echo ffmpeg -i "'$f'" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "'$dest'"
  # uncomment line below
  # ffmpeg -i "$f" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "$dest"
  echo
done < <( find "$videos" -iname '*.avi' -type f -print0 )
```

for obvious reasons previews shouldn't be located inside videos
previews should be created in their final location right off the bat, so there won't be preview files in source folders. If you want to have them, add something like
```
cp "dest" "${f%.*}(preview).{f##*.}"
```
after ffmpeg

---

### Post by sohlinux on 2012-10-24
> **Vaphell said:**
> ```
#!/bin/bash

videos="$HOME/test/preview/videos/"
previews="$HOME/test/preview/previews/"

while IFS= read -rd '' f
do
  dest="$previews${f#$videos}"
  echo "file: '$f'"
  mkdir -pv "${dest%/*}"
  echo "target: '${dest}'"
  echo "command:"
  echo ffmpeg -i "'$f'" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "'$dest'"
  # uncomment line below
  # ffmpeg -i "$f" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "$dest"
  echo
done < <( find "$videos" -iname '*.avi' -type f -print0 )
```

for obvious reasons previews shouldn't be located inside videos
previews should be created in their final location right off the bat, so there won't be preview files in source folders. If you want to have them, add something like
```
cp "dest" "${f%.*}(preview).{f##*.}"
```
after ffmpeg

thanks but that gave an error

root@server [/]# sh /scripts/2.sh
/scripts/2.sh: line 17: syntax error near unexpected token `<'
/scripts/2.sh: line 17: `done < <( find "$videos" -iname *.avi -type f -print0 )'
root@server [/]#

I dont need previews in the source

thanks

---

### Post by Vaphell on 2012-10-24
```
root@server [/]# **sh** /scripts/2.sh
```

ignoring the fact that running as root to perform trivial operations on files doesn't make any sense, the script should be run with bash, not sh - note the hashbang line
```
#!/bin/bash
```

just chmod it and run without mentioning shell
```
chmod +x /scripts/2.sh
/scripts/2.sh

```

---

### Post by sohlinux on 2012-10-24
> **Vaphell said:**
> ```
root@server [/]# **sh** /scripts/2.sh
```

ignoring the fact that running as root to perform trivial operations on files doesn't make any sense, the script should be run with bash, not sh - note the hashbang line
```
#!/bin/bash
```

just chmod it and run without mentioning shell
```
chmod +x /scripts/2.sh
/scripts/2.sh

```

same problem

chmod +x /scripts/2.sh

me@server [/]# /scripts/2.sh
/scripts/2.sh: line 17: syntax error near unexpected token `<( find "$videos" -iname *.avi -type f -print0 )'
/scripts/2.sh: line 17: `done <( find "$videos" -iname *.avi -type f -print0 )'

---

### Post by Vaphell on 2012-10-24
how many < you got there in the last line? there should be 2
```
done <[COLOR="MediumTurquoise"]space[/COLOR]<( ... )
```
could you paste the error msg and the last line of the script here wrapped in [co****de][/code]? loss of formatting makes it harder to notice minute details.

---

### Post by sohlinux on 2012-10-24
> **Vaphell said:**
> how many < you got there in the last line? there should be 2
```
done <[COLOR="MediumTurquoise"]space[/COLOR]<( ... )
```
could you paste the error msg and the last line of the script here wrapped in [co****de][/code]? loss of formatting makes it harder to notice minute details.



oh yes I missed out on one of the <

I need to run root because the videos are under chown root

but now it says 

```
 root@server [/]# /scripts/2.sh
find: `/root/data3/images/wm/': No such file or directory


```

looks like its adding /root to the beginning of /data3...

I want to copy the previews from /data3/images/wm/ to /data3/images/wm/previews/

so this is what I have

```

#!/bin/bash

videos="$HOME/data3/images/wm/"
previews="$HOME/data3/images/wm/previews/"

while IFS= read -rd '' f
do
  dest=$previews${f#$videos}
  echo "file: '$f'"
  mkdir -pv "${dest%/*}"
  echo "target: '${dest}'"
  echo "command:"
  echo ffmpeg -i "'$f'" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "'$dest'"
  # uncomment line below
  ffmpeg -i "$f" -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy "$dest"
  echo
done < <( find "$videos" -iname '*.avi' -type f -print0 )

```

---

### Post by sohlinux on 2012-10-24
removed $HOME and now it appears to be doing something but

```
root@server [/]# /scripts/2.sh

file: '/data3/images/wm/AVI-ABI/abi.avi'

mkdir: created directory `/data3/images/wm/previews'

mkdir: created directory `/data3/images/wm/previews/AVI-ABI'

target: '/data3/images/wm/previews/AVI-ABI/abi.avi'

command:

ffmpeg -i '/data3/images/wm/AVI-AB/abi.avi' -ss 00:05:0.0 -t 00:01:00.0 -vcodec copy -acodec copy '/data3/images/wm/previews/AVI-ABI/abi.avi'

FFmpeg version 0.6.5, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jan 29 2012 17:52:15 with gcc 4.4.5 20110214 (Red Hat 4.4.5-6)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC' --enable-avfilter --enable-avfilter-lavf --enable-libdc1394 --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg4 @ 0x21b79a0]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/data3/images/wm/AVI/abi.avi':
  Duration: 00:20:31.72, start: 0.000000, bitrate: 1632 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 128 kb/s
Output #0, avi, to '/data3/images/wm/previews/AVI-ABI/abi.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], q=2-31, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[avi @ 0x21bd6c0]st:1 error, non monotone timestamps 522 >= 522bitrate=   0.0kbits/s
av_interleaved_write_frame(): Operation not permitted


```


I suppose thats a problem related to the video format so the script stops, is there any way of skipping to the next if it encounters an error in the video?

---

### Post by Vaphell on 2012-10-24
apparently that *Press [q] to stop encoding* eats all input, that is all following file names (they are waiting in input queue for* while read* to get them but the interactive mode of ffmpeg empties it). I must say not providing straightforward, easy to use batch mode is retarded

[http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)

check if adding **< /dev/null** or** < /dev/tty** at the end of ffmpeg command will make the problem go away

---

### Post by sohlinux on 2012-10-24
> **Vaphell said:**
> apparently that *Press [q] to stop encoding* eats all input, that is all following file names (they are waiting in input queue for* while read* to get them but the interactive mode of ffmpeg empties it). I must say not providing straightforward, easy to use batch mode is retarded

[http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)

check if adding **< /dev/null** or** < /dev/tty** at the end of ffmpeg command will make the problem go away

awesome < /dev/null did the trick!

---

