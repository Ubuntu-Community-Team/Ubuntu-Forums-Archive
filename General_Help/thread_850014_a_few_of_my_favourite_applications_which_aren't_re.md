---
title: "a few of my favourite applications which aren't really talked about. just for fun"
date: 2008-07-05
forum: General Help
---

### Post by pluckypigeon on 2008-07-05
I thought I'd make a little list and hopefully someone will add. I haven't really heard these added as anyones favourite apps so here goes

finch - a command line IM app - similar to pidgin

lynx - a command line web browser - I enjoy surfing the web on lynx, it's a different experience

top - a command line sysmonitor

httrack - a command line website downloader - it downloads a whole website

I do use GUI programs by the way. I just happen to enjoy using these command line ones also. 

Try them out

---

### Post by Mongo5000 on 2008-07-05
I have to admit as well, I like centericq.  Its a terminal based IM client similar to finch.

Sometimes its fun to do things in the terminal even though you can do them in the GUI... we're such nerds

---

### Post by pluckypigeon on 2008-07-05
thanks for your reply,

I have never used ICQ stuff. I'm going to have to check that out.

Has anyone used rtorrent? 

If I could play music from the command line I'd be really excited although surfing the web and chatting on the command line is really exciting in its self:)

---

### Post by Cogman on 2008-07-05
> **pluckypigeon said:**
> thanks for your reply,

I have never used ICQ stuff. I'm going to have to check that out.

Has anyone used rtorrent? 

If I could play music from the command line I'd be really excited although surfing the web and chatting on the command line is really exciting in its self:)

You can listen to music from the command line :) Install mplayer, then run mplayer -nogui song.ogg

---

### Post by Gunman1982 on 2008-07-05
Out of curiosity what are the benefits using httrack instead of wget?

---

### Post by pluckypigeon on 2008-07-05
> **Gunman1982 said:**
> Out of curiosity what are the benefits using httrack instead of wget?

I wouldn't say httrack is more beneficial than wget.

I use wget to download and httrack for website downloading. 

I know you can use wget for website downloading but httrack is more website specific and geared more to downloading websites

---

### Post by manfer on 2008-07-05
Just install sox and play. ;)

prompt:~$ **play musicfile**

(e.g. *play ~/Music/prueba.mp3*)

---

### Post by pluckypigeon on 2008-07-05
> **Cogman said:**
> You can listen to music from the command line :) Install mplayer, then run mplayer -nogui song.ogg

I heard about this but I didn't believe it. I'll have to check this out:)

---

### Post by pluckypigeon on 2008-07-05
> **manfer said:**
> Just install sox and play. ;)

prompt:~$ **play musicfile**

(e.g. *play ~/Music/prueba.mp3*)

I'll have to check this out also:)

---

### Post by cariboo on 2008-07-05
Have a look at the manual for httrack. In a terminal type:

```
man httrack
```

That will probably give you more information than you really want.:)

BTW: you have to install httrack first.

Jim

---

### Post by manfer on 2008-07-05
> **pluckypigeon said:**
> I'll have to check this out also:)

The package to install is sox.

Package: sox
Priority: optional
Section: universe/sound
Installed-Size: 176
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Pascal Giard <pascal@debian.org>
Architecture: i386
Version: 14.0.0-5
Depends: libc6 (>= 2.6.1-1), libltdl3 (>= 1.5.2-2), libsamplerate0, libsox0
Recommends: libsox-fmt-base, libsox-fmt-alsa | libsox-fmt-ao | libsox-fmt-oss
Suggests: libsox-fmt-all
Filename: pool/universe/s/sox/sox_14.0.0-5_i386.deb
Size: 60610
MD5sum: c03c6a0ec6de89c17e7aab877ecbbdaf
SHA1: d955d5904f120b3825b58f7ed3cddb1ce7ac63f1
SHA256: c664249c935b20710c6042062989432c2f0bc5ea6597c7c4c1e62f181edc68dd
Description: Swiss army knife of sound processing
 SoX is a command line utility that can convert various formats of computer
 audio files in to other formats. It can also apply various effects to these
 sound files during the conversion. As an added bonus, SoX can play and record
 audio files on several unix-style platforms.
 .
 SoX is able to handle formats like Ogg Vorbis, MP3, WAV, AIFF, VOC, SND, AU,
 GSM and several more.
 Any format support requires at least libsox-fmt-base. Some formats have their
 own package e.g. Ogg Vorbis is provided by libsox-fmt-ogg.
 .
 SoX supports most common sound architectures i.e. Alsa, Libao and OSS
 (provided by libsox-fmt-alsa, libsox-fmt-ao and libsox-fmt-oss). It also
 supports LADSPA plugins.
 .
 Homepage: [http://sox.sourceforge.net](http://sox.sourceforge.net)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

prompt:~$ **sudo apt-get install sox**

After install you would have three new commands at your disposal: sox, play, rec.

---

### Post by pluckypigeon on 2008-07-05
I tried mplayer -nogui and sox but couldn't get either of them to work.:confused:

I'll have to delve in deeper at some other point.:)

mplayer -nogui gave me a manual which I haven't read yet but I will and sox told me it can't open input file

This thread has steered toward command-line programs now which wasn't my idea at first, but now it has I wish I could change the topic to command line now. O well.

:)

---

### Post by manfer on 2008-07-05
> **pluckypigeon said:**
> I tried mplayer -nogui and sox but couldn't get either of them to work.:confused:

I'll have to delve in deeper at some other point.:)

mplayer -nogui gave me a manual which I haven't read yet but I will and sox told me it can't open input file

This thread has steered toward command-line programs now which wasn't my idea at first, but now it has I wish I could change the topic to command line now. O well.

:)

Maybe you need some of the libs for the type of file you are trying to play. Look for those libsox-fmt-xxxx libs.

---

### Post by pluckypigeon on 2008-07-05
Sorry, I didn't mean to turn this in to a help thread but thanks, it worked though.

What command line apps do other people use? I've become engrossed now!!:)

---

### Post by hyper_ch on 2008-07-05
> **pluckypigeon said:**
> lynx - a command line web browser - I enjoy surfing the web on lynx, it's a different experience
Check out Links2

> **pluckypigeon said:**
> top - a command line sysmonitor
check out htop

> **pluckypigeon said:**
> httrack - a command line website downloader - it downloads a whole website
that's how I got my 25k wallpapers ;)


and rtorrent with screen just rules as torrent client....

---

