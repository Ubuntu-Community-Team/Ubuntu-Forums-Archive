---
title: "GRUB Bootloader Fix"
date: 2013-11-23
forum: General Help
---

### Post by KingJosiah on 2013-11-23
I dual boot the latest version of Ubuntu from an external hard drive. What I want, is for when I plug the external hard drive in, it gives me the choice of whether to boot Ubuntu or Windows, and when it's unplugged, to just boot Windows. Now, that works fine in theory. However, whenever I use my external hard drive to run Ubuntu, it breaks the Windows bootloader. I know how to fix that, I would like some help in configuring the GRUB bootloader so that it doesn't break my windows bootloader every time I try to use it.

---

### Post by jamesisin on 2013-11-23
Does this external HDD have two operating systems or is Windows installed internally and Ubuntu installed on the external?

---

### Post by KingJosiah on 2013-11-23
Windows is installed internally.

---

### Post by jamesisin on 2013-11-23
If your situation is Windows installed internally and Ubuntu installed on the USB drive I would not dual-boot.

Instead I would do a strait installation of Windows internally, then detach that drive and do a strait installation of Ubuntu on the USB (now attached) drive.

Then you simply adjust your BIOS settings to follow a boot order something like this:

[LIST=1]
[*]CD
[*]USB
[*]HDD (internal)
[/LIST]

Then if you boot with no USB drive attached, Windows boots.  If you attach the USB drive, Ubuntu boots.  Alternatively you can always pull up the BIOS boot menu and choose which to boot manually.

I see no reason to go through the added trouble of setting up a dual-boot in this situation when you get nothing additional from that extra work.

Is there a reason why you feel you *must* create a dual-boot system in this case?

---

### Post by oldfred on 2013-11-24
Did grub get installed to internal hard drive originally?
Grub remembers where to reinstall on major updates and you may need to reset that to make sure it reinstalls to external drive.

Check this line, and then run the dpkg update if not external drive, then recheck afterwards.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by KingJosiah on 2013-11-25
> **oldfred said:**
> Did grub get installed to internal hard drive originally?
Grub remembers where to reinstall on major updates and you may need to reset that to make sure it reinstalls to external drive.

Check this line, and then run the dpkg update if not external drive, then recheck afterwards.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

This solved my problem. Thank you!

The reason I want to dual-boot is because I also use that external hard drive for storage, and I'd rather not have to think about unplugging and plugging it back in when the right OS is on and stuff.

---

### Post by jamesisin on 2013-11-25
Then merely change the boot order in the BIOS.  Either way, glad you sorted it.

---

