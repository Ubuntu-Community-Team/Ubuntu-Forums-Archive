---
title: "grub: inconsistent filesystem structure after last kernel update"
date: 2007-09-02
forum: General Help
---

### Post by oldmanstan on 2007-09-02
after the last (feisty) kernel update i rebooted my computer (as directed) and when i selected my installation from grub i got a inconsistent filesystem structure error from grub.  the recovery mode won't work either, same error.

i booted into another install that hadn't gotten the update (gutsy) and ran fsck on the partition (with the problem)... the first time i ran it, it said that the date for the last time the drive was mounted was in the future and said it fixed the problem.  rebooted, same error from grub.

ran fsck again, said drive was clean, same error though.  ran fsck -f on the drive, did its thing for awhile, after it finished i tried again, same error.

any ideas for what else i could do to fix this?

thanks

---

### Post by meierfra on 2007-09-02
Other people had similar problems. The update messed up the file /boot/menu/lst in the feisty install. It should have back-upped  the file before hand. So you should be able to just replace menu.lst by the most reasoned back-up. Let me know if you need help with that. ( Also you should look at the files  to see whether my suggestions really makes sense in your case)

---

### Post by merlinus on 2007-09-02
What usually happens is that the grub root is changed.

You can check this by pressing e at the grub menu and looking at the root.  It should reflect your first hard disk and ubuntu partition, so if ubuntu is on the third partition, change it to (hd0,2).

Then press b to boot.

You can try other numbers as well.

Once it is working, you can edit /boot/grub/menu.lst to make the change permanent.

-merlin

---

### Post by oldmanstan on 2007-09-02
ok, thanks for the replies, here's some more info:

first, i can't find any backups of menu.lst.  i had installed the other version of ubuntu after the main version, so would the menu.lst i want be on the second hard drive? the menu.lst on the main drive makes no mention of other installs so it can't be the right one

second, i tried using the rescue function on the install cd (turns out to be pretty useless), i reinstalled grub with it, thinking that would work, it didn't.  doing so eliminated my other grub entries (to the installs that work, there are actually 2 gutsy installs both on second HD, 2 partitions).  so to fix that i just wiped on of the gutsy installs and replaced it with a new feisty install, which auto-detected the other installs and added them back to grub (yes, it's a round-about way of fixing things but i didn't no any other way).

third, there are no differences between the grub commands in the menu.lst file on my main HD (the one that doesn't work) and the other menu.lst file that grub is actually using.  also, the drive seems correct for the entry that doesn't work, it is (hd0,0) which is correct as far as i know, first partition on the first HD.

this is really bugging me, i don't understand how a simple upgrade can kill my whole hard drive.  did the testing people screw up or what? i salvaged everything in my home dir by moving it to the other drive but i REALLY REALLY REALLY don't want to have to totally redo my OS.

---

### Post by meierfra on 2007-09-02
I don't have much hope that this will lead to anything but one has to start somewhere: Post the menu.lst from the feisty, and the menu.lst  actually used by grub. Also post the output of  "sudo fdisk -l"

---

### Post by oldmanstan on 2007-09-02
> **meierfra said:**
> I don't have much hope that this will lead to anything but one has to start somewhere: Post the menu.lst from the feisty, and the menu.lst  actually used by grub. Also post the output of 
"sudo fdisk -l"

here's feisty
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

here's the one from the most recent install, which i assume is the one that's being used...

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d9c049f-83ea-4070-8f48-ec86e9072a36 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d9c049f-83ea-4070-8f48-ec86e9072a36 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6be544a-64af-46ab-9f6d-a80c08a82b83 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.22-10-generic (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=013a0a2d-9d47-4fb2-9b58-dfefce6a6489 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.22-10-generic (recovery mode) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=013a0a2d-9d47-4fb2-9b58-dfefce6a6489 ro single 
initrd		/boot/initrd.img-2.6.22-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, memtest86+ (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, memtest86+ (on /dev/hda1) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.22-10-generic (on /dev/hdb1) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ede25e6d-4c82-4ca9-af87-697c310d936e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.22-10-generic (recovery mode) (on /dev/hdb1) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ede25e6d-4c82-4ca9-af87-697c310d936e ro single 
initrd		/boot/initrd.img-2.6.22-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, memtest86+ (on /dev/hdb1) (on /dev/hdb3)
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

i only posted the portions that make up the lists, not the random options at the top

here's sudo fdisk -l

```
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e478d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       37966   304961863+  83  Linux
/dev/hda2           37967       38913     7606777+   5  Extended
/dev/hda5           37967       38913     7606746   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x069b47d0

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4777    38371221   83  Linux
/dev/hdb2            9554        9964     3301357+   5  Extended
/dev/hdb3            4778        9553    38363220   83  Linux
/dev/hdb5            9554        9964     3301326   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 125 MB, 125960192 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         961      122959+   6  FAT16

Disk /dev/sde: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         953     1966064    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 128, 32) logical=(952, 71, 32)
```

thanks!

---

### Post by meierfra on 2007-09-02
I don't see anything wrong. Could you post the output of

```
sudo fdisk -l
```
and 
> blkid

---

### Post by oldmanstan on 2007-09-02
blkid

```
/dev/hda1: UUID="e6be544a-64af-46ab-9f6d-a80c08a82b83" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" UUID="252280a8-7ceb-4008-8816-0b867602daae" 
/dev/hdb1: UUID="4d9c049f-83ea-4070-8f48-ec86e9072a36" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb3: UUID="013a0a2d-9d47-4fb2-9b58-dfefce6a6489" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: TYPE="swap" UUID="c09521b2-edc5-4a0a-98d2-5b3a9ab269b5" 
/dev/sda1: SEC_TYPE="msdos" UUID="6433-3138" TYPE="vfat" 
/dev/sde1: SEC_TYPE="msdos" UUID="89E9-C95C" TYPE="vfat" 
```

fdisk output was in last reply, sorry, i didn't see that part in your message so i had to add it

thanks

---

### Post by meierfra on 2007-09-03
Well everything seems to be the way it should  to be.   So I don't really have any good suggestion.

I googled for grub error 16. The only thing I found, which was even remotely promising, was  somebody how solved the problem by moving the  /boot folder to a  separate partition: 

[http://readlist.com/lists/suse.com/suse-linux-e/10/54583.html]("http://readlist.com/lists/suse.com/suse-linux-e/10/54583.html")

Unless somebody comes up with a better idea, that   might be worth  a try.  I have never done that , so I'm not quite sure what is all involved but the principal steps should be like this: Shrink hda1 by a little bit, create  a new partition and  format it to ext3. Backup your /boot folder. Empty the /boot folder. Mount  the new partition at /boot  and copy the backup of /boot to /boot.  Edit  /etc/fstab ( to mount /root permanently) and menu.lst (since the /root  is now mounted)

---

### Post by meierfra on 2007-09-03
Just another thought: Did you try booting from the older kernel 

Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)

---

### Post by oldmanstan on 2007-09-03
> **meierfra said:**
> Just another thought: Did you try booting from the older kernel 

Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)

no, no i did not, until this morning when i started the computer i took a look through the list on grub and decided to give the older one a try, it works... i was just about to post that here and saw your message, good thinking! :)

question though: is booting from the old kernel going to affect the system in terms of stability or anything else?

thanks again

---

### Post by meierfra on 2007-09-03
I would guess that the older kernel should be fine for now.

But you might try reinstaling  the linux-headers which got upgraded. ( or roll back to the previous linux-headers, if that's possible)

---

