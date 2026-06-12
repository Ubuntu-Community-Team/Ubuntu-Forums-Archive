---
title: "Restart results in black acreen new kernel 4.15.0-48"
date: 2019-04-25
forum: General Help
---

### Post by userxub-3498 on 2019-04-25
Updated two different machines to the 4.15.0-48 kernel tonight and both of them restart to a black screen. 4.15.0-47 caused black screen after sleep mode, 4.15.0-46 is glitchy after sleep but workable. 4.15.0-48 is useless - period. 
Is there some reason 18.04 users aren't getting the 4.20 kernel ?

---

### Post by kc1di on 2019-04-25
do you have a Nvidia graphic card by any chance?

I've had no problems here with 4.15.0-48.

---

### Post by Rubi1200 on 2019-04-25
What happens if you try this when booting?
[https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

If you get to the desktop then please install inxi if not already installed:

```
sudo apt-get install inxi
```

then run this and post the results:

```
inxi -GM
```

Thanks.

---

### Post by userxub-3498 on 2019-04-25
Thanks for the reply but no, Intel graphics in both machines.

---

### Post by userxub-3498 on 2019-04-25
Ok, thanks. I already trashed -48 but re-started with -46 and added the nomodeset to grub and while it did get stuck at "loading ram disk..." once started the previous glitch related to sleep mode was gone and the odd black screen during start was also gone. Installing inxi now.

---

### Post by userxub-3498 on 2019-04-25
Already had inxi. The report pasted below. 
-------------------------------------------------
$ inxi -GM
Machine:   Device: laptop System: Panasonic product: CF-W8EWEZZAM v: 001 serial: N/A
           Mobo: Panasonic model: CFW8W-1 v: 1 serial: N/A
           BIOS: American Megatrends v: V1.50L14 date: 06/05/2009
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev (unloaded: modesetting,vesa)
           Resolution: 1024x768@76.00hz
           OpenGL: renderer: llvmpipe (LLVM 7.0, 128 bits)
           version: 3.3 Mesa 18.2.8

---

### Post by userxub-3498 on 2019-04-25
Ok, -48 was still on my other machine (an old Fujistsu tablet connected to a 32" widescreen monitor) so I did the nomodeset edit to grub and Yes it did stop the black screen problem however it also forced the graphics into a default mode only so it won't ID the 32" monitor. After that I checked on the laptop and sure enough, it was also forced into a default graphics mode and would no longer ID external monitors. So for me this isn't a fix, both these machines are routinely connected to external displays.

---

### Post by userxub-3498 on 2019-04-25
So update: back to where I was an hour ago. One machine still running the -48 kernel and which must be hard restarted because restart results in a perpetual black screen. 
Second machine, running on -46, -48 purged but damage done as it's got new glitches it didn't before like a 30 second black screen immediately after the bios screen.

---

### Post by jeremy31 on 2019-04-25
In terminal run ```
cat /boot/grub/grub.cfg | nc termbin.com 9999
```
Post URL
Do you use encryption on the hard drive?

---

### Post by userxub-3498 on 2019-04-25
here's the link: [https://termbin.com/39d8](https://termbin.com/39d8)

I can copy it here if you prefer. Also, no encryption on HD. I also just purged -48 from the other machine and it's restarting ok again though it also has a delay it didn't before, only ~25 seconds on that one. On both it's a weird screen, not true black, more like muddy or blurry black. Never seen one like that before.

---

### Post by userxub-3498 on 2019-04-25
This bit caught my attention as it is the correct time delay. 
--------------------------------------------------------------------
```
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###
```

---

### Post by userxub-3498 on 2019-04-26
Today's update contained "Linux firmware for Kernel" and removed old headers for -47, -48. Hasn't made any discernible difference.  Back to the operational but glitchy -46 which 1. still has a 30 second black screen delay and 2. requires multiple tries to relaunch from sleep. But at least it works.

---

### Post by lou6 on 2019-04-27
No help here I'm afraid - only writing to commiserate.  I have nearly the same problem on a Dell e6420 running 18.04 with the exception that 4.15.0-47 works fine for me and is what I'm running now.  Purged 4.15.0-48 after following a few suggestions without any joy.

---

### Post by userxub-3498 on 2019-04-30
Thanks Lou, sorry to hear you had issues too. My only gripe with Linux is the total lack of transparency from developers et al. They release updates etc, people have issues and there's no way to know what if anything is being done to correct problems and what to expect. These graphics related bugs have been a problem for a long time and no one seems to be paying attention. For this OS to ever be mainstream they can't expect the general public to de-bug after every update.

---

### Post by lou6 on 2019-05-01
I concur with your statements RE:debugging - I had a similar experience last year on one of my other laptops with the 4.13 kernel.  It would absolutely not boot and I spent the better part of a day fixing grub to boot to a kernel I could use.  The only upside to this is that I'm becoming much more adept at debugging these problems...

---

### Post by bflat2 on 2019-05-01
That kernel may work. Tried the 'nomodeset' option at boot? For me it worked, definitely.

---

### Post by lou6 on 2019-05-02
For me 4.15.0-48 with 'nomodeset' killed access to my external monitor - as if it did not exist, no way to define/access external monitor from Display Manager (xubuntu).

---

### Post by userxub-3498 on 2019-05-03
Yes, the new kernels have video mode settings embedded to allow for hi-def splash etc (because that's what we need...) so nomodeset is meant to shut off those kernel settings during boot until x-server is running. In theory if all is well it won't effect video rendering after boot but obviously it does. The problem seems to be in the video driver which causes nomodeset to have other effects (like defaulting to single video option) not the other way round. 

My system has all the correct video drivers but still has an issue resulting in the following:
command: [COLOR=#242729][FONT=Consolas]lspci -k | grep -EA3 'VGA|3D|Display'
Report:
[/FONT][/COLOR] *-display:0               
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e1c0(size=8) memory:c0000-dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f04fffff

I have searched multiple forums and can't find a real solution yet. In fact it's truly disappointing to find many threads marked "solved" that only list ways to list your video info, what a joke. "Look at me, look at me, I figured out how to run a command to tell me blah blah blah".

---

### Post by userxub-3498 on 2019-05-03
Output from lspci -k | grep -EA3 'VGA|3D|Display' includes status on both the native (display:1) and VGA (display:0) monitors. I reset the VGA external monitor to primary and restarted. It was weird, part of desktop was on each screen but now lspci -k | grep -EA3 'VGA|3D|Display' output is totally different. 


00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Mobile 4 Series Chipset Integrated Graphics Controller
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Matsushita Electric Industrial Co., Ltd. Mobile 4 Series Chipset Integrated Graphics Controller
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
	Subsystem: Matsushita Electric Industrial Co., Ltd. 82567LM Gigabit Network Connection


and you can see the UNCLAIMED tag is gone. (Format is different too) I restarted again with the native monitor as primary and it's the same. I suppose changing the settings overwrote the config and possibly forced an update but that's just a guess. I still have some small issues, coming out of sleep mode still requires 2 tries, always. But I can live with it.

---

### Post by andres1gb on 2019-05-05
Same issue here in a machine running 32bits Xubuntu 18.04. After a system shutdown or a reboot, screen remains black until some graphics corruption happens. Next boot is always normal and I can use the laptop normally.

If I disable graphics boot in grub (GRUB_CMDLINE_LINUX_DEFAULT="text"), text mode shows a normal boot until this happens, not always at the same point. Switching back from 4.15.0-48 to 4.15.0-47 solves the issue at all.

Here is my machine (yes, an oldie, but still rocks with an SSD) and graphics card output, just in case it could be of help to someone:

```

Machine:   Device: laptop System: TOSHIBA product: TECRA A8 v: PTA83E-01E007SP serial: 66869740G
           Mobo: TOSHIBA model: Portable PC v: Version A0 serial: $$Y16670NU
           BIOS: TOSHIBA v: Version 3.50 date: 05/08/2007
CPU:       Dual core Intel T2400 (-MCP-) cache: 2048 KB
           clock speeds: max: 1830 MHz 1: 1243 MHz 2: 1267 MHz
Memory:    Used/Total: 1144.3/3268.9MB
           Array-1 capacity: 4 GB devices: 2 EC: None
           Device-1: DIMM 0 size: 2 GB speed: N/A type: DDR2
           Device-2: DIMM 1 size: 2 GB speed: N/A type: DDR2
Graphics:  Card: Intel Mobile 945GM/GMS 943/940GML Express Integrated Graphics Controller
           Display Server: X.Org 1.19.6 drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x800@60.00hz
           OpenGL: renderer: Mesa DRI Intel 945GM x86/MMX/SSE2 version: 1.4 Mesa 18.2.8
Network:   Card-1: Intel 82573L Gigabit Ethernet Controller driver: e1000e
           Card-2: Intel PRO/Wireless 3945ABG [Golan] Network Connection driver: iwl3945


```

---

### Post by userxub-3498 on 2019-05-05
Thanks Andre. Personally I prefer old gear, if only just to prove it's still viable. It's one of the reasons I switched to Linux and specifically why I use Xubuntu distro. That and a deep contempt for Miscrosoft and Mac. I see you have Intel graphics too. And not sure if I said in the OP both of my machines are also 32bit. They will both run 64 but it sucks up resources like sponge.

Are you able to run any diagnostics when it fails?

---

### Post by lou6 on 2019-05-05
My main system is also 32-bit - Dell 6420 8GB.  I received an update to 4.15.0-48 two days ago on my second machine (Dell 6430 32 bit) and accepted it with trepidation but it's booting normally.  Only difference I saw between this and the update to the main machine: the newest update was 4.15.0-48.51 and the previous one was 4.15.0-48.50 - also a difference in Dell models but I do not know the significance of the final 2 digits (50 to 51).

---

### Post by andres1gb on 2019-05-05
I haven't found evidence of the failure itself, I guess it excedes my skills. But I have found differences in the modules installed by this kernel and the previous one:

> andres@andres-TECRA-A8:/etc/modprobe.d$ ls /lib/modules/4.15.0-47-generic/kernel/
arch  block  crypto  drivers  fs  kernel  lib  mm  net  sound  ubuntu  virt
andres@andres-TECRA-A8:/etc/modprobe.d$ ls /lib/modules/4.15.0-48-generic/kernel/
arch  crypto  drivers  fs  lib  net  sound  ubuntu  virt



My best guess is that some specific driver is not available now and, therefore, some device is not properly initialized on boot. If trouble persists in upcoming versions, I'll try to investigate a bit more or to compile my own kernel.

---

### Post by userxub-3498 on 2019-05-06
Hey Lou, great to hear it's working for you. 48.50 vs 48.51 - the last four digits are release versions and I haven't found any info on what is different in these two but will check again later (have a project today and have to head out) I do know that the two Dells you have run different graphics chips and that is probably why one was ok and the other had issues. 

Andre, agreed - generally the problems are driver related and most reports I've seen point to video but I'm sure that's not the only source. I've also had issues with audio drivers in the past. Sounds like the best plan, find a kernel that works and keep it and or compile you own. Someone should create a db where you can enter your machine info and pick the best kernel.

---

### Post by lou6 on 2019-06-23
Well, 6 or 7 weeks have elapsed and my Dell e6420 (still running 4.15.0-47) has received no kernel upgrades while my e6430 has had several.  Have I painted myself into a corner of some kind here where I will not ever get an upgrade?  Just wondering...

---

### Post by userxub-3498 on 2019-06-24
Since back-dating to the older kernel neither of my machines have updated the kernel either. To be honest, they are both working well now so I haven't looked for a newer one but it seems the auto updates logged that it was manually changed and I haven't seen any included in the system updates or there simply hasn't been one but that's doubtful. I check all the listed updates now before downloading to be sure because I don't want a new kernel unless I know for sure it's ok. My bottom line is, unless there's some major breakthrough in a new kernel I'm happy with what I am using now. If you want to upgrade the dell you can always do it manually via the kernel database but definitely research what works (or doesn't) for that machine before doing so.

---

### Post by userxub-3498 on 2019-06-24
Oh, and I've been hearing rumors that they are no longer going to support 32bit after the current LTS release but haven't verified it yet. It would be a sad day for me as support for older architecture is one of the main reasons I switched to linux in the first place and I think many others as well. I guess they have forgotten who their original user base was.

---

### Post by cruzer001 on 2019-06-24
The dev's need to be made aware.  Sign up at Launchpad.  No need to leave any text reply (unless you want to) you can just check "affects me too".

[https://ubuntuforums.org/showthread.php?t=2415972&page=2&p=13866271#post13866271](https://ubuntuforums.org/showthread.php?t=2415972&page=2&p=13866271#post13866271)

---

### Post by deadflowr on 2019-06-24
> **userxub-3498 said:**
> Oh, and I've been hearing rumors that they are no longer going to support 32bit after the current LTS release but haven't verified it yet. It would be a sad day for me as support for older architecture is one of the main reasons I switched to linux in the first place and I think many others as well. I guess they have forgotten who their original user base was.

You can read and participate in the very heated discussions here:
[https://community.ubuntu.com/]("https://community.ubuntu.com/")

---

### Post by userxub-3498 on 2019-08-03
Wow. You could be on that discussion forever and not resolve anything. Seems I am also guilty of conflating my terms a bit so to clarify. I mentioned that I use and prefer older machines - mostly because I resent the whole "deliberate obsolescence" that drives hardware and software development - so one of the machines which I use daily is old enough to have a 32bit cpu. Another, the one I am using now, has 32/64bit capability but runs much quicker on 32. I am not a big gamer so to my knowledge don't have specific 32 bit only software that I "must have". My concerns are for CPU architecture not software (obviously given that one follows the other). Once the hammer drops on 32bit OS then every machine with a 32bit cpu out there becomes unsupported. I know the discussion is more complicated than just that, and few others care about old tech, but that is my personal bottom line.

---

