---
title: "Where/how to get up-to-date ffmpeg onto ubuntu 16.04 desktop ?"
date: 2016-06-08
forum: General Help
---

### Post by Ronald_F._Guilmett on 2016-06-08
Please excuse my ignorance which, I confess up front, is abundant.

I have Ubuntu 16.04, and I've already installed a binary for ffmpeg 2.8.6-1ubuntu2.  (Please don't ask me exactly *how* I got this installed, or which repositories I used.  I frankly don't remember anymore.)

Anyway, ffmpeg is crashing on me due to some bug that I already googled for and that, apparently, has been fixed in later versions for ffmpeg.  So I need to get a fresher ffmpeg installed on this 16.04 desktop system.

The problem is that I've already googled around for awhile and I'll be damned if what I found make any sense to me.  I'm sure that a big part of the problem is that although I have plenty of UNIX experience, I'm still not really very down with the **apt **tool and/or with proper procedures and protocols for package installation on Ubuntu generally.

Anyway, here is where I started:

[https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)

Ok, so on that page I clicked on the Tux (penguin) icon (duh!) and then I clicked on the link that says "_Ubuntu - official packages for Vivid, Wily, Xenial_".  (16.04 == Xenial, so this link would seem to take me closer towards what I want.)

So anyway, clicking on that link takes me here:

[https://launchpad.net/ubuntu/+source/ffmpeg/7:3.0.2-1ubuntu1](https://launchpad.net/ubuntu/+source/ffmpeg/7:3.0.2-1ubuntu1)

Now life gets complicated.  I see these lines, which do not inspire ***any*** confidence whatsoever that I am even in the right place to start to get what I want:

ffmpeg (7:3.0.2-1ubuntu1) yakkety; urgency=medium
...
ffmpeg (7:3.0.2-1) unstable; urgency=medium

yakkety != xenial,
so where is the stuff for 16.04 that I came here seeking?  Is the stuff for yakkety (16.10) at all likely to work on 16.04 (xenial)?

I am also not at all filled with confidence by seeing "unstable; urgency=medium".
Can someone (anyone) please explain to me what THAT is all about?

So anyway, scrolling down on the above page, I come to the heading "Binary packages built by this source".  (I didn't know that source code was able to build anything, all on its own, but we'll pass that for now.)

So then there is a blue link for "ffmpeg".  Following that gets me here:

[https://launchpad.net/ubuntu/yakkety/+package/ffmpeg](https://launchpad.net/ubuntu/yakkety/+package/ffmpeg)

Now I have about a zillion choices, but only two are self-evidently of interest to me, i.e.:

ffmpeg 7:3.0.2-1ubuntu1 in amd64 (Proposed)
ffmpeg 7:3.0.2-1ubuntu1 in amd64 (Release)

Problem is:  I have no idea which one is the "right" one for me.  Is "Proposed" better than "Release", or vise versa?  Nothing on this page gives me even the vaguest hint of what those terms might mean in this specific context.

To be on the safe side, I decide to click on the link for "Release"... just because that sounds better to me than "Proposed".  So that then takes me to this new page:

[https://launchpad.net/ubuntu/yakkety/amd64/ffmpeg/7:3.0.2-1ubuntu1](https://launchpad.net/ubuntu/yakkety/amd64/ffmpeg/7:3.0.2-1ubuntu1)

On this page, I again see a link to the sources, but I'm looking (hopefully) for a pre-built binary.  Under the heading "Downloadable files" I see two links... one to yet another web page whose title is "amd64 build of ffmpeg 7:3.0.2-1ubuntu1 in ubuntu yakkety PROPOSED", and another link titled "ffmpeg_3.0.2-1ubuntu1_amd64.deb".  I click on the first one, and then on the first link on that page that sounds like it goes towrads the binary I am seeking, and I found that no, I am now just going around in circles.  (Sigh.)

So then, instead, I click on the other link and download the .deb file.  OK.  Swell.  Now what?  I confess that I'm not even 100% sure how to get this properly installed.  Do I need to first uninstall the ffmpeg 2.8.6 that's already installed, or will whatever tool performs the install of this .deb file do that for me?  Will all of the requsite libraries be automagically installed when I install this .deb file, or am I gonna need to get all those installed manually myself beforehand?

Well, I suppose that I might be able to just plow my way past all of these issues, but again, when I'm done, will I even end up with something that's going to run properly on 16.04 (xenial)?  Will it be "unstable" and prone to crashing all the time?  If so, then this exercise isn't really gonna help me, and I will have wasted quite a lot of time for nothing.

---

### Post by Ronald_F._Guilmett on 2016-06-08
This just isn't going well at all.

So I used the Ubuntu GUI file browser, found the .deb file I previously described, and clicked on it.  This brought up the stock Ubuntu software installer..  I clicked "install" and basically, nothing happened.  (Why the stock Ubuntu software installer is the default tool associated with the .deb file extension if it isn't even really capable of installing those is beyond me.)

Anyway, seeing that the Ubuntu installer did absolutely nothing when asked to install the .deb file reminded me that there's some special trick you have to use if you want to ACTUALLY install a .deb file.  I googled, and was thus reminded about the gdebi thing.  Fortunately, I had already installed that... probably when I was trying to install ffmpeg 2.8.6.  So I right clicked on the .deb file, and opened it with gdebi, then clicked "install".

Bottom line:  Failure ensued.

I got a message in the gdebi window saying:

Error: Dependency is not satisfiable: libavcodec57 (>=7:3.0)|libavcodec-extra57 (>=7:3.0)

It might have been helpful if SOMETHING has at least given a hint as to WHY this dependency was "not satisfiable".  I mean seriously, what exactly is the beef here chief?  I can't exactly fix it if I don't even know what's wrong.  A little more verbosity here wouldn't hurt.

Can anyone tell me how to fix this?

---

### Post by CantankRus on 2016-06-09
You can't just download a deb file from a different release and expect all dependencies to be satisfied.

Use this ppa which contains the depedencies as well.
Firstly install ppa-purge to  revert to default packages if you get problems.
```
sudo apt install ppa-purge
```

Add this [**_[COLOR="#B22222"]PPA[/COLOR]_**]("https://launchpad.net/~nicola-onorata/+archive/ubuntu/desktop") and update sources.
```
sudo add-apt-repository ppa:nicola-onorata/desktop
sudo apt update
```

This ppa contains numerous other packages that you may not want to update or could cause problems.
So just update ffmpeg and it's dependencies...
```
sudo apt install ffmpeg
```
This should show simalar to this...
> The following NEW packages will be installed:
  libavcodec57 libavdevice57 libavfilter6 libavformat57 libavresample3 libavutil55 libpostproc54 libswresample2
  libswscale4
The following packages will be upgraded:
  ffmpeg
  
When finished installing disable the nicola-onorata/desktop ppa (the **-r** flag removes ppa) and update sources again.
```
sudo add-apt-repository **-r** ppa:nicola-onorata/desktop
sudo apt update
```

If you need to purge the ppa and revert to default packages you will need to re-enable the ppa, update sources and run ppa-purge.
```
sudo add-apt-repository ppa:nicola-onorata/desktop
sudo apt update
sudo ppa-purge ppa:nicola-onorata/desktop
```

---

### Post by Ronald_F._Guilmett on 2016-06-11
Thank you very much for your detailed and precise explanation.  I shall certainly be attempting to follow your instructions to the letter as soon as I have finished migrating my system to the SSD I just bought.

I do want to say however.... and this is certainly not meant as a knock on _you_ in any way, so please don't take it that way... that upon reading your instructions for accomplishing this seeming small task, I was reminded of the teacher giving his young pupils instructions in Monty Python's "The Meaning of Life"...

     Now before I begin the lesson will those of you
     who are playing in the match this afternoon move your clothes
     down on to the lower peg immediately after lunch before you
     write your letter home, if you're not getting your hair cut,
     unless you've got a younger brother who is going out this
     weekend as the guest of another boy, in which case collect his
     note before lunch, put it in your letter after you've had your
     hair cut, and make sure he moves your clothes down onto the
     lower peg for you. Now...

P.S. Funny thing... As it turns out, the bug in the older ffmpeg that caused me to want to update it actually _isn't_ even fixed in
the 3.0.2 version.  (I managed to find a statically linked ffmpeg 3.0.2 and ran a test using that one.)  I still do want to
update my ffmpeg anyway (so your detailed instructions were not wasted in any sense).

P.P.S. FYI - Nobody should bother trying to use *any* recent incarnations of ffmpeg to copy an mpeg1 video + mpeg1 audio from a .mp4
container into a .mkv container.  Newer ffmpegs don't like to do that.  Like not at all.  They refuse to do the copying and give some
useless error about how MKV requires timestamps (which are allegedly missing from the input streams... at least for 11
out of the 12 such input files I tested).

Avidemux also failed to do these same copies, but was at least able to copy the mpeg1 video & audio streams into a
properly indexed .avi output container, which was adequate for my purposes.  (But Avidemux fails on several other
tasks that ffmpeg has no problem with.)

---

### Post by kevdog on 2016-06-11
My only recommendation is that you probably want to compile ffmpeg from source from the git repository if you want the latest and greatest.  I believe a user name Andrew76 who I don't see around here much anymore had a guide on the forums here how to do that.  PPA's are another option, but then you are always relying on the ppa maintainer to update the release.

---

### Post by FakeOutdoorsman on 2016-06-11
> **Ronald_F._Guilmett said:**
> P.P.S. FYI - Nobody should bother trying to use *any* recent incarnations of ffmpeg to copy an mpeg1 video + mpeg1 audio from a .mp4
container into a .mkv container.  Newer ffmpegs don't like to do that.  Like not at all.  They refuse to do the copying and give some
useless error about how MKV requires timestamps (which are allegedly missing from the input streams... at least for 11
out of the 12 such input files I tested).

Please provide a short input sample file, your command, and the resulting console output so I can attempt to duplicate this issue.

[quote=kevdog]My only recommendation is that you probably want to compile ffmpeg from source from the git repository if you want the latest and greatest.[/quote]
Simply downloading a static binary is probably the easiest method:
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)

---

### Post by yoshii on 2016-06-11
Ronald, I empathise with you very much on this issue.  
It can be very daunting sometimes.  

This webpage can be of some assistance when missing dependencies are listed:  [https://pkgs.org/](https://pkgs.org/)
It's a search page for linux packages.  You can select your linux version from the drop-down menu before you enter in search terms.  

Then, in the results, included with the download link, are the dependencies for the dependencies!!!!?!
I know that can get nuts too, but if you are careful and patient enough, you can get everything you need unless there are just too many of them.  

I recently was able to install 32-bit OcenAudio for 32-bit Ubuntu Studio v16.04.x LTS.  But it required about 20 different files none of which were documented on the OcenAudio website or download page.  I used [https://pkgs.org/](https://pkgs.org/) to accomplish it.  

I find that gDebi and Synaptic Package manager and "sudo dpkg -i *.deb" are really handy.  I removed Gnome-Software since it doesn't work yet.  And I gave up on Ubuntu Software Center since it's discontinued.

---

### Post by Ronald_F._Guilmett on 2016-06-11
> **FakeOutdoorsman said:**
> Please provide a short input sample file, your command, and the resulting console output so I can attempt to duplicate this issue.

Sorry.  It am not allowed to do so.  (In fact I have been warned not to do so by a forum admin.)

> 
Simply downloading a static binary is probably the easiest method:
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)

Yes!  As I mentioned, I did indeed end up running some tests with a static binary of 3.0.2, and indeed, I got that static binary from Mr. Van Sickle's web site.

> **yoshi2 said:**
> Ronald, I empathise with you very much on this issue.  
It can be very daunting sometimes.

Thank you.  I do appreciate that.

As I described, there were _numerous_ annoyances along the way when I tried to get the Right Thing installed... and there does not seem to be any good reason for several of them.
 
I was particularly unhappy after following the link that said " "_Ubuntu - official packages for Vivid, Wily, Xenial_", only to end up in a place where I _could_ get an ffmpeg suitable for 16.10 (Yakkety) but *not* for 16.04 (Xenial), which is what I went there for.  (False advertising?)

Also, the loop of circular links that I ended up getting trapped in (see first post in this thread) was also not particularly pleasant.  And I was rather disappointed to find that the specific (Cannonical?) developer who has apparently been putting up these various ffmpeg binaries appears to have decided to remain exceptionally coy about his e-mail address, so I could never just ask him directly, via e-mail "Hey!  What am I missing?"  (I guess that this fellow must be EXCEPTIONALLY popular... so much so that he worries about being hounded by the press for interviews... requests which would clog up his inbox if he actually made his e-mail address public.  Yes, life is hard when you are a media superstar, I guess.)

My preceeding reference to that famous Monty Python skit was intended to encapsulate the obvious question I have about all this, i.e.:  Does something as simple as just installing the latest release of one particular popular application (ffmpeg) onto the latest and most up-to-date Ubuntu LTS (16.04) REALLY need to be quite this complicated?  (I've come to expect this kind of unvarnished complexity from e.g. Arch Linux, but not from Ubuntu.)

---

### Post by mc4man on 2016-06-12
Can't recollect seeing mpeg1 audio/video in mp4 container, seems wrong. If one tried to copy with ffmpeg a .mpeg or .mpg into .mkv then they likely see something like this - 

[matroska @ 0x2662ea0] Can't write packet with unknown timestamp
av_interleaved_write_frame(): Invalid argument
Don't think this is unexpected or new.

You  could in the above case copy with ffmpeg to .mp4 or .avi, then copy to .mkv

---

### Post by Ronald_F._Guilmett on 2016-06-12
> **mc4man said:**
> Can't recollect seeing mpeg1 audio/video in mp4 container, seems wrong.

Sorry.  Yes.  I misspoke.  The files in question are MPEG-PS containers.

> 
 If one tried to copy with ffmpeg a .mpeg or .mpg into .mkv then they likely see something like this - 

[matroska @ 0x2662ea0] Can't write packet with unknown timestamp
av_interleaved_write_frame(): Invalid argument


Yes!  That's what I got... along with some insulting, absurd, and meaningless error messages telling me to "fix your code".  Huh??  What code?

*My* code is all fine.  It works, has been tested, and doesn't die for unexplained reasons while spitting out cryptic error messages.

> 
Don't think this is unexpected or new.

Wait... *what??*

It sure as hell was *unexpected to me!  *I can't comment precisely on how "new" it might be.  (Some other guy posted about this same problem elsewhere, and said that he didn't have the problem when he switched back to some significantly older version of ffmpeg.)

> 
You  could in the above case copy with ffmpeg to .mp4 or .avi, then copy to .mkv

Nope.  I can do the copy from the .mpg to the .avi, but then if I try to do the copy from the .avi to the .mkv again I get the:

Can't write packet with unknown timestamp
av_interleaved_write_frame(): Invalid argument


To be clear, I'm not doing anything strange or fancy here, just like....

ffmpeg -i foo.mpg -acodec copy -vcodec copy foo.avi
ffmpeg -i foo.avi -acodec copy -vcodec copy foo.mkv

---

### Post by mc4man on 2016-06-12
Well till something better comes along maybe try  mp4 > mkv,  seems to work here ok. Before was trying a mpeg from hubble telescope so it didn't have audio. That went ok as far as  avi > mkv. Just tried this sample with both a/v & the avi to mkv failed as you've seen.
```
wget http://samples.mplayerhq.hu/MPEG1/zelda%20first%20commercial.mpeg
```
ex. here,.mpeg to .mp4 to .mkv

```
~$ ffmpeg2 -i '/home/doug/zelda first commercial.mpeg' -c copy 1.mp4
ffmpeg version N-80283-g84efdab Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-14ubuntu2.1) 20160413
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 24.100 / 55. 24.100
  libavcodec     57. 46.100 / 57. 46.100
  libavformat    57. 37.101 / 57. 37.101
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 46.101 /  6. 46.101
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
Input #0, mpeg, from '/home/doug/zelda first commercial.mpeg':
  Duration: 00:00:29.80, start: 0.070267, bitrate: 690 kb/s
    Stream #0:0[0x1e0]: Video: mpeg1video, yuv420p(tv), 160x120 [SAR 1:1 DAR 4:3], 614 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 29.97 tbc
    Stream #0:1[0x1c0]: Audio: mp2, 44100 Hz, mono, s16p, 64 kb/s
[mp4 @ 0x3b10ae0] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.
    Last message repeated 1 times
Output #0, mp4, to '1.mp4':
  Metadata:
    encoder         : Lavf57.37.101
    Stream #0:0: Video: mpeg1video (j[0][0][0] / 0x006A), yuv420p(tv), 160x120 [SAR 1:1 DAR 4:3], q=2-31, 614 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 90k tbc
    Stream #0:1: Audio: mp2 (i[0][0][0] / 0x0069), 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
[mp4 @ 0x3b10ae0] Timestamps are unset in a packet for stream 0. This is deprecated and will stop working in the future. Fix your code to set the timestamps properly
[mp4 @ 0x3b10ae0] pts has no value
    Last message repeated 144 times
[mp4 @ 0x3b10ae0] pts has no value
frame=  894 fps=0.0 q=-1.0 Lsize=    2498kB time=00:00:29.77 bitrate= 687.3kbits/s speed=2.26e+03x    
video:2241kB audio:233kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.021057%

doug@doug-Lenovo-IdeaPad-Y510P:~$ ffmpeg2 -i 1.mp4 -c copy 1.mkv
ffmpeg version N-80283-g84efdab Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.3.1 (Ubuntu 5.3.1-14ubuntu2.1) 20160413
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
  libavutil      55. 24.100 / 55. 24.100
  libavcodec     57. 46.100 / 57. 46.100
  libavformat    57. 37.101 / 57. 37.101
  libavdevice    57.  0.101 / 57.  0.101
  libavfilter     6. 46.101 /  6. 46.101
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  1.100 /  4.  1.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2mp41
    encoder         : Lavf57.37.101
  Duration: 00:00:29.83, start: 0.000000, bitrate: 686 kb/s
    Stream #0:0(und): Video: mpeg1video (mp4v / 0x7634706D), yuv420p(tv), 160x120 [SAR 1:1 DAR 4:3], 614 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 29.97 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: mp3 (mp4a / 0x6134706D), 44100 Hz, mono, s16p, 63 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
[matroska @ 0x2771f00] Using AVStream.codec to pass codec parameters to muxers is deprecated, use AVStream.codecpar instead.
    Last message repeated 1 times
Output #0, matroska, to '1.mkv':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2mp41
    encoder         : Lavf57.37.101
    Stream #0:0(und): Video: mpeg1video (mpg1 / 0x3167706D), yuv420p(tv), 160x120 [SAR 1:1 DAR 4:3], q=2-31, 614 kb/s, 29.97 fps, 29.97 tbr, 1k tbn, 90k tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, mono, 63 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=  894 fps=0.0 q=-1.0 Lsize=    2490kB time=00:00:29.78 bitrate= 685.1kbits/s speed=1.54e+03x    
video:2241kB audio:233kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.692379%


```

As far as 'not new', I've seen mailing list stuff about this error with mpeg-ts going back a couple of years or so.

---

### Post by Ronald_F._Guilmett on 2016-06-13
> **mc4man said:**
> 
As far as 'not new', I've seen mailing list stuff about this error with mpeg-ts going back a couple of years or so.

As I mentioned, the specific files that I personally am working with are actually MPEG-PS, not MPEG-TS.  (But that's a small detail.)

Anyway, I do agree that the evidence suggests that this specific ffmpeg bug is not particularly new.  It's still a bug however.  Too bad none of the ffmpeg folks think its worth fixing.  (Several other programs, e.g. handbrake, kodi, vlc, smplayer, have no problems at all coping with the relevant input files.  It's only ffmpeg that is balking when asked to copy the contained streams to a .mkv file.  I have trouble understanding why ffmpeg can't either find or manufacture timestamps, as necessary, in order to make the MKV container format happy.  Obviously, somewhere within the input files there must be *some *kinds of clues about when things are supposed to appear.  Otherwise, how would all of the players I mentioned... and also handbrake... know how to play these same files properly... which they do.)

---

### Post by kazakore on 2016-06-13
Have you heard of FFmbc? A long time fork of FFmpeg with many fixes mainly aimed at broadcast situations and used by some of the biggest broadcasters around the world. It may well have the fixes you require. 

[https://github.com/bcoudurier/FFmbc](https://github.com/bcoudurier/FFmbc)

I've not used in a few years and seems the old Google Code site is empty so can only assume that above is the correct migration. Seems the latest version forked from the official FFmpeg not long again and patched. It definitely used to have a lot better transport stream handling and professional formats available for both input and output. (We used it on Linux boxes used for ingesting of news media for a company I used to work for where xmf and imx formats were required and not supported by FFmpeg.)

---

### Post by roler2 on 2016-06-15
[COLOR=#000000]*The following NEW packages will be installed:*[/COLOR]
[COLOR=#000000]*libavcodec57 libavdevice57 libavfilter6 libavformat57 libavresample3 libavutil55 libpostproc54 libswresample2*[/COLOR]
[COLOR=#000000]*libswscale4*[/COLOR]
[COLOR=#000000][I]The following packages will be upgraded:
ffmpeg

[/I][/COLOR]Is there a way to install ffmpeg with all the dependencies listed without utilizing the PPA? I tried to install ffmpeg using the current .deb file on the ffmpeg web site however it stated that the listed dependencies are necessary for installation. Is there a way to install the dependencies because using GDebi does not install the dependencies like it normally does for other .deb installations. Lubuntu 16.04 (that PPA I think is the one which messed up my installation-be careful-apparently it uninstalls some very important files associated with Lubuntu and there is no other fix other than a complete reinstall).[COLOR=#000000][I]
[/I][/COLOR][COLOR=#417394][I]
[/I][/COLOR]

---

