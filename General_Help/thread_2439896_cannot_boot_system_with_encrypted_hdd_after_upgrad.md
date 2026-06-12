---
title: "cannot boot system with encrypted hdd after upgrade"
date: 2020-04-02
forum: General Help
---

### Post by buzlite on 2020-04-02
Using lubuntu 19.10.
I have a system with an encrypted harddrive that was setup during the installation of lubuntu19.10
After an upgrade, lubuntu prompts for the passphrase for the encrypted drive. After providing it, lubuntu does not boot and directs me to initramfs or grub. During the boot process I found the following message at the console...

```
[ 0.840283] Initramfs unpack failed: Decoding failed
Volume group "luks" not found
Cannot process volume group luks
Volume group "luks" not found
Cannot process volume group luks
Volume group "luks" not found
Cannot process volume group luks
Gave up waiting for suspend/resume device
Volume group "luks" not found
Cannot process volume group luks
Gave up waiting for root file system device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
-Missing modules (cat /proc/modules;  ls /dev)
ALERT! /dev/mapper/luks-d91ba8d3-c39d-4cf0-a31a-2b65ac900e24 does not exist
BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

```

Any directions to fix this?
Thanks in advance

---

### Post by TheFu on 2020-04-03
Whenever using encryption, be 100% certain you have perfect backups and know how to restore them.  

Do you know the name of the encryption container from the prior install?  If so, you can mount it, get all the data off then work on setting up the current system as you like, with or without encryption, then finally move/copy all the data back as needed.

I have never attempted a system release upgrade with encryption involved though I've been using LUKS for over 5 yrs now. Some things are just too scary.

---

### Post by buzlite on 2020-04-03
Unfortunately, I don't know the encryption container name. I plan on installing lubuntu on a new flashdrive with the same user accounts and then use that to access the computer's encrypted drive. If I can read the encrypted drive, I plan on backing up the contents and then reinstall lubuntu on it. I've learnt my lesson and will not encrypt the drive again. I'll only encrypt a directory. Seems safer bet this way.
Thanks for the help.

> **TheFu said:**
> Whenever using encryption, be 100% certain you have perfect backups and know how to restore them.  

Do you know the name of the encryption container from the prior install?  If so, you can mount it, get all the data off then work on setting up the current system as you like, with or without encryption, then finally move/copy all the data back as needed.

I have never attempted a system release upgrade with encryption involved though I've been using LUKS for over 5 yrs now. Some things are just too scary.

---

### Post by TheFu on 2020-04-03
> **buzlite said:**
> Unfortunately, I don't know the encryption container name. I plan on installing lubuntu on a new flashdrive with the same user accounts and then use that to access the computer's encrypted drive. If I can read the encrypted drive, I plan on backing up the contents and then reinstall lubuntu on it. I've learnt my lesson and will not encrypt the drive again. I'll only encrypt a directory. Seems safer bet this way.
Thanks for the help.

LUKS doesn't care what the username is and having LVM LVs with the same name on different disks will cause issues too, so I wouldn't suggest installing anything to gain access.  I suppose you could manually rename the VG and LVs.  I've not done that, but there are commands for it.  Nothing with LVM is point-n-click, it is all commands.

Encrypted directories are a one-off solution since HOME directory encryption was deprecated (for a number of reasons).

I have accessed LUKS encrypted storage using a "Try Ubuntu" flash/install drive and using the file manager to gain access. Point-n-clicky.  I've done that with Ubuntu-mate.  Don't know if any other file managers have the encryption and LVM support needed or not.

For a fully manual way, let me search the forums here for instructions posted for others: 
[https://ubuntuforums.org/showthread.php?t=2368898](https://ubuntuforums.org/showthread.php?t=2368898)
[https://ubuntuforums.org/showthread.php?t=2312028](https://ubuntuforums.org/showthread.php?t=2312028) 
Hopefully, those will be helpful.
I don't have any Lubuntu 19.10, so things my have changed or not.

---

### Post by buzlite on 2020-04-04
Finally got this issue resolved.
I followed the instruction from [here]("https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk") to gain access the encrypted system harddrive and backed up the files. Then I reinstalled lubuntu (without disk encryption)
Thanks for the help.

---

### Post by ciamele on 2020-04-05
I see that the OP resolved his issue. I just recently experienced a similar problem, and used the instructions [here]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting") to resolve it. While I was in the live USB OS, I used Gparted to see the partition names.

---

