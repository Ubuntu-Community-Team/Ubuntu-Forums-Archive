---
title: "Xine trouble!"
date: 2006-07-19
forum: General Help
---

### Post by Xecuter on 2006-07-19
I installed Xine and tried to watch a DVD, but I got a message about frame-drops and were told to run xine-check.

First problem: No xine-lib is installed. Where can I get it? I've been searching all over for it but I haven't found it.

Edit: An output of xine-check.
```
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.15-26-k7)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc

[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...
         press <enter> to continue...

```

---

### Post by Ramses de Norre on 2006-07-19
```
sudo aptitude install libxine-main1 libxine-extracodecs
```

---

### Post by Xecuter on 2006-07-19
> **Ramses de Norre said:**
> ```
sudo aptitude install libxine-main1 libxine-extracodecs
```

Nope. xine-check shows the same! They where allready installed.

---

### Post by Xecuter on 2006-07-19
bump

---

### Post by jefffq on 2006-07-29
I have the **exact same** problem (all the same xine-check output). I'm guessing you're using 6.06 and installed xine with apt-get and did nothing funky, like me. Has anyone out there solved this?

I have noticed that VLC plays videos better, but still not perfect.

I tried [this]("http://www.ubuntuforums.org/showthread.php?t=12799"). It didn't help.

:(

---

### Post by jefffq on 2006-07-29
Well, after combining the methods of various howtos and forum posts, I finally managed to get video files and DVDs to play smoothly even in fullscreen.

I had the ATI drivers installed (from EasyUbuntu), but I didn't have the kernel headers installed so DRI couldn't function. So first off I installed the appropriate headers through apt-get.

Then I just had to add some lines to xorg.conf and restarted X.

In the 'module' section I added 'load "dri"'.

In the 'device' section I added the following lines:
    option "UseInternalAGPGART" "no"
    Option "RenderAccel" "true"
    Option "VideoOverlay" "on"

I ran xine-check again and the stuff about overlays was gone. It still wines about the multiple instances and lack of xine-lib, but I think that's just the weird way Ubuntu is installing it.

I hope that works for you too Xecuter.

---

### Post by ykram on 2006-07-30
I took have the same error message:
             [ hint ] Your X server doesn't support YV12 overlays.
So I decided to take your advice and try what you did but alas, still no go. I'm using the fglrx driver for a Radeon 9250 and has problems with fglrx not being used but mesa instead (turns out it was a composite problem). In any event, I'm still unable to fix this YV12 overlay problem presented by xine-check.

    Option "RenderAccel" "true"
    Option "UseInternalAGPGart" "no" 
    Option "VideoOVerlay" "on" 

is what I added to my xorg.conf. I also seem to be having a problem with video not being shown on the 2nd LCD (using fglrx driver for both Device Sections. I should specify by saying it'll work up to a point until it gets to mid screen, mplayer will go blank and fgl_glxgears will not show the OpenGL animation while reporting FPS in excess of 250. Anybody else have these problems? (I'm using the old fglrx driver since new ones provided by dapper don't seem to work properly with my old card)

---

### Post by jefffq on 2006-08-02
Do you have your kernel-headers installed and the "load dri" line in xorg.conf?

I don't think a slightly older fglrx driver should matter, the resources I was going from were working with older drivers. What did you mean about it using mesa? The stuff I was mentioning relies entirely on it using fglrx and not mesa.

As for videos not playing in the second monitor ... There are technical things surrounding this issue that I'm not knowledgeable in, I'm just aware that they're there and it is a real thing. Different players seem to respond differently and have different tricks to coax it into the desired monitor. :???:

---

### Post by cantormath on 2006-08-02
Here:
Use this
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

follow the directions, install automatix.
Run automatix, it will install all the codecs for you for dvd and every other thing.
Install the players, Mplayer, and codecs.  Install the java and flash to if you havent done that right.

It does it for you, just click away.

Install anything else you see that you like.

---

