---
title: "Problems with AMD graphics in 15.10"
date: 2016-02-18
forum: General Help
---

### Post by A.R.B on 2016-02-18
I think it's really Crazy that all the Ubuntu flavours have been released with a Serious Graphics FGLRX 15.10 Problem! :(

---

### Post by QIII on 2016-02-18
What problem are you encountering?

---

### Post by A.R.B on 2016-02-19
> **QIII said:**
> What problem are you encountering?

Well! I am Amazed at your reply ??? Have you not seen on the internet forums Etc. that 1000's of people are having problems with the fglrx graphics ?

Just take a look at the links below for more info...

[http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem](http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem)


[http://askubuntu.com/questions/620869/15-04-installed-fglrx-amd-ati-drivers-wont-boot](http://askubuntu.com/questions/620869/15-04-installed-fglrx-amd-ati-drivers-wont-boot)


[http://www.thinkwiki.org/wiki/Problems_with_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx)


[https://www.reddit.com/r/linux_gaming/comments/3nzdoc/anyone_else_have_issues_with_fglrx_and_kernel_42/](https://www.reddit.com/r/linux_gaming/comments/3nzdoc/anyone_else_have_issues_with_fglrx_and_kernel_42/)


[https://community.amd.com/thread/183174](https://community.amd.com/thread/183174)


So if you managed to see the problems above people are having including myself, then all we want is a Fix for the fglrx graphics so that we can click on Software & Updates without having to be a Technical Linux wizard, and just download and update our Systems so that they work in the way they are supposed to! :(
Or if someone can upload a Debian Complete package containing all the files & dependencies needed for Ubuntu/Lubuntu 15.10 so we can install it on our Systems that way.

---

### Post by cariboo on 2016-02-19
It would be better if you gave us the details about your problem instead of linking to problems others have had. There are many users that are using AMD graphics without any problems.

---

### Post by A.R.B on 2016-02-19
> **cariboo said:**
> It would be better if you gave us the details about your problem instead of linking to problems others have had. There are many users that are using AMD graphics without any problems.

OK! First I will give you My Linux Set up details...

Desktop PC, Mini Micro Tower, Motherboard Gigabyte,  (Spare Computer...for backups Etc.)

AMD A4-3300 APU with Radeon(tm) HD Graphics,Radeon HD 6410D,4GB 1600 Mhz Ram.

Below is a Full Install after the HD had been Formatted so it's a fresh Install...Just like to mention I used the Encrypt the "Home Folder" Password Option.

Lubuntu 15.10 (wily) 64 Bit, GNOME 3.16.2, Kernel 4.2.0-29-generic.

I installed Lubuntu 15.10 on the above system (Very carefully!) plus I updated the System completely with all the build-dep's needed,so that the System is running perfect!
I then noticed that the Graphics display on the TV/Monitor on HDMI I am using was not very clear ? the best I can describe it is that the colours are not clear ? and that it looks like lower quality pixels ?
So I then installed the fglrx graphics using the Synaptic manager and restarted the Computer,which resulted in the TV/Monitor looking much the same as before :(
I then tried changing the Settings in the fglrx amd Catalyst GUI for the display,and first it would not let me do it using the standard GUI so I tried to use the Administrator GUI,and it would not show the GUI to be able to do the changes ? so I logged in as Root user,now I was able to change the settings,I increased everything to make it look better,then restarted the Computer,and it was still the same :(
So basically the fglrx amd Catalyst is not doing what it is supposed to do,or is it something to do with the fact that I am using the HDMI ouput to the TV/Monitor ?

I just looked at the  AMD site below using the "Manualy Select Your Driver" for the fglrx amd Catalyst for My Computer :)


AMD Drivers & Software downloads


[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)


................................................................


For the Option below... 


Step 4:  Select the supported operating system that you have:


If I enter (Linux x86_64) it recomends 


AMD Catalyst™ 15.9 Proprietary Linux x86 Display Driver


....................................................................................................................


And For the same Option below... 


Step 4:  Select the supported operating system that you have:


If I enter (Ubuntu x86_64) it recomends a whole load of different Versions :(


AMD Catalyst™ 15.9 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators
AMD Catalyst™ 15.9 Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support)
AMD Catalyst™ 15.9 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators Devel Files (OGL, OCL)
AMD Catalyst™ 15.9 Proprietary Ubuntu 14.04 x86_64 Catalyst Control Center
AMD Catalyst™ 15.9 Proprietary Ubuntu 12.04.4x86_64 Video Driver for Graphics Accelerators
AMD Catalyst™ 15.9 Proprietary Ubuntu 12.04.4 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support)
AMD Catalyst™ 15.9 Proprietary Ubuntu 12.04.4 x86_64 Video Driver for Graphics Accelerators Devel Files (OGL, OCL)
AMD Catalyst™ 15.9 Proprietary Ubuntu 12.04.4 x86_64 Catalyst Control Cente


....................................................................................................................


So now I am even more Confused as to which one I need ?

Below is some of the best Help & Info I could find...

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-4.2-Cat-Not-Ready](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-4.2-Cat-Not-Ready)

---

### Post by mörgæs on 2016-02-19
You don't have to add *Please! Please!* to the title. It will not give you a faster response.

In Buntu we can not expect non-security bugs to be fixed in anything but the development version which is 16.04 at the moment. From time to time they do get fixed in released versions but don't take it for granted.

Best you can do is to see how it works in 16.04.

---

### Post by QIII on 2016-02-19
> Well! I am Amazed at your reply ??? Have you not seen on the internet forums Etc. that 1000's of people are having problems with the fglrx graphics ?

You might do well to be a little less shrill.  Your demanding tone is more likely to turn the volunteers here off than to garner support.  We are all *volunteer* users like you and cannot control what the developers or packagers at Canonical do.  We cannot control what AMD does.

If you will look at my signature, you might take a hint that I do follow AMD graphics issues more than casually and have written great swaths of that wiki article.  I am also involved in many of the bug reports with regard to AMD graphics on Launchpad.  I asked you about *your* issues specifically for a *reason*.  Finding articles about problems with this or that is easy -- finding articles dealing with a particular issue that might affect you is somewhat more difficult.  

Every one of your referenced links, except for the one from Phoronix, is old enough that it likely has nothing at all to do with your problem.  One of your references comes from *2009*.  A few months ago there was a problem specific to fglrx and 15.10 -- a problem, mind you, that had nothing to do with anything Canonical had done but with the fact that AMD did not update fglrx properly to work with the version of gcc in 15.10:  it wouldn't compile properly into the kernel.

That is the issue referenced in the Phoronix article, and it has been resolved -- despite the fact that it is a problem AMD created.  By the way, I even blogged about this issue with more detailed inside information than Phoronix had at the time of that article.

"Everyone is having problems" is quite vague and it is also not quite true.  I don't have problems with it and I was testing it along with the process of some very good people at Canonical dealing with the gcc issue and installation as that progressed.

Now -- on to your issue.

Some of the lower spec A series APUs have been known for some time to have issues when used with AMD's proprietary Linux driver.  That is nothing anyone at Canonical or here on the forums can do anything about.  The fglrx driver is proprietary and closed source.  It can't be changed by any open source developer or distribution purveyor.  For many, these issues have been resolved by using the open source Radeon driver.  I don't know if that would be the case for you.  In any case, demanding that anyone in the open source community should help to fix a proprietary driver is pointless.

However, if you would care to attach a screenshot of your desktop so we can see exactly what you are talking about it would be very helpful.  We might be able to help you discover how to resolve the issue using the Catalyst Control Center.

---

### Post by A.R.B on 2016-02-19
> **mörgæs said:**
> You don't have to add *Please! Please!* to the title. It will not give you a faster response.

In Buntu we can not expect non-security bugs to be fixed in anything but the development version which is 16.04 at the moment. From time to time they do get fixed in released versions but don't take it for granted.

Best you can do is to see how it works in 16.04.

OK! I removed the Please! Please! to "NOTICE!!!" :)

> **QIII said:**
> 
"Everyone is having problems" is quite vague and it is also not quite true.  I don't have problems with it and I was testing it along with the process of some very good people at Canonical dealing with the gcc issue and installation as that progressed.

Now -- on to your issue.

Some of the lower spec A series APUs have been known for some time to have issues when used with AMD's proprietary Linux driver.  That is nothing anyone at Canonical or here on the forums can do anything about.  The fglrx driver is proprietary and closed source.  It can't be changed by any open source developer or distribution purveyor.  For many, these issues have been resolved by using the open source Radeon driver.  I don't know if that would be the case for you.  In any case, demanding that anyone in the open source community should help to fix a proprietary driver is pointless.

However, if you would care to attach a screenshot of your desktop so we can see exactly what you are talking about it would be very helpful.  We might be able to help you discover how to resolve the issue using the Catalyst Control Center.

Hi

Thank you for so much info :) Regarding your Quote: "I don't have problems with it" could you explain better Why it works for you and not so many other People ?
And your Quote: "Some of the lower spec A series APUs have been known for some time to have issues when used with AMD's proprietary Linux driver"
 I have never had any problems with the System I am using running other versions of Lubuntu,it's only with some recent Versions ? I have always used the standard Default set up out of the box! I only tried the fglrx drivers because the standard Default set up out of the box! no longer works! :(
A Screenshot of My desktop would not help because it's hard to see from an image of the Screen that there are any problems,it's one of those situations where from previous experience and usage a person can just see that it's not as good or clear as it was before! a good example is using Wine,then it is more Noticeable,in fact I will try and upload a Wine Screen shot to show what I mean (maybe that's a good way to get an idea) ?

---

### Post by mörgæs on 2016-02-19
> **A.R.B said:**
> OK! I removed the Please! Please! to "NOTICE!!!"

(sigh...)

---

### Post by QIII on 2016-02-19
> **A.R.B said:**
>  could you explain better Why it works for you and not so many other People 

No, I can't.  That's why I am asking you for diagnostic information.

 > I have never had any problems with the System I am using running other versions of Lubuntu,it's only with some recent Versions ? I have always used the standard Default set up out of the box! I only tried the fglrx drivers because the standard Default set up out of the box! no longer works! 

Then you have thrown in a red herring by mentioning the fglrx driver.  If you have not been using it before, then the discussion should be limited to why the open source driver was working before and now is not.

---

### Post by A.R.B on 2016-02-19
> **QIII said:**
> 
Then you have thrown in a red herring by mentioning the fglrx driver.  If you have not been using it before, then the discussion should be limited to why the open source driver was working before and now is not.

Very good point! for some reason I just thought it was a general problem with the latest Lubuntu releases concerning all the Graphics drivers,it must have been something to do with reading so many problems using the fglrx driver,that I assumed everyone had moved over to it as part of the latest distributions,so Yes! "why does the open source driver that was working before not work now!" ?  :)  :(

---

### Post by QIII on 2016-02-19
First questions then:

Were you using the same TV/monitor before?

Have you attempted to adjust the picture using the menu on the monitor?

---

### Post by Bashing-om on 2016-02-19
A.R.B; :)

Me run ATI graphics card;
Me use open source driver;
Me have no problem with the card/driver in 15.10 .

As QIII advises ^^ we get specifics on your problem, we can give specifics on a probable solution .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by A.R.B on 2016-02-20
> **Bashing-om said:**
> A.R.B; 

Me run ATI graphics card;
Me use open source driver;
Me have no problem with the card/driver in 15.10 .

As QIII advises ^^ we get specifics on your problem, we can give specifics on a probable solution .[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]together we can
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


You forgot the "Me also have problems with fglrx Graphics drivers"

> **QIII said:**
> First questions then:

Were you using the same TV/monitor before?

Have you attempted to adjust the picture using the menu on the monitor?

Yes! I have always used the same TV/monitor as before! and have not adjusted the picture monitor settings.

OK! So now that I have woken up :( after it being pointed out to me that the 15.10 Graphics problems are not just with fglrx drivers, but actually with the FREE! open source drivers that come with a fresh install of Lubuntu 15.10 straight out of the Box!

So now the Detective work can really Start by me giving as much info as possible 

First of all I have now done a fresh install on a Asus 15.6'' laptop and a Samsung 10'' Net-book,using Lubuntu 15.10 and there are No! problems with the Graphics using the FREE! open source drivers 
So from the info above the Graphics problem I am having using the Micro PC connected to a HDMI output going to a TV/monitor must be the problem ? I think! ?
More info I first had the problems above after doing a fresh install using the latest Versions of Lubuntu,the last good Version that worked with no problems was 13.10 then as soon as I tried the 14.+ Versions I started to get the Graphics problems,so what has changed from the previous Version 13.10 to the latest Versions ? I imagine loads!
After thinking about it a bit more,would it be possible to use the 13.10 FREE! open source drivers in 15.10 ?

The FREE! open source drivers that are installed on my 15.10 System are below...

xserver-xorg-video-ati (X.Org X server -- AMD/ATI display driver wrapper)

xserver-xorg-video-radeon (X.Org X server -- AMD/ATI Radeon display driver)

I have recently heard about something called "Blacklist" from trying to get the fglrx drivers to work,there was something mentioned that "The fglrx packages should blacklist amdgpu so that the said driver does not prevent fglrx from loading" could this now/also be happening in some way using the FREE! open source drivers ?
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1510573](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1510573)

I had a look in the folder /etc/modprobe.d which is where I believe the "Blacklist" files are I noticed (blacklist-framebuffer.conf) ? listed below maybe there is something there ?

```
# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist bochs-drm
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
#blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
blacklist udlfb
```

And finally for the moment :) attached is a Desktop Screen Shot showing "Google.com" you will notice around the edges of the letters that they look Fuzzy/Jagged not clear ?
and one final thought! could the above problems be anything to do with something as simple as the Type of Fonts now used in Lubuntu 15.10 ?

I just had a look at the Desktop Screen Shot showing "Google.com" from my Micro PC using the Asus laptop and it's hard to see if there is anything wrong with it ? so the Screen shot works OK on the Micro PC,but when you are actually using the Monitor it looks Fuzzy/Jagged not clear

OK! I think I might be getting to the bottom of this problem! :) the Screen Shot that was correct as an image saved,but not as the actual Screen I am looking at has helped,so I think I am looking at a lower Screen size on the TV/Monitor using the HDMI ? than the Screen Shot of 1366 x 768

I just Booted the Computer into Recovery mode,and I noticed from the text "error no ums support in radeon module"

After a look on the web I found the command (dmesg | grep radeon) so I ran it with the results below...

```
[    1.526703] [drm] radeon kernel modesetting enabled.
[    1.534418] fb: switching to radeondrmfb from VESA VGA
[    1.535232] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.535234] radeon 0000:00:01.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.535327] [drm] radeon: 512M of VRAM memory ready
[    1.535329] [drm] radeon: 1024M of GTT memory ready.
[    1.535509] [drm] radeon: dpm initialized
[    1.549857] radeon 0000:00:01.0: WB enabled
[    1.549861] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034ef5c00
[    1.549863] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034ef5c0c
[    1.550589] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90000c32118
[    1.550594] radeon 0000:00:01.0: radeon: MSI limited to 32-bit
[    1.550627] radeon 0000:00:01.0: radeon: using MSI.
[    1.550653] [drm] radeon: irq initialized.
[    2.280635] fbcon: radeondrmfb (fb0) is primary device
[    2.280747] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    2.280749] radeon 0000:00:01.0: registered panic notifier
[    2.286322] [drm] Initialized radeon 2.43.0 20080528 for 0000:00:01.0 on minor 0
```

All a bit Gobbledygook to me :( but someone may be able to see something,I think I have to change something in the Kernel itself ?

Any Help ? I am still looking at it ...

[https://bbs.archlinux.org/viewtopic.php?id=166037](https://bbs.archlinux.org/viewtopic.php?id=166037)

[https://forums.opensuse.org/showthread.php/501077-No-UMS-support-in-radeon-module-no-X](https://forums.opensuse.org/showthread.php/501077-No-UMS-support-in-radeon-module-no-X)

I Just found another Command (dmesg | egrep "drm|radeon") with the output below...

```

[    1.493431] [drm] Initialized drm 1.1.0 20060810
[    1.526703] [drm] radeon kernel modesetting enabled.
[    1.534418] fb: switching to radeondrmfb from VESA VGA
[    1.534877] [drm] initializing kernel modesetting (SUMO2 0x1002:0x9645 0x1458:0xD000).
[    1.534892] [drm] register mmio base: 0xFDFC0000
[    1.534893] [drm] register mmio size: 262144
[    1.535232] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.535234] radeon 0000:00:01.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.535236] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.535237] [drm] RAM width 32bits DDR
[    1.535327] [drm] radeon: 512M of VRAM memory ready
[    1.535329] [drm] radeon: 1024M of GTT memory ready.
[    1.535339] [drm] Loading SUMO2 Microcode
[    1.535405] [drm] Internal thermal controller without fan control
[    1.535452] [drm] Found smc ucode version: 0x00011100
[    1.535509] [drm] radeon: dpm initialized
[    1.535673] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.549715] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    1.549857] radeon 0000:00:01.0: WB enabled
[    1.549861] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034ef5c00
[    1.549863] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034ef5c0c
[    1.550589] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90000c32118
[    1.550591] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.550592] [drm] Driver supports precise vblank timestamp query.
[    1.550594] radeon 0000:00:01.0: radeon: MSI limited to 32-bit
[    1.550627] radeon 0000:00:01.0: radeon: using MSI.
[    1.550653] [drm] radeon: irq initialized.
[    1.567362] [drm] ring test on 0 succeeded in 1 usecs
[    1.567371] [drm] ring test on 3 succeeded in 3 usecs
[    1.613113] [drm] ring test on 5 succeeded in 1 usecs
[    1.632988] [drm] UVD initialized successfully.
[    1.633391] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.633427] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.150083] [drm] ib test on ring 5 succeeded
[    2.171289] [drm] Radeon Display Connectors
[    2.171293] [drm] Connector 0:
[    2.171294] [drm]   VGA-1
[    2.171296] [drm]   HPD2
[    2.171298] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.171299] [drm]   Encoders:
[    2.171300] [drm]     CRT1: INTERNAL_UNIPHY2
[    2.171301] [drm]     CRT1: NUTMEG
[    2.171302] [drm] Connector 1:
[    2.171303] [drm]   HDMI-A-1
[    2.171304] [drm]   HPD1
[    2.171305] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.171306] [drm]   Encoders:
[    2.171307] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.280538] [drm] fb mappable at 0xD0478000
[    2.280540] [drm] vram apper at 0xD0000000
[    2.280541] [drm] size 4325376
[    2.280542] [drm] fb depth is 24
[    2.280543] [drm]    pitch is 5632
[    2.280635] fbcon: radeondrmfb (fb0) is primary device
[    2.280747] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    2.280749] radeon 0000:00:01.0: registered panic notifier
[    2.286322] [drm] Initialized radeon 2.43.0 20080528 for 0000:00:01.0 on mino
```

OK! I just found your Ubuntu/RadeonDriver help section

 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

After reading through it,I noticed in the (xorg.conf) that it was referring in some way to the (Driver  "fglrx") ? which I had removed thoroughly by purging it etc. :( then  it said that I can remove the (xorg.conf) as Modern Systems can run without it! :) or something like that.
I Restarted the computer and it started! but everything was still the same as before ? :(  I feel that something could be done to the (xorg.conf) to Solve my Graphics problem! but I don't know what ?

Below is the (xorg.conf) content before I removed it where you will see the (Driver  "fglrx") being used for something ? ...

```
Section "ServerLayout"    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection


Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:0:1:0"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



```

I found this help below...

[http://ubuntuforums.org/showthread.php?t=2215592&](http://ubuntuforums.org/showthread.php?t=2215592&)

And so from the above I done everything below,and nothing is Solved!! :(

```
sudo apt-get remove --purge fglrx*sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
(No point running sudo dpkg-reconfigure xserver-xorg as it is now a deprecated command and does nothing any more.)


sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers (A.R.B this returned an Error) ? so I just carried on...
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-core


sudo apt-get install lubuntu-desktop


Restarted the Computer...


Same as before! :)
```

Just when I was giving up...

I found these links about HDMI & xorg.conf because it's the HDMI output to a TV/Monitor that I believe is the problem ? 

[http://tuxradar.com/content/modify-xorgconf-better-performance](http://tuxradar.com/content/modify-xorgconf-better-performance)

[https://wiki.ubuntu.com/X/Config/HDMI](https://wiki.ubuntu.com/X/Config/HDMI)

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

So first of all after a bit of reading Ubuntu/Lubuntu Etc. Versions 10 +  the xorg.conf is now found in /usr/share/X11/xorg.conf.d/xorg.conf

The tuxradar link above shows an example below...

Once you've found a modeline that works,

Section "Device"
        ...
        Option          "monitor-TMDS-1"    "MonitorTMDS1"
        Option          "IgnoreEDID"        "true"
EndSection

Section "Monitor"
        Identifier      "MonitorTMDS1"
        ...
        Modeline        "1920x1080@60hz"    148.352  1920 1960 2016 2200  1080 1082 1088 1125  +hsync +vsync
        Option          "IgnoreEDID"        "true"
        Option          "PreferredMode"     "1920x1080@60hz"
EndSection


I am trying to set up the xorg.conf with a Display of (1366x768) for Lubuntu 64Bit and that's where I need some help ?

From the above I installed the program below to help...

sudo apt-get install read-edid

Below is the output from $ xrandr

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 478mm x 268mm
   1366x768      59.79*+
   1920x1080     60.00    60.00    50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1368x768      60.02  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
```

Below is the output from $ xrandr --verbose

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x51
    Timestamp:  45771
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    load detection: 1 
        range: (0, 1)
HDMI-0 connected 1366x768+0+0 (0x54) normal (normal left inverted right x axis y axis) 478mm x 268mm
    Identifier: 0x52
    Timestamp:  45771
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0019c9000000000000
        00170103814627782a82e9a654479821
        1d4c5aa10800d1c03140454061408180
        010101010101632156b051001b304070
        3600de0c1100001e000000fd0016500e
        5b10000a202020202020000000fc0046
        554e41492054560a2020202000000000
        000000000000000000000000000001ea
        02031ff54c0203840507101112131416
        1f230907078301000065030c0020008c
        0ad08a20e02d10103e9600138e210000
        18011d00bc52d01e20b8285540c48e21
        00001e011d80d0721c1620102c2580c4
        8e2100009e8c0ad08a20e02d10103e96
        00c48e210000188c0ad090204031200c
        405500c48e2100001800000000000067
    audio: auto 
        supported: off, on, auto
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    dither: off 
        supported: off, on
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: off, on, auto
    coherent: 1 
        range: (0, 1)
  1366x768 (0x54) 85.470MHz +HSync +VSync *current +preferred
        h: width  1366 start 1430 end 1542 total 1798 skew    0 clock  47.54KHz
        v: height  768 start  771 end  777 total  795           clock  59.79Hz
  1920x1080 (0x55) 148.500MHz -HSync -VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x56) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x57) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x58) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080i (0x59) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0x5a) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080i (0x5b) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1280x1024 (0x5c) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1368x768 (0x5d) 85.885MHz -HSync +VSync
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock  47.71KHz
        v: height  768 start  769 end  772 total  795           clock  60.02Hz
  1280x720 (0x5e) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x5f) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x60) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1024x768 (0x61) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x62) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  720x576 (0x63) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x576i (0x64) 13.500MHz -HSync -VSync Interlace
        h: width   720 start  732 end  795 total  864 skew    0 clock  15.62KHz
        v: height  576 start  580 end  586 total  625           clock  50.00Hz
  720x480 (0x65) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x66) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  720x480i (0x67) 13.513MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock  15.75KHz
        v: height  480 start  488 end  494 total  525           clock  60.00Hz
  720x480i (0x68) 13.500MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock  15.73KHz
        v: height  480 start  488 end  494 total  525           clock  59.94Hz
  640x480 (0x69) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x6a) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  720x400 (0x6b) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
```

---

### Post by QIII on 2016-02-26
Bump.

---

### Post by A.R.B on 2016-02-28
Below is the kind of Feedback discussion I was hoping for :(

[http://arstechnica.com/civis/viewtopic.php?t=35478](http://arstechnica.com/civis/viewtopic.php?t=35478)

---

### Post by QIII on 2016-02-28
Compare the tenor of your first post (which required editing to bring it in line with the Ubuntu Forums rules) and the tenor of the opening post in that thread.  Do you perceive any difference that might account for the different reception of that request for support?

How do you expect that most of the volunteers here might react to the tone of your first post?

What about your subsequent posts?  I submit that a more polite tone might have served you well.

---

### Post by A.R.B on 2016-02-29
I rest my case Sir to the person I inform thee of my intentions in a legitimate way to bestow upon such persons an opinion bestowed within thy self!

---

### Post by QIII on 2016-02-29
There is no point in allowing this thread to consume any more of anyone's attention.

Closed.

---

