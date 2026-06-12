---
title: "Ubuntu Hangs at bootup"
date: 2007-10-14
forum: General Help
---

### Post by rkillcrazy on 2007-10-14
I just built a new PC.  Specs are below...

MOBO = Asus M2N-SLI Deluxe
Video = Asus EN7600GS Silent (PCIE)
CPU = AMD Athlon 64 X2 6000+ (~3.0 GHz)
RAM = 2GB RAM (dual-channel kit)
HDD = Two 150GB Western Digital Raptors set up in a RAID-0 in the BIOS

Issue:
Windows Vista 64 loaded fine and I downloaded/ran Wubi-7.04.04.  It pulled down the ISO just fine, rebooted and ran the setup.  Upon reboot, it gets to the Ubuntu logo screen with the progress bar.  If anyone has ever looked at the progress bar, they'd notice it is broken into little segments.  Well, it doesn't even fill the first segment completely.  At this point, it hangs.

Any ideas?

10-14-07
1043 EDT

---

### Post by Tiggums on 2007-10-14
Mine does the exact same thing.  It worked for several days, but lately it would just start to load, but not finish that first bar, I was able to get past it by booting windows and restarting it, so I figured that Wubi had a problem with rebooting improperly, maybe it wouldn't allow it to start up without Windows having been properly restarted... Now nothing will work for it.  I have Ubuntu 7.04, have been installing updates, but other than that I have not changed anything.

---

### Post by Wall86 on 2007-10-14
I had the same issue, I could not find a solution. If you run ubuntu on live CD you will notice that it will not see your SDA's as a Raid but as seperate SCSi devices, there are some guides aroudn for setting up ubuntu onto Fake hardware RAID's, but nothing for wubi yet. 

I ended up just breaking my array, and installaing Kubuntu onto one my Barracuda's

---

### Post by Tiggums on 2007-10-14
Yeah mine says no raid disks detected or something like that, but I only have one hard drive, and just used wubi... go figure...

---

### Post by Megatog615 on 2007-10-14
Same with me, but it hangs after "No RAID disks." Eventually it drops to a busybox terminal. I can't even get to the installer.

---

### Post by ago on 2007-10-15
Press Alt+F1 to see where it hangs (before it hangs) or better, edit menu.lst and take away "quiet spalsh" to get a verbose booting process.  If the latest line complains about ACPI, try to put acpi=off in your menu.lst (and possibly submit a ubuntu bug rebort).

---

### Post by rkillcrazy on 2007-10-15
> **ago said:**
> Press Alt+F1 to see where it hangs (before it hangs) or better, edit menu.lst and take away "quiet spalsh" to get a verbose booting process.  If the latest line complains about ACPI, try to put acpi=off in your menu.lst (and possibly submit a ubuntu bug rebort).

Ago, I'll try that when I get home tonight...

Everyone,
I just found it strange that it got through setup just fine with the RAID array but wouldn't boot.  NVIDIA stuff is normally pretty good with Ubuntu so I couldn't imagine why it wouldn't work.

10-15-07
0845 EDT

---

### Post by Tiggums on 2007-10-15
I tried starting without the quiet splash but it hangs at the waiting for root system part....

---

### Post by ago on 2007-10-15
Do you all use raid, some raid might not be well received, particularly software raids (=managed on the windows side)

---

### Post by Tiggums on 2007-10-15
I only have 1 hard drive, so I don't think it uses raid? Idk for sure because I'm rather uneducated with hard drives...

---

### Post by ago on 2007-10-15
Wait 5 minutes you should get a prompt, then you can look at /tmp/lupin.log

---

### Post by rkillcrazy on 2007-10-15
> **ago said:**
> Do you all use raid, some raid might not be well received, particularly software raids (=managed on the windows side)

I use RAID-0.  It's a hardware RAID (set in BIOS) not a software RAID (set in Windows).

10-15-07
1013 EDT

---

### Post by Tiggums on 2007-10-15
After reading another forum that you commented in, I did force restart a few times, so I'm guessing I might have corrupted my file system... Idk exactly how to go about fixing it... I have downloaded the ubuntustudio file, but it doesn't work either, same thing happening wrong.  It always hangs on the waiting for root system, and nothing happens, thanks for the help...

---

### Post by ago on 2007-10-15
Get a bootable CD with chkdsk (windows official CD or some of the rescue CD you find) then run it with chkdsk /r

---

### Post by rkillcrazy on 2007-10-15
> **ago said:**
> Press Alt+F1 to see where it hangs (before it hangs) or better, edit menu.lst and take away "quiet spalsh" to get a verbose booting process.  If the latest line complains about ACPI, try to put acpi=off in your menu.lst (and possibly submit a ubuntu bug rebort).

OK, I hit ALT+F1 and got the following:

```

Loading, please wait...
[11.604000] Buffer I/O error on device sda1, logical block 73261040
	Check root=bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! /media/host/wubi/install/install.virtual.disk does not exist. Drpping to
a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

Does that help anyone out?

10-15-07
1708

---

### Post by SLK on 2007-10-16
I have similar problem after installing FF where booting into Ubuntu doesn't proceed and stops at "waiting for root system..." and after few minutes I get the "BusyBox" message...I'll try ALT-F1 when I get home and give more info here...

Cheers,
SLK

---

### Post by ago on 2007-10-16
Post here /tmp/zenigata.log /tmp/lupin.log

---

### Post by Tiggums on 2007-10-16
Didn't know if you wanted mine, but here they are anyways...

---

### Post by rkillcrazy on 2007-10-16
> **ago said:**
> Post here /tmp/zenigata.log /tmp/lupin.log

Likewise...I didn't know if you wanted mine but here they are.  I didn't see a \tmp\ folder but I found them in \logs\.

10-16-07
1105 EDT

---

### Post by Tiggums on 2007-10-17
So do you think I'd be better off uninstalling wubi, then reinstalling?

---

### Post by ago on 2007-10-17
rkillcrazy logs look good, Tiggums do not. But at this stage I won't have much time to debug 7.04. Your best shot is to wait for 7.10

---

### Post by Tiggums on 2007-10-17
Ok, I'll just download 7.1 tomorrow, thanks for all the help...

---

### Post by ago on 2007-10-17
Better wait for ubuntu-final at this point... The RC url is already down...

---

### Post by akb on 2007-10-18
I did not read the whole thread, but since I got stuck several times at the progress bar (same position) too, try these tips:

a) append "noapic" as a kernel parameter

b) unplug usb mediums when booting with wubi, as these can rearrange your hdd mappings

---

