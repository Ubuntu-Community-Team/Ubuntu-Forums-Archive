---
title: "Samsung 226BW Quirks?"
date: 2007-05-22
forum: General Help
---

### Post by eklitzke on 2007-05-22
Hi everyone,

I recently purchased a shiny new Samsung 226BW monitor. This is a 22" widescreen monitor that runs at 1680x1050. I have been using it for a couple of days on a noisy old Pentium III computer with some integrated Intel graphics chipset (pre-800/900 series), and it actually worked perfectly -- I literally just plugged the monitor in and I was working at the native resolution without tweaking anything.  I got my laptop back (from some repairs) today, and with the Intel 800 series graphics cards, the monitor doesn't work.

The first step I took was to use the 915resolution utility to patch the video BIOS; I have done this in the past with my particular chipset (Intel 855GM) to get it to work with a 1440x900 monitor. I read the documentation for this program (and even downloaded and compiled the latest upstream release), and consequently ran
```
915resolution 5c 1680 1050 32
```
I am running this using mode 5c, since I don't need that mode (it is by default configured to be used for 1920x1200@32), but I get the same results running any other mode. After running the 915resolution program and editing my xorg.conf file, restarting the X server does in fact bring the monitor up at 1680x1050. The problem is that the physical dimensions of the image are too large. What I mean is that if I move my mouse to the sides or bottom of the image, the mouse disappears and continues to move for about an inch or so.  This is even after using the autoadjust feature on the monitor, or manually setting the vertical/horizontal offset on the monitor, although this is really a problem with the size of the image, not its placement.  The image also looks a tiny bit stretched (little enough that some people might not notice it, except for the cropped edges), which seems to confirm that the physical dimensions of the displayed image are to blame.

I can't find it right now, but earlier I found a patch from April (2007) that adds some code to X11 that handles a DDC quirk in the Samsung 226BW.  I'm not sure about Feisty, but I checked on the Gutsy install that I have on another partition, and at least in that installation the patch is already part of the xserver-xorg-core package, and it does not work in Gutsy either. So I don't think this is the problem (not to mention, it worked on the older computer with a different video chipset).

Here is the monitor section I am using in my /etc/X11/xorg.conf
```
Section "Monitor"
        Identifier      "Samsung 226BW"
        Option          "DPMS" "true"
        VertRefresh 56-75
        HorizSync   30-81
        DisplaySize 474 296
        Mode "1680x1050"
                DotClock 119.0
                HTimings 1680 1728 1760 1840
                VTimings 1050 1053 1059 1080
        EndMode
EndSection
```

Here are the pertinent lines from the Xorg.0.log
```
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) I810(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) I810(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 119.0 MHz   Image Size:  474 x 296 mm
(II) I810(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) I810(0): Monitor name: SyncMaster
(II) I810(0): Serial No: H9NP306295
(II) I810(0): EDID (in hex):
(II) I810(0):   00ffffffffffff004c2d7e023232454d
(II) I810(0):   0c1101030e2f1e782ad515a455499a27
(II) I810(0):   145054bfef80b30081808140714f0101
(II) I810(0):   0101010101017c2e90a0601a1e403020
(II) I810(0):   3600da281100001a000000fd00384b1e
(II) I810(0):   510e000a202020202020000000fc0053
(II) I810(0):   796e634d61737465720a2020000000ff
(II) I810(0):   0048394e503330363239350a202000cd
(II) I810(0): Using hsync ranges from config file
(II) I810(0): Using vrefresh ranges from config file
```

Note in particular that the mode timings in my xorg.conf file match those from the DDC information given out by the monitor.

Has anyone gotten this monitor working correctly on an Intel 800/900 series chipset? If so, do you have any pointers for me?

Thanks a lot!

---

### Post by capdog on 2007-05-22
Hi there

I am having the exact same headaches. I recently started another thread:

[http://ubuntuforums.org/showthread.php?t=450796](http://ubuntuforums.org/showthread.php?t=450796)

..about this issue, I have the Samsung 226BW and the Intel 950 GMA onboard graphics card (hewlett packard laptop).

As yet, no solutions, but I can point you to further resources to see if you can get any ideas. The first is someone with identical hardware to mine who posted a solution on the Debian forums...

[http://forums.debian.net/viewtopic.php?t=14242](http://forums.debian.net/viewtopic.php?t=14242)

I can't seem to get it to work, although I suspect I'm close and merely doing a small thing wrong. I am dying to get my hands on his xorg.conf, but I can't seem to locate him. He also links to the following:

[http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux](http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux)

Which is not the exact model of monitor but it's the same problem.

Those are by far the best bits on info I've got my hands on. The other solution is to install the xserver-xorg-video-intel package which replaces i810 driver with a build of the new intel drivers and is supposed to negate the need for the 915resolution hack. This didn't work for me (see my thread).

Please, please post your solution or any other methods you try! Thanks!

---

### Post by capdog on 2007-05-22
Got it to work! Here is the link:

[http://ubuntuforums.org/showthread.php?p=2702458](http://ubuntuforums.org/showthread.php?p=2702458)

---

### Post by eklitzke on 2007-05-23
I actually tried all the advice in that howto already, and none of it worked for me.  I did, however, notice that the author wrote something about the xserver-xorg-video-intel driver, which is a replacement for the i810 driver.  I installed this driver and replaced the video card driver (the line now says "intel" where it previously said "i810"), and now everything works!  You don't even have to use 915resolution with the intel driver.  The only caveat is that xv seems to be unsupported with this driver, so you will have to use the x11 driver for mplayer and the like.

---

### Post by itaylor on 2008-01-07
Thanks eklitzke,
I tried all this for the similar Samsung 2232BW (same resolution as 226BW) and also only had success after installing the xserver-xorg-video-intel driver (on Thinkpad Z61t running Gutsy).

---

