---
title: "Unable to boot please help"
date: 2015-01-28
forum: General Help
---

### Post by alasdair3 on 2015-01-28
I have ubuntu server 14 on a 16gb usb drive which has been running perfectly. The install was done using default settings and comprises the following three partitions:
 - 512mb fat32 partition with the /boot flag
 - 256mb ext2 partition that contains /grub and /efi folders
 - a 14gb lvm partition containing /home, /root and /swap.

The root volume became full so I booted a ubuntu live usb and resized it with system-config-lvm. 

Since then my main system has been unable to boot at all - I just get a message asking me to insert bootable media on powering on.
I can boot the live USB without problem and have tried running boot-repair but it just gives me an error "GPT detected, please create boot paritition". I tried following it's instruction without success.

I'm sure there is a way to repair or reinstall the necessary boot-loader onto my main system but I can't figure out how.

If anyone could point me in the right direction I'd be very grateful.

Many thank in advance for your help.

---

### Post by dragonfly41 on 2015-01-28
If you boot up again with live USB .. then install boot repair from here ..

[https://sourceforge.net/p/boot-repair](https://sourceforge.net/p/boot-repair)

and apply .. also taking written note of the pastebin url created after repair .. I hope that this will sort your problem.

[edit]

Sorry skim read your post too quickly .. more on subject here.

[http://ubuntuforums.org/showthread.php?t=2216976](http://ubuntuforums.org/showthread.php?t=2216976)

---

### Post by alasdair3 on 2015-01-28
Thanks for your reply.

I did try using boot-repair on a live usb. Unfortunately it just gave me an error: "GPT detected, please create boot partition". 

I think I need to re-install grub-efi but I'm just not sure how. Part of the problem is that I don't really understand what all the partitions are on my system. They were created automatically during the ubuntu install.
 - 512mb fat32 partition with the /boot flag - I think this has something to do with EFI but I'm not sure what. I don't know whether any files should / were / are located on it or what there purpose is but I'm guessing it's relevant to my problem
- 256mb ext2 partition that contains /grub and /efi folders - Again, this looks important and seems to contain files relevant to booting. Is this the main boot directory? If so, is this where I would need to re-install grub-efi?
- a 14gb lvm partition containing /home, /root and /swap - from what I understand, this contains the actual os and doesn't really have anything to do with the bootloader per say. My problem seems to be actually getting GRUB to start during power-on, so I think files here are more "downstream".

My system is set to boot as UEFI - this hasn't changed recently and used to work. I have tried switching to legacy but it still fails to boot. I don't know whether the UEFI side of things is important to how I fix this.

Many thanks.

---

