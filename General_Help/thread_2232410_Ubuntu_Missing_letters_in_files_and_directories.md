---
title: "Ubuntu: Missing letters in files and directories"
date: 2014-07-01
forum: General Help
---

### Post by justtryit on 2014-07-01
Relatively new with Ubuntu.  Would appreciate any thoughts, or links, which anyone else might care to share, toward solution of some display problems I am having.

Thanks!

Running Ubuntu 14.04 64 bit... Getting weird GUI text effects (e.g.: as in below screenshot - note no lowercase b appears anywhere on display) after system stumbles (on high use(?), with multiple screens open, screen grays out, then comes back to bright)

Was fresh installation, runs mostly okay, but still having some intermittant video challenges with 14.04 (e.g.: diagonal white lines) using nvidia driver, which seems to cure with ctl-alt-F1 and ctl-alt-F77.  Not sure if the two problems are at all related or not. 

14.04 Ubuntu LTS 64bit on m7664x (Athlon64x2) 8gb RAM, w/on board nvidia 6150 LE, running into HP-L1710 display

justtryit@m7664x:~$ lspci | grep -i vga
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)



[IMG]http://www.seadogbytes.com/misc/Screenshot.jpg[/IMG]

---

### Post by r_avital on 2014-07-01
Hi and welcome,

First, where is that screenshot from, I mean what application?  It's obviously a directory listing, just curious to see if this would happen in any other application, when it happens.  If it's a directory listing, can you do the same directory listing in a terminal?  Hit Ctrl+Alt_l (lower-case L), it should open a terminal window, and enter this at the prompt: ls -l

Do you get the same files listed?  Is the problem still showing up in the terminal window?

Second, make up a file with some random text with a bunch of "b" characters in spots where you would expect to find them, and keep that file open in some editor (like gedit).  When the screen darkens and comes back, does the same problem happen with the text in the editor?

When the screen of an application darkens momentarily and comes back to normal brightness level, it usually means that application is busy getting data updated, getting refreshed.  It's happened to me, and it may not happen if you have one graphics card vs. another, but it's usually an indication that something is slowing down the transfer of data to that screen.  Do your disks spin a lot when that screen is dark?

---

### Post by grahammechanical on 2014-07-01
"screens?" Or application windows? The greying of an application window is the way the OS tells us the application is busy. It does not mean not enough RAM or the CPU running at 100% or anything like that.

How much of its own memory does that graphic card have? You could try using a different video driver. System Settings>Software and Updates>Additional Drivers tab.

Regards.

---

### Post by justtryit on 2014-07-02
Thank you for responding, grahammechanical...

1. Yes, I think I must mean 'application windows', 

2. RE:  "It does not mean not enough RAM or the CPU running at 100% or anything like that."
... yes I guess I WAS beginning to worry that either the processor, or the 8GB of RAM was not going to be enough to run Ubuntu 14.04 well.  Great if that is not going to be the case.  Thank you.

3. Yes I have been struggling with the video driver selection.  The 304.121 seems to run with the fewest problems of the ones I tried (...the 173, two other '304' versions and the non-proprietary default one), but even the 304.121 gives me those diagonal white dashes at bootup.  IIRC, the 173 one had some sort of kernal conflict, and just gave me a black screen with a blinking white cursor at upper left.)

4. The 6150LE graphics are on the mobo.  ...'dxdiag' (run under winxp) says 256MB
...under Ubuntu, it says the following:

justtryit@m7664x:~$ lspci -v -s 00:05.0
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 2a34
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at f8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

...If that's not enough video memory, does it appear that this machine might be likely work better with one of the less-demanding Ubuntu 'flavors'?  I have only tried Ubuntu 12.04 and Ubuntu 14.04 thus far.  My goal, of course, is to find a replacement for both winXPMCE and Win7pro, so I can go forward, and leave them behind.

Thank you for your kind assistance.

---

### Post by justtryit on 2014-07-02
Thank you for your comments r_avital...
1.  The screenshot is a portion of the listing from the default program (is that nautilus?) under the file cabinet icon on the left side of the main Ubuntu desktop.  I have not tried going to terminal when the problem happens, but I did notice that the missing letters seemed to be manifesting themselves everywhere in GUI mode, on the tops of all of other windows, and even in the top bar, like "Firefox We  Browser", etc.  IIRC, it was also happening within (Thunderbird) email messages on the screen at the time.  I'll have to try a few more things, as you suggest, when the problem happens again.

2. RE:  "it usually means that application is busy getting data updated,"
...The drives do not seem to noticably be churning more than usual.  The Ubuntu partitions are on a fairly new 320GB WD Blue, so maybe it's quieter than it might otherwise be.  Actually I am not sure why I would be getting these gray-out slowdowns...
...I ran this machine for six or seven years with 32bit winXPmce and only 4GB of RAM, with fewer performance hangups.  I am running now with 64bit Ubuntu 14.04, with 8GB RAM, and was actually hoping for a performance bump over what I saw with winXP, but I have not seen it so far.

Thanks again for your help and suggestions.

---

### Post by r_avital on 2014-07-03
justtryit,

I truly hate receiving answers that take the easy way out and blame the hardware, so I hate giving such answers myself.  So apologies in advance, but if the PC is six or seven years old, and the video hardware is just as old, there might be an issue there.  A long time ago I had a bad video card under Win2k that was throwing characters outside of a window's frame and other weird behavior like missing characters.  I'm not saying that's the problem, but it would help if you could test the same version of Ubuntu on another system.

For less demanding versions of Ubuntu, you might want to go to something pre-Unity, like 10.10 or even 10.04 (the latter being an LTS release).  But again, I would only suggest that for testing on your system, not for regular use.  For more current flavors of Ubuntu, with less intense demands on video, you might want to try the latest LinuxMint version (Mint is based on Ubuntu), and a plain-vanilla one, without the cinnamon window manager.

I'm sorry I don't have better answers, but consider that if this is your first experience with Linux in general, picking a "flavor" or distribution that works for you, is usually a process of testing several different ones until you find your "bull's eye" target.

It used to be true, that you could install practically any Linux on old hardware and "bring it back to life" so to speak, and it's still true with many distros, I'm not so sure it's still true with Ubuntu though.

---

### Post by justtryit on 2014-07-04
RE:  :...if the PC is six or seven years old, and the video hardware is just as old, there might be an issue there."

Thanks for you response, r_avital...
...and thanks for the chuckle.  Used to be, back in the old days, Dad got the new one, and the kids got the hand-me-downs.  Not so much now.  Last computer I bought had an intel i3 processor... but I bought it for my daughter!  As you correctly noted, THIS one isn't 'quite' that new.

I am still running 12.04 on my (similar-vintage) laptop, and not having either of these graphics issues. ...Perhaps I just jumped the gun a little on the 14.04 upgrade to this machine.

---

### Post by lunalui on 2014-10-14
Hi, 
I'm experiencing a similar problem on ubuntu 14.04 (32 bit): sometimes some letters disappear from the titles in the window bars and in menus. The problem is fixed by restarting the computer. It seems to happen whenever I switch on/off manually the wifi connection before logging in. My laptop (a vaio) is 3 years old. On the other hand, if I type in a terminal (all) letters are fine....

---

### Post by emanuil-tolev on 2015-05-21
Sorry for necroing the thread, but it's the first result for "ubuntu letters missing from UI" which is the first thing I thought to search for when I experienced this problem on a Lenovo Thinkpad T450s, Ubuntu 14.04.2 x64.

The problem is that this computer has a nice screen - a bit too nice, as its high 1080p resolution made the default font sizes physically too small and thus unredable.

I had previously used unity-tweak-tool to adjust the text scaling to 1.15 from 1.00. There are many way to alter this setting in Gnome / Unity. Adjusting the scaling to 1.10 or 1.20 fixed the issue for me - it looks like half the letters just don't scale properly on the scaling settings ending in 0.05.

---

### Post by dino99 on 2015-05-21
some tests should be made with different themes (adwaita, ambiance, ...) using ubuntu-tweak > Appearance

---

### Post by justtryit on 2015-06-05
> **justtryit said:**
> RE:  :...if the PC is six or seven years old, and the video hardware is just as old, there might be an issue there."

Thanks for you response, r_avital...
...and thanks for the chuckle.  Used to be, back in the old days, Dad got the new one, and the kids got the hand-me-downs.  Not so much now.  Last computer I bought had an intel i3 processor... but I bought it for my daughter!  As you correctly noted, THIS one isn't 'quite' that new.

I am still running 12.04 on my (similar-vintage) laptop, and not having either of these graphics issues. ...Perhaps I just jumped the gun a little on the 14.04 upgrade to this machine.

UPDATE:  Purged nvidia* drivers, then reinstalled (reverted) to the Nvidia 173 driver on this machine, which seemed to mostly cure the missing characters problems and lessen the frequency of, although sadly not eliminate, the freezes/lockups.

justtryit@m7664x:~$ inxi -b
System:    Host: m7664x Kernel: 3.13.0-53-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: HP Pavilion 061 product: RN650AA-ABA m7664x version: 0nx1114RE101NODM300
           Mobo: ASUSTek model: NODUSM3 version: 1.05 Bios: Phoenix version: 3.10 date: 12/13/2006
CPU:       Dual core AMD Athlon 64 X2 4200+ (-MCP-) clocked at 1000.00 MHz 
Graphics:  Card: NVIDIA C51 [GeForce 6150 LE] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1280x1024@50.0hz 
           GLX Renderer: GeForce 6150 LE/PCI/SSE2 GLX Version: 2.1.2 NVIDIA 173.14.39
Network:   Card: NVIDIA MCP51 Ethernet Controller driver: forcedeth 
Drives:    HDD Total Size: 640.1GB (23.1% used)
Info:      Processes: 187 Uptime: 14:07 Memory: 1742.4/7920.8MB Client: Shell (bash) inxi: 1.9.17

---

### Post by mörgæs on 2015-06-07
How does a live boot of X/Lubuntu behave?

---

### Post by ElX on 2015-06-08
I see this too with Ubuntu desktop 64 14.04.02 on a very new Dell Inspiron with a very high resolution screen, in fact, that's one of those Windows touchscreens.
The letters are missing in labels to icons on the desktop, in system preferences, and other similar places with system font scaled according to the resolution.
It seems the problem is combination of poor drivers (and I would not expect fixes soon) and unusually high resolution, which was not properly tested.
So, my first hunch will be to try "zoom" in accessibility options of Compizconfig Settingsmanager, which is what I will try in the evening.
[http://askubuntu.com/questions/82398/how-to-zoom-inzoom-out](http://askubuntu.com/questions/82398/how-to-zoom-inzoom-out)

---

### Post by mörgæs on 2015-06-08
I should have been more clear in my previous post. I meant: How does a live boot of X/Lubuntu 15.04 behave?

---

### Post by ElX on 2015-06-09
Sorry, cannot try 15.04 now. However, live 14.04.02 boot was fixed a moment ago with the command:
gsettings set org.gnome.desktop.interface font-name 'Ubuntu 10'Generally, it's well known that size 11 is tough in many cases, seems like in this one it was too tough. Hope it will be useful to someone.

---

