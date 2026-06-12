---
title: "DVDs will not play on 2 of my Ubuntu OS, but will on another ..."
date: 2023-08-22
forum: General Help
---

### Post by cwmoser on 2023-08-22
For the life of me I cannot figure out why I cannot play DVDs on two of my Ubuntu PCs.
All are running Ubuntu 22.04 Mate.

I've tried various players.  With mplayer it just dies.  With SMPlayer it outputs:
No protocol handler found to open URL computer:///hp....
The protocol is either unsupported, or was disabled at compile-time.
Exiting... (Errors when loading file)

I've tried reloading "Extras restricted" and several other things.

It was working properly some time ago ... I think some update fubared my DVD player.

Is this a known bug with 22.04 ???

---

### Post by VMC on 2023-08-22
Maybe this link will help:
[https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html.en](https://help.ubuntu.com/stable/ubuntu-help/video-dvd-restricted.html.en)

---

### Post by cwmoser on 2023-08-23
Still will not play.  Its a home made DVD I made from a VCR tape.  Not commercial.
It will play properly on a DVD player attached to my Television, but not on the DVD players on two of my Ubuntu 22.04 computers.

I get this output:  "MPlayer/mpv has finished unexpectedly, Exit code: 2"

This is the log from SMPlayer:
/usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color --input-ipc-server=/tmp/smplayer-mpv-3a68a4 --msg-level=ffmpeg/demuxer=error --video-rotate=no --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-vo-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=77594641 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --osd-bar-align-y=0.6 --sub-ass --embeddedfonts --sub-ass-line-spacing=0 --sub-scale=1 --sub-font=Arial --sub-color=#ffffffff --sub-shadow-color=#ff000000 --sub-border-color=#ff000000 --sub-border-size=0.75 --sub-shadow-offset=2.5 --sub-font-size=50 --sub-bold=no --sub-italic=no --sub-margin-y=8 --sub-margin-x=20 --sub-codepage=ISO-8859-1 --sub-pos=100 --volume=55 --cache=auto --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --screenshot-directory=/home/carl/smplayer_screenshots --audio-pitch-correction=yes --volume-max=110 --ytdl --script-opts=ytdl_hook-ytdl_path=yt-dlp --term-playing-msg=MPV_VERSION=${=mpv-version:}
INFO_VIDEO_WIDTH=${=width}
INFO_VIDEO_HEIGHT=${=height}
INFO_VIDEO_ASPECT=${=video-params/aspect}
INFO_VIDEO_FPS=${=container-fps:${=fps}}
INFO_VIDEO_FORMAT=${=video-format}
INFO_VIDEO_CODEC=${=video-codec}
INFO_DEMUX_ROTATION=${=track-list/0/demux-rotation}
INFO_AUDIO_FORMAT=${=audio-codec-name}
INFO_AUDIO_CODEC=${=audio-codec}
INFO_AUDIO_RATE=${=audio-params/samplerate}
INFO_AUDIO_NCH=${=audio-params/channel-count}
INFO_LENGTH=${=duration:${=length}}
INFO_DEMUXER=${=current-demuxer:${=demuxer}}
INFO_SEEKABLE=${=seekable}
INFO_TITLES=${=disc-titles}
INFO_CHAPTERS=${=chapters}
INFO_TRACKS_COUNT=${=track-list/count}
METADATA_TITLE=${metadata/by-key/title:}
METADATA_ARTIST=${metadata/by-key/artist:}
METADATA_ALBUM=${metadata/by-key/album:}
METADATA_GENRE=${metadata/by-key/genre:}
METADATA_DATE=${metadata/by-key/date:}
METADATA_TRACK=${metadata/by-key/track:}
METADATA_COPYRIGHT=${metadata/by-key/copyright:}
INFO_MEDIA_TITLE=${=media-title:}
INFO_STREAM_PATH=${stream-path}
 --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} computer:///hp%20%20%20%20%20%20%20CDDVDW%20SH-216AL.drive

No protocol handler found to open URL computer:///hp%20%20%20%20%20%20%20CDDVDW%20SH-216AL.drive
The protocol is either unsupported, or was disabled at compile-time.
Exiting... (Errors when loading file)

---

### Post by cwmoser on 2023-08-23
Under /dev I do not have a "dvd", but I do have "cdrom -> sr0"

```

$ ls -l /dev | grep -i cdrom
lrwxrwxrwx   1 root root             3 Aug 22 14:00 cdrom -> sr0
crw-rw----+  1 root cdrom      21,   2 Aug 22 14:00 sg2
brw-rw----+  1 root cdrom      11,   0 Aug 22 14:00 sr0

```

---

### Post by crip720 on 2023-08-23
You mention two of your Ubuntu PCs.  Do you have more PCs that the DVD plays on?  If DVDs played before on a PC and now do not, most of the time I suspect the DVD player hardware, instead of software.  The VLC player should play almost any format.  An external USB DVD player should tell if software/hardware problem.

---

### Post by cwmoser on 2023-08-24
This is wierd. 
I use to be able to use my Grub Repair and Clonezilla DVDs and those don't work anymore too.

Is there a way to remove the device DVD and then reinstall???

---

### Post by #&amp;thj^% on 2023-08-24
Wouldn't it be easier to just remove the CD/DVD drive.
```
 ls -l  /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 Aug 24 10:16 /dev/sr0

```
And i too suspect hardware problems.

---

### Post by TheFu on 2023-08-24
> **crip720 said:**
> You mention two of your Ubuntu PCs.  Do you have more PCs that the DVD plays on?  If DVDs played before on a PC and now do not, most of the time I suspect the DVD player hardware, instead of software.  The VLC player should play almost any format.  An external USB DVD player should tell if software/hardware problem.

+1.

All my DVD players died a few years ago. Some barely were used.  My solution was to get a $20 USB DVD player/writer and that has been working since last Xmas. Plus, since it is USB, I only need 1 to connect to the computer where having the DVD player is most useful.

When discussing DVDs, it is always important to talk commercial or which format it was burned using with self-made DVDs.  There are +RW, -RW and +/-RW formats. Also there are single layer and dual layer ... which is the difference between a 4G and an 8G disc.  Each of those things must align for a disk to play on any specific player.  With commercial DVDs, there is also the region code. If the player is locked to a different region than the commercial disc was made for, then it won't work either.

I don't recall when it happened, but most DVD writers can be placed into any of the -RW +RW or +/-RW modes now.  I feel lucky if I get 5 yrs from a disc player - and the actual amount of use doesn't seem to matter.

---

### Post by cwmoser on 2023-08-25
Replaced the DVD Player from yet another PC ... still the same problem.
I really think its not the DVD hardware but instead some odd configuration issue.

---

### Post by cwmoser on 2023-08-26
I found the problem ... replaced the SATA cable and DVD player is working fine on my desktop PC.
Thanks all for the help and insites.

Now, the other computer, my older laptop, I'll have to investigate but getting the desktop PC working was more important.

---

