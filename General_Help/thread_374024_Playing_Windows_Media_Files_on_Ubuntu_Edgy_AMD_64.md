---
title: "Playing Windows Media Files on Ubuntu Edgy AMD 64"
date: 2007-03-02
forum: General Help
---

### Post by unebaguettesvp on 2007-03-02
Hi All!

Has anyone been able to play Windows Media Files on Ubuntu Edgy with AMD 64 architecture using xine-lib?!

I can't figure out how to do it. I'm very new to Linux. So, I apologize in advance.

This is what I have done so far:

I downloaded, compiled, and installed xine-lib 1.1.4 successfully. I downloaded, compiled, and installed gxine 0.5.11 successfully. I can view avi, divx, and quicktime with absolutely no problem whatsoever.

When I try to play a WMV9 file, the video is only OK but there is NO SOUND!!!

I did this:

wget -c
http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb<br /> sudo dpkg -i --force-architecture w32codecs_20061022-0.0_i386.deb

which I got from here:
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

That didn't change anything. Then on the same page, I saw a problem with
no sound:

[http://ubuntuforums.org/showpost.php?p=136306&postcount=2](http://ubuntuforums.org/showpost.php?p=136306&postcount=2)

I looked in catalog.cache, and this entry doesn't exist:
[/usr/lib/xine/plugins/1.0.0/xineplug_decode_w32dll.so]

That other page says that:
"The Windows Codecs package cannot be used directly by the AMD64
distribution."

Is this true?

I've spent a week on this already and I still have no luck. Has anyone
gotten this to work?

Before I compile, do I need to have the win32 codecs installed? Or does it matter? Because I compiled xine-lib before installing the codecs. How would I go about uninstalling xine-lib?

-Phil

---

### Post by SaddisticTwist on 2007-03-02
Hello, I'm not to sure, but the 64 does not support certain formats and software as of yet. Though there are alternatives; example running a 32bit application in the 64bit OS. 

You can find more information here [http://www.ubuntuforums.org/showthread.php?t=191205]("http://www.ubuntuforums.org/showthread.php?t=191205")

The link should provide you with more information about running, different media formats in the 64 enviroment.

---

### Post by wankykootiepooper on 2007-03-02
Hello.

I am also running an AMD64 box.  I am using MPlayer, with the MPlayer plug in for Firefox.

I can play WM8, but not WM9.  As you also said, everything else works fine.

I also run some of my machines on Gentoo.  I can tell you from my experience in that camp that you cannot simply install 32bit codecs and get them to work on a native AMD64 player.  The way I had it working on another machine was to install a 32 bit version of MPlayer running 32 bit codecs and a 32 bit version of MPlayerplug-in for Firefox, which generally worked on most media.

In the link you specify, there are two ways suggested to create a 32 bit environment to run mplayer with these codecs in a VServer.  I'm comfortable dealing with kernel issues, but a lot of people aren't, so I'm not certain whether this helps you or not.

You can also find a different VServer howto at: [http://wiki.u32.net/Ubuntu-VServer](http://wiki.u32.net/Ubuntu-VServer)

I will be fixing this one way or another in the next few weeks.  I'll keep you posted.

Eric.

---

