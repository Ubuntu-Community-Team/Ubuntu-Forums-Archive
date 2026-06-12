---
title: "How to convert .mkv to .mp4 with sound?"
date: 2019-09-15
forum: General Help
---

### Post by satimis on 2019-09-15
Hi all.

Ubuntu 16.04

I have tried running ffmpeg and avconv to convert a .mkv to .mp4.  Both worked but the .mp4 file is without sound.

Please help to solve the problem.  Thanks

Regards
satimis

---

### Post by TheFu on 2019-09-15
Perhaps if you posted the attempted commands, someone would see something wrong?

Also, the output from **mkvinfo** would help.  MKVs can hold many more types of video and audio than mp4 allows.

---

### Post by Jim_Lynch on 2019-09-15
> **satimis said:**
> Hi all.

Ubuntu 16.04

I have tried running ffmpeg and avconv to convert a .mkv to .mp4.  Both worked but the .mp4 file is without sound.

Please help to solve the problem.  Thanks

Regards
satimis
I have used the following command to successfully convert an .mkv file to .mp4 and insert an audio track at the same time.
```
ffmpeg -i output.mkv -i ~/Music/background/test.mp3 -c copy -map 0:v:0 -map 1:a:0 Test.mp4

```

YMMV.
All .mkv files are not the same.  The output.mkv file was generated from  photofilmstrip.

Jim

---

### Post by (kyT%0) on 2019-09-15
this has always worked for me :

```
ffmpeg -i .mkv -codec copy .mp4

```

add the respective file names before .mkv & .mp4

leave no spaces in the file name.

---

### Post by satimis on 2019-09-15
> **u-n said:**
> this has always worked for me :

```
ffmpeg -i .mkv -codec copy .mp4

```

add the respective file names before .mkv & .mp4

leave no spaces in the file name.
Hi,

Tried your advice.  It created a .mp4 file without complaint.  Activate it with "Video" following warning popup```

Required plugin could not be found

Videos requires to install plugins to play media files of the following type: MPEG-4 AAC decoder

```

Still without sound.

&#10219; apt policy ubuntu-restricted-extras```

ubuntu-restricted-extras:
  Installed: 65
  Candidate: 65
  Version table:
 *** 65 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
        100 /var/lib/dpkg/status

```
ubuntu-restricted-extras already installed.

---

### Post by satimis on 2019-09-15
> **Jim_Lynch said:**
> I have used the following command to successfully convert an .mkv file to .mp4 and insert an audio track at the same time.
```
ffmpeg -i output.mkv -i ~/Music/background/test.mp3 -c copy -map 0:v:0 -map 1:a:0 Test.mp4

```

YMMV.
All .mkv files are not the same.  The output.mkv file was generated from  photofilmstrip.

Jim
Hi Jim,

Thanks for your advice.  The .mkv file was captured with "SimpleScreenRecorder" on an online live-broadcasting.

satimis

---

### Post by (kyT%0) on 2019-09-15
i would advice you to try another player, preferably mpv or vlc. to install :

```
sudo apt install mpv
```

```
sudo apt install vlc
```

---

### Post by satimis on 2019-09-15
> **TheFu said:**
> Perhaps if you posted the attempted commands, someone would see something wrong?

Also, the output from **mkvinfo** would help.  MKVs can hold many more types of video and audio than mp4 allows.
Sorry I couldn't recall.  I found those commands on Internet and they convert .mkv file to .mp4 file without complaint but no sound.

Whether following package provides "mkvinfo"
MKVToolNix – Matroska tools for Linux/Unix and Windows
[https://mkvtoolnix.download/downloads.html](https://mkvtoolnix.download/downloads.html)

Thanks

Regards
satimis

---

### Post by satimis on 2019-09-15
> **u-n said:**
> i would advice you to try another player, preferably mpv or vlc. to install :

```
sudo apt install mpv
```

```
sudo apt install vlc
```
Hi,

Thanks for your advice.

Before I have tried vlc on the converted .mp4 file.  No video and no sound.

Regards
satimis

---

### Post by ajgreeny on 2019-09-15
> **satimis said:**
> Sorry I couldn't recall.  I found those commands on Internet and they convert .mkv file to .mp4 file without complaint but no sound.

Whether following package provides "mkvinfo"
MKVToolNix – Matroska tools for Linux/Unix and Windows
[https://mkvtoolnix.download/downloads.html](https://mkvtoolnix.download/downloads.html)

Thanks

Regards
satimis
Just open a terminal and use command ```
history | grep ffmpeg
```
There are other ways, including a reverse search with Ctrl+R mpeg, but using grep is, I think, the easiest way to see all the commands used that included ffmpeg. immediately.

---

### Post by westie457 on 2019-09-15
I usually use a GUI app called Handbrake capable of DVD's and Bluray disks to MKV or MP4 files. It can also convert MKV files to MP4.
In the GUI the default settings just work quite well.

Here is a link to the man page. [https://handbrake.fr/docs/en/latest/cli/command-line-reference.html](https://handbrake.fr/docs/en/latest/cli/command-line-reference.html)

---

### Post by satimis on 2019-09-16
Hi all,

I solved my problem.

I ran SimpleScreenRecorder recording an online video.  

Previously under;
Audio input
Source: [Built-in Aud...nalog Stereo] (selected)
(please refers to photo-1)
No sound was recorded on .mkv file

I must select
Source: [Monitor of ...alog Stereo]
(please refers to Photo-2)

Problem now solved.

Thanks for all advice.

Regards
satimis

---

