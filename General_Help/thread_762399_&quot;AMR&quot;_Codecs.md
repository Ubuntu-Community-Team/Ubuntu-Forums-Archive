---
title: "&quot;AMR&quot; Codecs"
date: 2008-04-22
forum: General Help
---

### Post by ErusGuleilmus on 2008-04-22
It appears that my Mobile Phone records sounds in something called an AMR format. Totem is apparently aware of the format (as the screen shot suggests). Where could I get the codec to play these files?

Thanks!

---

### Post by angry_johnnie on 2008-04-22
If you have the [medibuntu]("http://www.medibuntu.org/") repositories, you just have to

```
sudo apt-get install amrnb
```

and that should do it :-)

Edit:  if you don't have the medibuntu repositories, click on the word 'medibuntu' up there.  It's a link, but for some reason it's not displaying as such... these forums are weird lately :-)

---

### Post by au6u5t on 2009-05-23
i still can,t play my 3GP files with samr audio codec with sound, i have install the amr package from medibuntu, amr package from medibuntu just fixed amr nb files issues, is there any way to fix samr issues? thanks

---

### Post by koshari on 2009-06-03
after installing the plugin use mplayer and sound will be there.

---

### Post by andrew.46 on 2009-06-04
Hi au6u5t,

> **au6u5t said:**
> i still can,t play my 3GP files with samr audio codec with sound, i have install the amr package from medibuntu, amr package from medibuntu just fixed amr nb files issues, is there any way to fix samr issues? thanks

I have to admit that I am not entirely clear what [COLOR="Purple"]***s***[/COLOR]amr files are... Can you post one here or a link?

Andrew

---

### Post by mc4man on 2009-06-05
Some players will use w32codecs for amr (nb or wb), vlc, even if dmo loader enabled will not.
Vlc will use ffmpeg to decode, so your ffmpeg must be compiled with amr enabled

> [00000452] avcodec decoder debug: ffmpeg codec (AMR narrow band) started
[00000452] main decoder debug: using decoder module "avcodec"


(some players term amr-nb as samr, see screen (from same file as above quote

---

### Post by au6u5t on 2009-07-18
> **koshari said:**
> after installing the plugin use mplayer and sound will be there.

you right i can hear the sound using mplayer thanks, i also can hear the sound using real player, only vlc not play sound. thanks, but i hope there is a way to make vlc play sound because i use vlc alot

---

### Post by moster on 2009-07-19
It seems that some licensing problems exist. I am not sure.

---

### Post by andrew.46 on 2009-07-19
Hi moster,

> **moster said:**
> It seems that some licensing problems exist. I am not sure.

For the svn MPlayer the licensing issue has been resolved with revision 29426: 

```

------------------------------------------------------------------------
r29426 | diego | 2009-07-19 01:07:26 +1000 (Sun, 19 Jul 2009) | 4 lines

Change libamr support to libopencore-amr support.
libamr support was removed from FFmpeg.
based on a patch by Andrew Wason, rectalogic rectalogic com

```

so the newest MPlayer will now compile against [libopencore-amr]("https://sourceforge.net/projects/opencore-amr/") for amr playback. Until the native encoder decoder is finished for FFmpeg anyway :-).

Andrew

---

### Post by moster on 2009-07-19
@Andrew, thanks for the information :)

---

### Post by Crajy B on 2009-08-27
Found a very easy and quick solution for the .3gp/AMR codec issue.

Install smplayer from the medibuntu repos.

Its a front-end for mplayer that will play amr files.

I have ubuntu-restricted-extras installed, if you don't have this, then you may also want to install libamrwb3 libamrnb3.

Cheers!

---

### Post by ichekryg on 2009-10-12
Worked for me, Thank you.

> **Crajy B said:**
> Found a very easy and quick solution for the .3gp/AMR codec issue.

Install smplayer from the medibuntu repos.

Its a front-end for mplayer that will play amr files.

I have ubuntu-restricted-extras installed, if you don't have this, then you may also want to install libamrwb3 libamrnb3.

Cheers!

---

### Post by andrew.46 on 2009-10-15
Hi Crajy,

> **Crajy B said:**
> Found a very easy and quick solution for the .3gp/AMR codec issue.

Install smplayer from the medibuntu repos.

Its a front-end for mplayer that will play amr files.

Well, strictly speaking SMPlayer is *not* held in the Medibuntu repository but the copy of *MPlayer* from Medibuntu plays amr files :). This will be something of an issue in the upcoming Karmic Koala where Medibuntu will no longer have a copy of MPlayer and the repository MPlayer will not play amr files...

Andrew

---

### Post by 5nak3 on 2009-10-30
As Andrew has stated, I've come across this problem.

Hardy - Jaunty I was able to play my 3gp files and amr files. But now with Karmic I've come across a problem and can play the video of 3gp files but with no sound. And amr files just wont play at all.

I've tried everything suggested in this thread, but to no avail. Does anyone have any information as to how to play amr or 3gp files in Karmic?

---

### Post by andrew.46 on 2009-10-30
Hi Snak3,

> **5nak3 said:**
> Does anyone have any information as to how to play amr or 3gp files in Karmic?

I have written a guide for compiling the svn MPlayer under Karmic Koala that is awaiting moderation before going into the Tutorials & Tips section. This enables amr sound. Just a matter of waiting until it is approved....

Andrew

---

### Post by 5nak3 on 2009-10-30
Hi Andrew,

Thanks for that, I'll keep an eye out for that. It isn't very important at the moment, but I just like being sure that if I want to watch one of my mobile videos I can without any problems.

May I ask why you chose SMplayer as opposed to Mplayer though? As far as I understand SMplayer is a simple front end for the latter, but as a package it is 3 or so times larger than Mplayer alone.

---

### Post by andrew.46 on 2009-10-30
Hi Snak3,

> **5nak3 said:**
> May I ask why you chose SMplayer as opposed to Mplayer though? As far as I understand SMplayer is a simple front end for the latter, but as a package it is 3 or so times larger than Mplayer alone.

The graphical element of MPlayer, called GMPlayer, has been effectively abandoned by the MPlayer developers and it generates many, many error messages. There has been endless debate on the MPlayer mailing lists about abandoning it completely and also a notice on [the MPlayer website]("http://www.mplayerhq.hu/design7/dload.html"):

> 
You might also want to check out the other frontends  since there is no further development and limited bug fixing for the included graphical user interface. 


I tend to use the commandline only myself but I realise that many will want a gui so a short investigation convinced me that SMPlayer was the best available. A further helpful thing with SMPlayer is that the developer is active on these forums and will answer any problems :).

Andrew

---

### Post by 5nak3 on 2009-10-31
Hi Andrew

Thanks for the clarification, I'll be sure to keep a look out for the tutorial.

Cheers

---

### Post by andrew.46 on 2009-11-01
Hi 5nak3,

> **5nak3 said:**
>  I'll be sure to keep a look out for the tutorial.

The guide has surfaced:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

I have attached a screenshot to the guide demonstrating amr playback from the commandline.

Andrew

---

### Post by chichilalescu on 2009-11-16
found something that actually works for amr files...
I'm not interested in playing them, I wanna convert them to mp3 and then I play the mp3s.

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

Note that I run ubunut 9.10 64bit, so there should be no problem with forcing the architecture.

---

### Post by andrew.46 on 2009-11-16
Hi chichilaleasu,

> **chichilalescu said:**
> found something that actually works for amr files...
I'm not interested in playing them, I wanna convert them to mp3 and then I play the mp3s.

Most amr sound is pretty low quality, do the mp3s produced by transcoding with this application sound any good?

Andrew

---

### Post by ario on 2010-03-29
Hey! What are you talking about guys?
Are you telling me that ubuntu never can play amr files normally and users must compile a bunch of source codes just by themselves?
If canonical don't want to do it our way then why don't we chose another distro?!?

---

### Post by ario on 2010-03-29
Ok! Compiled and installed ffmpeg by first running:
```
sudo su
apt-get install subversion
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure
make
make install

```
So all commands ran without any error just a bunch of warnings. Now what? I still can't play the thing! :(

started mplayer and it prompts:
```

libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [s263]  176x144  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh263] vfm: ffmpeg (FFmpeg H.263+)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
**Cannot find codec 'libamr_nb' in libavcodec...**
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 176 x 144 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 176x144 => 192x144 Planar YV12 
[swscaler @ 0xb5750240]using unscaled yuv420p -> rgb32 special converter

```
Notice the highlighted error message above. I searched svn downloaded source code in my "~/ffmpeg" folder. there was no libamr_nb in "ffmpeg/libavcodec/" folder. FFMpeg project removed amr and not supporting it anymore? Installing windows and start dual booting just for playing a 3gp file like an insane?
I may prefer to use VirtualBox to start windows and play the thing but... Oh my God!
Any suggestion?

---

### Post by ario on 2010-03-29
Tried downloading and compiling the whole MPlayer source code. All done and take about 15 minute to compelete. But still don't!
[B]Finally downloaded realplayer linux .deb package from this address:
[http://www.real.com/realplayer/linux](http://www.real.com/realplayer/linux)
and installed it.[/B] RealPlayer downloaded 18 more packages itself to install. And after all it played my 3gp file with amr audio in it. Loud and Clear.
Wow!

---

### Post by andrew.46 on 2010-03-29
Hi ario,

> **ario said:**
> Tried downloading and compiling the whole MPlayer source code. All done and take about 15 minute to compelete. But still don't!

You might be best to download the newest svn MPlayer code and then compile against *libopencore-amrwb-dev* and *libopencore-amrnb-dev*. Both of these are available in the Karmic repositories. But perhaps you are happy with the realplayer?

Andrew

---

### Post by ario on 2010-03-31
> **andrew.46 said:**
> Hi ario,



You might be best to download the newest svn MPlayer code and then compile against *libopencore-amrwb-dev* and *libopencore-amrnb-dev*. Both of these are available in the Karmic repositories. But perhaps you are happy with the realplayer?

Andrew

Thanks Androw. I'm not happy with commercial softwares like RealPlayer. But how can I compile something against something else? Because I've downloaded and compiled the latest version of MPlayer when I had libopencore-amrwb and libopencore-amrnb installed by synaptic via ubuntu official repositories. But no success. Now should I install *libopencore-amrwb-dev* and *libopencore-amrnb-dev* via synaptic and just make and install MPlayer again or what?
Thanks for your attention good guy;)

---

### Post by andrew.46 on 2010-03-31
Hi ario,

Perhaps you could try the last of a long series of guides I have written for MPlayer:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

This enables amr playback:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -ac help | grep amr[/COLOR]**
libopencoreamrnb ffmpeg    working   AMR Narrowband  [libopencore_amrnb]
libopencoreamrwb ffmpeg    working   AMR Wideband  [libopencore_amrwb]

```

All the best,

Andrew

---

