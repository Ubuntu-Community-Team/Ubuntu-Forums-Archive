---
title: "boot problem"
date: 2017-01-29
forum: General Help
---

### Post by dtree46 on 2017-01-29
PC is HP Envy, i7, 24gb, 500ssd, 16.04lts.
When booting, the HP logos appears then disappears so fast there is no time to press F10.
Can no longer set bios to allow booting form live CD.
How is this solved?

dlw

---

### Post by dtree46 on 2017-01-29
Not dual boot.

---

### Post by oldfred on 2017-01-29
Did you leave fast boot on in UEFI.
That setting assumes you have no changes to system hardware nor configuration, so UEFI immediately turns over boot to operating system. That does speed booting as most times you reboot, system has not changed.

Often you can get UEFI to go thru full start up checks with a cold (full power down) boot.
My desktop motherboard has settings for both warm reboot & cold boot on whether fast boot is on or off or even set a delay. Most laptops do not have all those settings.

You may be able to cold boot, by totally powering down, remove battery if laptop, hold power switch to drain all power for about 10 sec. 
Then boot and immediately press correct key(s) to get into UEFI for your system. Varies by brand, even some models within a brand.
If battery is not removeable like a tablet, you may have a tiny hardware reset on back of tablet somewhere. 
Some systems can only be reset by jumpering pins on motherboard.

---

### Post by dtree46 on 2017-01-29
Not dual boot.

---

### Post by dtree46 on 2017-01-29
Do not know about UEFI.

Turned off by holding power button 10 seconds plus, still no boot.

There are 3 jumpers on motherboard.
Use 1-2 resets cmos
Use 2-3 default.

Using 1-2, HP logo appears,  F9  nor F10 work.
Using 2-3 gives sane result except now error message, /dev/sda2: clean,24810/29712960 blocks with flashing cursor.
Can not enter anything.

---

### Post by oldfred on 2017-01-29
Are you also pressing escape?

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

The message you are getting is then that Ubuntu is booting, and did a quick check of file system.

---

### Post by dtree46 on 2017-01-29
Using ESC+F10 also does not work.
Now after the logo, a purple screen  comes on then quickly back to black with above error.
The person installing Ubuntu, removed W10 at my request.

---

### Post by oldfred on 2017-01-29
Need you to boot into Ubuntu's live installer and add Boot-Repair.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you do not have Ubuntu live installer, download flavor that matches your version.
       
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by efflandt on 2017-01-29
I have a low end (slow Pentium quad-core) HP Win10 laptop. To get into UEFI setup tap Esc once per second during boot until a menu comes up. From there you should be able to press F9 and select "ubuntu" if it was properly UEFI installed or F10 to get into UEFI/BIOS setup. I actually set UFEI for 5 second password delay to give me time to do that even though I have UEFI/BIOS password is NOT set.

With Win10 fast boot disabled I simply used Win10 Disk Management to shrink Win10 partition, then installed Ubuntu. Initially it booted grub, but something switched it to Win10 by default. So I have to do the tap Esc, press F9 thing to select "ubuntu". Not sure if something on your system is still trying to default to Windows (in EFI boot partition), but with Windows no longer on th drive, grub will not display a menu by default (purple screen may be a sign of that).

But I am not sure how to help you unless tapping Esc as soon as you start to boot gets you into a useful menu.

---

### Post by dtree46 on 2017-01-29
Pressing ESC every second or so while logo is visible doesn't work.
Nor does holding down ESC and F9 or  F10 every second or so.

---

### Post by dtree46 on 2017-01-29
Pressing ESC every second while logo visible does not work.
Pressing F9 or F10 every second while logo visible also does not work.
PC does not recognize live CD.

---

### Post by oldfred on 2017-01-30
Is then live DVD correctly installed as bootable.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download) 
[https://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](https://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

---

### Post by dtree46 on 2017-01-30
CD is bootable.
Just used it on another PC.

---

### Post by dtree46 on 2017-01-31
Solved.
Finally learned the correct way to enter the BIOS.

I thank everyone for their efforts.
They were very much appreciated.

dlw

---

