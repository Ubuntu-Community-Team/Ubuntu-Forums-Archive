---
title: "Ubuntu Dissapeared from BIOS Boot Order"
date: 2016-01-02
forum: General Help
---

### Post by mulluysavage on 2016-01-02
After opening up my laptop for structural repair, boots straight into Windows. Booting up into BIOS menu, first option lists "HDD:" when I believe it used to be "Ubuntu". Second option is Windows. 

I had opened up the case and put it back together, booted into Ubuntu fine. Had to go back in to re-connect speakers. ACER v-151 i7 w/UEFI BIOS, Have a dual-boot setup that I installed myself on an SSD. Ubuntu 14.04

---

### Post by grahammechanical on 2016-01-02
Has the UEFI boot system been reset to manufacturer's defaults? You may get help by running Boot Repair from a Live session.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When we select to create a BootInfo summary we get a URL to where the report is temporarily stored online. Paste the URL link in this thread and then we can access it as well.

Regards.

---

### Post by mulluysavage on 2016-01-07
I made a USB boot drive from a Sony 2GB stick, which doesn't boot. I've never once been able to boot any machine from a usb flash drive. I've tried several times over the years, is this a wonky process?

---

### Post by Bucky Ball on 2016-01-07
Nothing wonky about it. You made a boot USB? Of what and how? 

Pressing F12 at boot takes you to a boot device option screen on many machines. Oddly, my machine has never reacted to changes of boot order in the BIOS, only when I select a boot device from the F12 boot device list.

Check the manual for the motherboard to see if your is F12 or something else.

---

### Post by mulluysavage on 2016-01-08
I made a boot usb stick of Boot Repair using Unetbootin.

I made a boot usb stick of Boot Repair using Unetbootin. I made sure the boot order had HDD: Sony 2GB blah blah blah (the name of my usb stick) priority before my HDD. I see the led on it flash on boot, but then *Windows* boots (omfg)

I looked at it with Gparted, and it has a boot flag...

---

### Post by oldfred on 2016-01-08
Many UEFI especially if secure boot is on do not default to allow USB boot. You may have a setting in UEFI to allow that.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by mulluysavage on 2016-01-08
Booting to legacy bios made a difference. Now I get the following errors :

PXE-E61: Media test failure, check cable 
PXE-M0F: exiting PXE ROM
Missing Operating System

Tried Linux Live Installer, and was able to boot  Boot Repair Disk from USB drive. However, got the message:

The boot of your PC is in Legacy mode. Please change it to EFI mode. Please use Boot-Disk-64 bit which contains an EFI-compatible version of this software (use it from live USB, not CD)

Seems to be a catch-22 if I can't boot up to a USB in UEFI secure mode. I can't seem to  turn secure mode of in UEFI from my bios, nor can I move the USB up from last priority in the boot order. Yes it's an ACER machine. V-171.

Any other solutions for recovering my dual boot?

Actually, looks like I was in fact using Boot Repair Disk 64-bit

---

### Post by Bucky Ball on 2016-01-08
It really helps if you just post the link to your bootinfo produced by Boot Repair so we can see the whole thing rather than providing selected excerpts. :)

---

### Post by mulluysavage on 2016-01-09
I don't think it ran,  I think that's the output. That's the whole message.

---

### Post by oldfred on 2016-01-09
That sounds more like you just loaded Boot-Repair.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Acer after install requires you to set supervisory password & set trust on Ubuntu/grub efi files.
You may need that or some other setting in UEFI changed.
      
 Very latest UEFI/BIOS works, downgrade not required:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
[/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)

[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

### Post by mulluysavage on 2016-01-11
Ok I see. Here's my boot-info link.

[http://paste2.org/tvc2Wdkp](http://paste2.org/tvc2Wdkp)

I can change my EFI option to disable secure boot, but not change the boot order so that USB is priority over HDD.

---

### Post by oldfred on 2016-01-11
Did you set the supervisory password?
And enable trust on the efi boot files in the ESP? As shown in several of the links?
You should also boot flash drive in UEFI mode, not BIOS/CSM/Legacy boot mode.

You also are showing 14.04.2? It is at .3 with many improvements that may help a new computer work better.

---

