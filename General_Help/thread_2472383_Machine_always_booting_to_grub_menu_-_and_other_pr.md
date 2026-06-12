---
title: "Machine always booting to grub menu - and other problems"
date: 2022-02-25
forum: General Help
---

### Post by josephmmorgan on 2022-02-25
Dell Precision 7730
Intel Hexa-Core i9
64GB Ram
2 nvme 500GB SSD
Ubuntu 20.04.03
Bare-Metal Ubuntu *** NO DUAL BOOT - NEVER HAD WINDOWS ON IT ***
Grub Version:  2.04-1ubuntu26.13

I recently had to rebuild my Ubuntu, and freshly installed 20.04.03.   Once running, all is generally fine, though it seems noticeably slower than the 20.04 before it. 
One really bothersome thing is the machine *always* boots into the GRUB menu.   My BIOS only sees Ubuntu in boot order.  

When the menu displays, Ubuntu is listed as the first OS, and it says it should auto start after 10 seconds.   If I hit Enter, it boots up just fine.  Yet, if I wait more than 10 seconds, I can't do anything other than power it down.  After 10 seconds, the keyboard is dead.   Pressing Enter doesn't work, I can't use any arrow keys, ESC doesn't work.  Only the power button works at that point.
 
So, I'm thinking I must have something missing (or misunderstood in my grub.cfg).   These are the only un-commented lines in the grub.cfg file:

```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

What am I *not* seeing here?

---

### Post by TheFu on 2022-02-25
Once you are in the working, booted, OS, runs **sudo update-grub**.
That will search all devices for OSes that grub knows how to boot.

Is there any chance that **any** storage devices in the computer were cloned?  If they have the same GUID or UUIDs, that will cause boot problems, since to the OS, both seem like the same disk. When I've done this, the booted device/partition would swap from time to time - making me very confused until I realized the issue.

---

### Post by josephmmorgan on 2022-02-25
Not cloned as far as I know.  There are 2 512GB SSDs, each with its own UUID.    Only the boot drive was reformatted on the rebuilt.  The other remained untouched.  Is there a command to run to see what boot OS's grub sees without actually rebooting?

---

### Post by TheFu on 2022-02-25
There is a menu. It has moved around, so it is release dependent and I don't know where it is. I'd look under /boot/grub/ lacking any other information. I see a menu.lst file there.

This is rebuilt by the update-grub command, so don't modify it in that location, if that is the same location on your system.

Formatting doesn't change the disk GUID.

BTW, I don't use UEFI, so I don't know how the boot menu for that works.

---

### Post by grahammechanical on 2022-02-25
It is my understanding that menu.lst was used with Grub version 1 (legacy). Grub version 2 uses grub.cfg. 

According to the Grub 2 manual GRUB_DEFAULT=0 means boot the first entry in the menu; GRUB_TIMEOUT_STYLE=hidden means before displaying the menu wait for the timeout set by GRUB_TIMEOUT and GRUB_TIMEOUT=0 means boot the default entry immediately without displaying the menu.

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

I suggest that at the Grub menu you select advanced options for Ubuntu and see how many kernels are listed there. Each kernel should have a duplicate with recovery mode. That is normal. See if you have duplicate entries other than the recovery mode entries. I see no reason why you are seeing a Grub menu and why it has a timeout greater that zero seconds.

Regards

---

### Post by oldfred on 2022-02-25
UEFI or BIOS installs?

If UEFI, your UEFI uses partUUID (GUID) to know which ESP - efi system partition (FAT32) to boot from.
Then in ESP is a  3 line grub.cfg that uses a configfile to know which grub.cfg install to load. It will have an UUID of that install.

If BIOS, the part of grub in the MBR and hidden core.img in sectors after MBR, determine which system  it will load. 

If you want to document all the details you can run the Boot-Repair report. I periodically run report & copy into /home folder so backed up with my normal backup. Then I have documented lots of details on all my installs.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by josephmmorgan on 2022-02-25
Well.  This is strange.   I'll have to keep an eye on it, but, just for fun, I ran:

[B]sudo update-grub

[/B]And rebooted, and now grub doesn't show.  I now wish I had taken a backup of /boot/grub/grub.cfg so I could compare.

---

