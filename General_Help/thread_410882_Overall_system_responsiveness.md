---
title: "Overall system responsiveness"
date: 2007-04-16
forum: General Help
---

### Post by Brucevdk on 2007-04-16
This is sort of discussed in several other threads, but usually it boils down to somebody incorrectly installing the drivers for their chipset/video card. Some threads also compare Windows XP to Ubuntu (and GNU/Linux in general), but I feel a separate topic is warranted.

My generic system specs (summarized): IBM ThinkPad R51 2887AVG (Intel Centrino (Pentium M) 1.5GHz, Intel 82852/855GM Integrated Graphics and 768MB RAM). You can find the output to several commands such as lspci and glxinfo below, I have also attached my xorg configuration (xorg.conf). 

I'm using GNOME and running Ubuntu (Edgy Eft), the system (GUI) feels a lot less responsive overall compared to Microsoft Windows XP, especially when scaling the CPU frequency down to for example 600MHz. I personally wouldn't call it slow, but it is definitely noticeable. As far as I know it wasn't any different in any of the previous versions (i.e. Breezy Badger and Dapper Drake) nor has it improved in Feisty Fawn. This makes me wonder whether this is "as good as it gets" for the time being. 

I'm not sure if it is perception but when I ALT + Tab around it just doesn't seem very snappy. It is most noticeable when you cycle through tabs in Mozilla Firefox, or a text-editor such as SciTE (universe) by keeping CTRL + TAB pressed for a while (though you'll notice it with gVim too). You'll notice a delay in rendering, especially in SciTE which takes several seconds to become responsive again.

Since I personally do not know any other GNU/Linux users nor do I have any systems other than my laptop at my disposal, I recently went to a local LUG meeting so I could verify if the issue exists over a wide range of configurations and distros. I was  hoping that the issues were system specific. However, all of the systems there felt the same in terms of responsiveness. A member of that user group did inform me a little bit about the underlying client/server architecture, i.e. the X Window System and hinted that this might have something to do with it but obviously it's a very generic "problem" which could have any number of causes. 

Everybody did tell me it used to be a lot, and when I say that I really do mean a lot, worse. There's also a LUG radio episode where the "speed" (responsiveness) of GNU/Linux is discussed, you can find it at [http://www.lugradio.org/episodes/74](http://www.lugradio.org/episodes/74). MacSlow (author of lowfat) responds to this in the forums, see [Ade, X11 is not slow!]("http://forums.lugradio.org/viewtopic.php?t=3341"). I haven't watched the whole talk on AIGLX mentioned in that thread, but it does seem interesting and relevant.

I have come to these forums more or less for the same reason I went to the LUG meeting, to find out whether somebody is able to offer some more detailed insight into this situation. Perhaps I could have discussed it in the appropriate mailing lists, such as those of xorg or even application specific ones such as scite-interest but I'm not very experienced in that form of discussion. 

**Relevant threads and links**
[LIST]
[*] Post by poofyhairguy in the thread [linux responsiveness]("http://ubuntuforums.org/showpost.php?p=589624&postcount=6") in which the following link is mentioned, [http://jonsmirl.googlepages.com/graphics.html](http://jonsmirl.googlepages.com/graphics.html) (The State of Linux Graphics by Jon Smirl, dated August 30, 2005). The link offers an abstract technical view of everything related to X, but this doesn't make it "an easy read". A relevant excerpt (the whole article is relevant, but this is an interesting statement in and by itself): *"Linux is now guaranteed to be the last major desktop to implement a desktop GUI that takes full advantage of the GPU."*.
[/LIST]

**Warnings and errors from Xorg.0.log**
These are just the warnings grepped from the log, obviously the log itself contains a lot more information (plus it places these warnings into context) so I've attached the full log (see below).

```

(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
(WW) The directory "/usr/share/fonts/X11/CID/" does not exist.
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): VideoRAM reduced to 61440 kByte (page aligned - was 64000)
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 384 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 384 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 12545 pages failed
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

```

**System specifications and miscellaneous information**
```

$ dmesg | head -1
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Mar 13 23:32:38 UTC 2007 (Ubuntu 2.6.17-11.37-generic)

$ cat /etc/issue
Ubuntu 6.10 \n \l

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

$ cat /proc/cpuinfo | egrep "model name|MHz"
model name      : Intel(R) Pentium(R) M processor 1.50GHz
cpu MHz         : 1500.000

$ xdpyinfo | egrep "version:|dimensions|depth of"
X.Org version: 7.1.1
  dimensions:    1024x768 pixels (347x260 millimeters)
  depth of root window:    16 planes

$ glxinfo | egrep "direct|vendor|version|renderer"
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
GLX version: 1.2
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
glu version: 1.3

```

Here's the output of glxgears -printfps, just an indication. The "benchmarks" at [http://www.free3d.org/](http://www.free3d.org/) lists an FPS count of 1433 for the same chipset (Intel 82852/855GM Integrated Graphics Device (rev 02)) using the same resolution and depth settings.

```

libGL warning: 3D driver claims to not support visual 0x4b
4517 frames in 5.0 seconds = 903.296 FPS
4526 frames in 5.0 seconds = 905.031 FPS
4522 frames in 5.0 seconds = 904.286 FPS
4531 frames in 5.0 seconds = 906.028 FPS

```

---

### Post by MacSlow on 2007-04-20
Greetings Bruce!

The likely cause for a "slowness"- or "not as fast as it could be"-impression with Xorg and a composited environment (especially on OSS drivers using AIGLX) is the way memory is managed between the 3D/DRI-driver and the xserver at the moment. These (DRI-driver, xserver) are two seperate processes, which each have their own copy of a drawable (read: pixmap of a window... window in a X11-sense... not in a window-manager sense). In order to synchronize (for content-consistency reasons) these two copies of the same thing, it needs to do a lot of work, which would be not needed, if there would only be once single copy.

With the new memory-manager, which will unify this issue for DRI and the xserver, a good speed-up should be the result in the end. There are also some more things (not related to compositing and DRI) to improve in Xorg in general, which all will lead to better overall performance. But I'm no Xorg-hacker and don't know the details.

You should really take the time and watch the whole FOSDEM2007-talk from Kristian.

I admit that it is confusing and not easy to understand, if one does not follow happenings in Xorg frequently, and one isn't very keen on software-development. In addition to that tinkering around these low levels in the stack (graphics sub-system, drivers) is not easy to digest by nature.

Best regards...

MacSlow

---

