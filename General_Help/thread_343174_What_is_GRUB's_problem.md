---
title: "What is GRUB's problem?"
date: 2007-01-21
forum: General Help
---

### Post by max_croft on 2007-01-21
I've been having this issue for a while now, but now it's gotten worse.

I've got 3 hard disks:

/dev/hdd IDE2 Slave 40GB - The disk I install Ubuntu on
/dev/sda 320GB SATA - Windows XP
/dev/sdb 250GB SATA - Temp

In the days of Breezy Badger, I would install GRUB on /dev/hdd1 and under XP, use BOOTPART to create an entry in BOOT.INI so I could use NTLDR as my bootloader.

When selecting Linux from the NTLDR menu, GRUB would run briefly and then crash. I remember how I figure this out, but if I edited hd0,0 to hd1,0 Ubuntu would boot fine. Don't ask me why, but if I selected h1,0 when installing Ubuntu, then it would wipe the MBR of windows and I would lose NTLDR. So I had to install using hd0,0 and then manually edit the menu.lst to hd1,0 and everything would fine.

Since Dapper Drake and especially now with 6.10, I can't even get Ubuntu to boot and I blame GRUB.

Now when I use the same options and settings that I've used previously to install Ubuntu, I'm greeted with my two options of XP and Linux at the NTLDR menu, but when I select Linux, the screen flicks very quickly to GRUB and then dumps me back to the NTLDR menu.

I feel I could troubleshoot this problem much easier if I could understand EXACTLY what GRUB is referring to with it's hd0,0 and hd1,0 in relation to /dev/hdd1 or whatever. And more importantly, I'd like to know why Ubuntu boots (when it use to boot) from hd1,0 but if use that option during installation, it wipes my MBR on my XP disk.

I was always confused by this, but didn't really worry too much as it worked with a bit of tweaking. Now I can't boot Ubuntu at all and I don't know why.

The other thing I noticed was that if I used Exlpore2FS in XP, it would show my drive as /dev/hdc1 yet when I install Ubuntu, it shows as /dev/hdd. But I'm thinking that could just be a windows issue.

---

### Post by ajmorris on 2007-01-21
> **max_croft said:**
> I feel I could troubleshoot this problem much easier if I could understand EXACTLY what GRUB is referring to with it's hd0,0 and hd1,0 in relation to /dev/hdd1 or whatever

hd0,0 is /dev/hda1 (being the first hard disk and first partition on that disk))
hd1,0 is /dev/hdb1(being the second hard disk and first partition on that disk)

(Grub starts from 0, not 1)

Hope that helps a little bit. :)

---

### Post by diepruis on 2007-01-21
GRUB is also sometimes confused by the boot order in the BIOS, or by SATA drives. For example, on my PC, if I set root=hd(1,0) GRUB screams at me. But if I set it to root=hd(0,0) it's fine. It seems that when booting my SATA drive is hd0 and afterwards it is hd1.

You state that you have drives like sda, sdb, hdd. What are hda, hdb and hdc? If they aren't drives then that may be your problem.

The contents of /boot/grub/device.map might shed some light on your problem.

---

### Post by max_croft on 2007-01-21
Thanks for the replies guys!

device.map shows me this

(hd0) /dev/hdd
(hd1) /dev/sda
(hd2) /dev/sdb

There are no other hard drives in my system. I suspect the 40GB is being read as hdd because it's running on the second IDE port from the motherboard and the hard disk is connected at the end of the IDE cable marking it as slave probably because I've got the disk set to cable select, but I can fix that.

Only, how come this hasn't affected it in the past?

I'll make the adjustments now and reinstall Ubuntu and I'll see what happens.

So judging from the device.map, should I then go with the default setting of GRUB wanting to be installed to hd0 or is that going to wipe the MBR on my XP disk again?

---

### Post by max_croft on 2007-01-21
> **diepruis said:**
> GRUB is also sometimes confused by the boot order in the BIOS, or by SATA drives. For example, on my PC, if I set root=hd(1,0) GRUB screams at me. But if I set it to root=hd(0,0) it's fine. It seems that when booting my SATA drive is hd0 and afterwards it is hd1.

That seems similar to the issue I have when installing GRUB. It tells me that /dev/hdd is hd0,0. But after the install and boot, it tells me that no images can be found. I edit the boot to  hd1,0 and it's fine. But if I install GRUB as hd1,0 I lose my MBR on my XP drive. 

Grrrr.. Why does GRUB hate me? :p

---

### Post by randiroo76073 on 2007-01-21
Altho this is win 98 entry, does your win entry look similar, ie:  is there a "chainloader" entry?

title          Windoz 98me at hda1
root           (hd0,0)
makeactive
chainloader    +1

w/o the chainloader it will mess everything up.

---

### Post by max_croft on 2007-01-21
Having now made the 40GB drive a master on the second IDE channel, it is now read as /dev/hdc

When installing Ubuntu, on step 6 of 6 where is says "GRUB will be installed on" and by default it shows (hd0), I've changed that to /dev/hdc1 and I'll see how it goes.

I'm installing it right now, so once it's installed, I'll have a look straight away to see if I have something like what you've got for your Windows 98 section.

---

### Post by max_croft on 2007-01-21
YAY! I'm booting again -- looks like 6.10 doesn't like booting from a slave drive.

This is what's in my menu.lst for the chainloader --

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I've got a feeling that those two map strings have something to do with the fact that I have to install GRUB to /dev/hdc1 instead of just leaving it to install on (hd0) which is what causes my MBR to be wiped.

To make things more confusing, the device.map reads like this:

(hd0)	/dev/hdc
(hd1)	/dev/sda
(hd2)	/dev/sdb

In the menu.lst, the boot details show this:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

But Ubuntu will not boot unless I change root (hd0,0) to (hd2,0) 

Can anyone clear that up for me because the more I think about it, the more it hurts my head.

---

### Post by randiroo76073 on 2007-01-21
Now your giving me a headache too, LOL!  Do a Google search on "Grub bootloader" and start reading is the only answer I have.  Might try "menu.lst" too

---

