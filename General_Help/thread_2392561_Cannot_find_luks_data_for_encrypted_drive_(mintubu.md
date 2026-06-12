---
title: "Cannot find luks data for encrypted drive (mint/ubuntu)"
date: 2018-05-22
forum: General Help
---

### Post by XwizCarl on 2018-05-22
I have an encrypted volume that I can no longer access. I have the password but am unable to get to a state where I can input it.
Grub provides me access to boot normally or in recovery mode. Neither of these work; however in recovery mode I get to initramfs/ busybox
typing exit<enter>
yields "Check cryptopts=source= bootarg: cat /proc/cmdline or missing modules, devices: cat /proc/modules; ls /dev
-r ALERT! /dev/disk/by-uuid/... does not exist. Dropping to a shell!

from fdisk -l if found the following:

/dev/sda1  boot  linux
/dev/sda2          extended
/dev/sda5          linux

Using live media I tried:
sudo cryptsetup luksOpen /dev/sda5 'Partition 5" (or /sda2 'Partition 2') gives:
Device: /dev/sda5 is not a valid LUKS device.

I believe sda5 is the volume I should be working on, but I tried this on sda2 as well with the same result.

my boot loader data is located below:
[https://paste.ubuntu.com/p/c6TcY4KS7F/](https://paste.ubuntu.com/p/c6TcY4KS7F/)

From the hexdump info it almost looks as though the luks data header was damaged or overwritten for sda5, but I obviously don't know what I am doing.

Any help would be appreciated. Cheers!

---

### Post by TheFu on 2018-05-22
I'd guess that something was corrupted somewhere, somehow. At this point, I'd start by checking all the hardware using every tool I know.  Disk controller, cables, HDDs, and look for errors in log files.  I'd also get the SMART data from the drive. If over 10 sectors are relocated, swap the drive immediately and only use the old disk for unimportant things.
I'd also have my last backup from before the issue happened ready.  With encryption, there really isn't any data recovery when there are logical data issues.  The data is gone if you don't have a backup and can't gain access to it using the normal boot-from-flash media, setup chroot, load cryptsetup + unlock the LUKS volume + lvm stuff then chroot.  I expect if you did get the chroot working, then you wouldn't be here.  Let me find my notes about that ... 
```
# How-to mount old C720 Luks encrypted storage
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# lsblk
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
# sudo cryptsetup luksOpen /dev/sdf5 c720
# sudo vgchange -ay
# sudo mkdir /mnt/root /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-root /mnt/root
or
# sudo mount /dev/c720--vg/lv--Stuff /mnt/Stuff
# sudo mount /dev/c720--vg/root /mnt/root

```

**lsblk** will show the layout of a disk ... disk-partitions-encryption-logical volumes   IFF there aren't issues.

You might need to install lvm2 or crypt-stuff as needed. I don't recall. 

I had an SSD fail in Feb on my laptop with FDE.  About once a month for the last year, it was going read-only, which caused lockups.  A reboot made it work again. I've had backup religion for a very long time, so kept using it.  When it finally did fail, I had denial for a few hours and tried to fix it. Since it wouldn't boot, that didn't last long.  Booted off a flash drive and couldn't access any of the partitions at all. It was dead Jim (McCoy's voice).  So then I had to move some storage around because only a 44mm M.2 SSD fits inside the laptop.  Dropped in a 64G SSD, loaded a fresh Ubuntu-Mate using FDE, restored the things from my backups as needed; data, /home, lists of installed programs, and a few /etc/ settings that I'd tweaked over the last few years.  Basically, I had everything back within a few hours after deciding it was dead and replacing the failed SSD.

Hope this is helpful.

---

### Post by XwizCarl on 2018-05-22
Thanks for the response!

I'm prepared for the inevitable and there is a relatively recent backup. I support my relatives for tech support and have put them all on encrypted machines. Now this one is (or could) be in a death spiral. To the owner's credit, it is a very old machine (XP laptop). Nonetheless, developing skills in dealing with this kind of problem may be useful. And not using encryption when not needed.

I have tried cryptsetup using the advice from forums and as you mentioned. I actually have not tried chkroot, is that something that is useful early in the chain or after unlocking the encryption. I haven't been able to get cryptsetup to recognize the device as a luks encryption. 

I'll try lsblk first and see if I can learn anything new. I'm surprised there is no apparent swap partition. I tried testdisk wasn't able to do anything useful (might be incompetence)

From another thread ([https://ubuntuforums.org/showthread.php?t=1643334](https://ubuntuforums.org/showthread.php?t=1643334)) it mentioned searching through the volumes for the luks header. It gave me one radical idea that will almost assuredly not work. If the header in the pastebin, sda5 is the actual luks header and not, say, a password or something, maybe manually editing the header to mirror a proper luks header would work. It could also be a total disaster. It also raises the question of how. I could use a hex editor but I don't know how I'd get at the volume header. Another option was to use
 [COLOR=#000000][FONT=&amp]grep -a -b -P --only-matching 'LUKS\xba\xbe' /dev/sda
[/FONT][/COLOR]
However, there are to many 'matches' for this. I'm also not sure what the 'LUKS\xba\xbe' is.

As for the hardware the native OS memory scan came up with errors but the liveOS found the memory to be fine. The hdd SMART says the disk is ok with 1 bad sector. Curious where that sector is...

Thanks again Bones!

---

### Post by XwizCarl on 2018-05-22
Another problem with the hex editing idea is the sha1 encryption. This is a kernal version 3.13 computer, but I would have assumed luks would use a more advanced encryption like sha256 on my 4.15.

Edit:
According to: [https://www.forensicswiki.org/wiki/Linux_Unified_Key_Setup_(LUKS)](https://www.forensicswiki.org/wiki/Linux_Unified_Key_Setup_(LUKS))
the header for sda5 is almost certainly not the luks region, due to the sha1 (and the lack if luks)

---

### Post by XwizCarl on 2018-05-22
sda
| sda2   1K
| sda5   232.7G
| sda1   243M

sda1 is the boot partition

Compared to my functional machine

sda
| sda2                             part
| sda5                             part
   || sda5 crypt                  crypt
      ||| mint--vg-root           lvm
      ||| mint--vg-swap_1      lvm
| sda1                             part

---

### Post by TheFu on 2018-05-22
I would assume the LUKS header to be crypto-signed. Modifying will likely trash the entire encryption access.

I think you are missing knowledge about LVM.  That is key understanding when working with default "installed" systems using whole drive encryption.  The swap is inside an LV - logical volume. So is the root LV.  LVs are like partitions, but not tied to partitions. You can resize them, often while the system is running.

The using luksOpen, the correct name originally used has to be entered.  You can't just make something up.

All the pretty formatting in my posts are made using commands.  I didn't try to type those layouts in, FYI.  The only trick is to use "code tags" when posting so things line up.  AdvReply (#).

IMHO, anything portable must be fully encrypted, period.

---

### Post by XwizCarl on 2018-05-22
Ok. I tried 'Partition 5' as this name appeared to be the name of both a functioning system and the non-functioning one. Initially I didn't know which drive I should have been working with so I tried 'Partition 2' on sda2 as this also appeared to be the partition name.

Cheers

---

### Post by XwizCarl on 2018-05-22
There are probably a number of things I should have tried. I will try to organize my notes on this for the future. Unfortunately I deleted the sda5 partition in an effort to do a clean install before I read the latest update, and recovery with testdisk has been a pain. I have been overlooking the lvm issue, but it appears I have to get past luksOpen first, which I have not been able to do.

Thank you for the help!

---

### Post by TheFu on 2018-05-23
testdisk is useless with encrypted partitions.  Encrypted data looks like random data until it is unlocked. That is the whole point of encryption.

---

