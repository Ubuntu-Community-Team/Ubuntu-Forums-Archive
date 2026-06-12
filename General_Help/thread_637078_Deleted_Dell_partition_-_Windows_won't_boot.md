---
title: "Deleted Dell partition - Windows won't boot"
date: 2007-12-10
forum: General Help
---

### Post by Puj on 2007-12-10
I really need help, i have searched the forum and google for an answer but i could not find anything. 

this is how the problem began:

1 - I wanted to make a new partition to try out linux mint along side gutsy and windows xp. 

2 - Had a "useless" dell partition of around 30mb at the start of the disk and as you can only have 4 main partitions i thought i would remove it, shift allong the main windows xp partition and make a new one for mint. 

3 - The deletion of the dell partition went fine. the shifting of the xp partition had an error saying something about the disk being busy some time near the end of the actual moving. i stupidly dident save the error report as i was doing it on the mint live cd. 

4 - Next, shut down mint live cd and tried to boot xp, it just goes to starting.... and stays there doing nothing. 

5 - The xp partition mounts as normal in ubuntu and all the data is there as far as i know - all the important stuff is backed up on an other drive too. 

I have tried fixmbr from the xp install disc but that just overwrote grub and i had to reinstall grub after that. 

Can anyone help me to get xp to boot, i believe the problems may be mainly due the the removal of the dell partition although i am not sure

here is  sudo fdisk -l which may help my explanation

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda3           10204       14528    34740562+  83  Linux
/dev/sda4           14529       14593      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2a36437

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             654        4863    33816825    7  HPFS/NTFS
/dev/sdb2               1         653     5245191   83  Linux

Partition table entries are not in disk order

```

---

### Post by chalewa on 2007-12-10
which one of those partitions is your windows one?

---

### Post by Puj on 2007-12-10
the first one on the 120GB hard drive - /dev/sda2, it used to be the second partition until i removed the dell one.

---

### Post by flamelab on 2007-12-10
The MBR has been messed up :(

What program did you use for the partition ? I hope gParted !

---

### Post by chalewa on 2007-12-10
yea i mean its obvious that the partition is still there, you should be able to get it to boot back into windows. you should just be able to make a new entry in grub that points to the windows partition and it will load it for you.

---

### Post by Puj on 2007-12-10
yea, i used gparted. i have tried changing some of the options to get grub to boot windows xp but I don't seem to be getting it right. 

my menu.lst in the boot/grub folder current is as follows - main part

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4d86c21a-50b1-419b-88b0-8dea69360d9e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4d86c21a-50b1-419b-88b0-8dea69360d9e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

What changes will i need to make - as you can see i am a bit of a noob

Also will I need to make any changes to the boot.ini or any other windows files as the windows partition is in now the first partition and after I got rid of the dell one.

---

### Post by Puj on 2007-12-11
I have tried changing " root		(hd0,0)  "

to other values but none of them worked

(hd0,0) - something about having no partition 0

(hd0,1) - stalls at "starting"

(hd0,2) - is the ubuntu partition so did not  try

so can anyone help?

---

### Post by Puj on 2007-12-18
bump! - i really need help

---

### Post by Puj on 2007-12-31
I have also tried "fixmbr" form the windows xp cd and it also did not work. i just got a blank screen after i turned on the pc. 

next I restored grub 

finally tried a recovery install from the win xp cd, once it it rebooted the pc it came back to grub and didn't continue the recovery install. 

any ideas people?

---

### Post by matburton on 2007-12-31
Hey,

My throw on the situation is as follows:
- Windows tends to assume that it's on the first partition on the disk
- Therefore I guess it assumes its partition will not be moved

Hence deleting the dubious dell partition wasn't the problem, it was moving the windows partition that probably has caused windows confusion. The menu.lst entry you provided with (hd0, 1) is correct.

Not quite sure what you can do about this, the MBR will be fine but the boot sector on the NTFS partition will be wrong.

Hmmm, perhaps [[COLOR="Blue"]_FIXBOOT_[/COLOR]]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx?mfr=true") might help.

Hope that helps ;),
Mat

---

### Post by Puj on 2007-12-31
Thanks for your reply, I have just tried fixboot as advises it dosen't seem to have made a difference. When i tried booting after i did it it just stalled at "starting..." as usual.

---

### Post by dagnabit dang doohickey on 2007-12-31
Since you moved XP, maybe your boot.ini is now pointing to the wrong partition.

---

### Post by Puj on 2007-12-31
I dont think it actualy event starts to load windows and i see no sign of it on screen and no hard drive activity when it says starting. 

 I have tried playing around with the partition numbers but i don't know how they work. in windows does it count the partitions from 1 or from 0 like in Linux. 

i have changed the numbers a little and dont quite remember how it was when it started ill paste my boot.ini below. 

```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin

```

---

### Post by dagnabit dang doohickey on 2007-12-31
The partition number should probably be 1 since XP is now on the first partition. Make a backup of your current boot.ini before editing it.

---

### Post by Puj on 2007-12-31
i'll try booting with the change now.

---

### Post by logos34 on 2007-12-31
You could also try to manually force a check disk from XP cd, but since you've already started a partition recovery operation I'm not sure what happening.

boot windows cd>'R' for recovery console>at the prompt type **chkdsk /r**

---

### Post by Puj on 2007-12-31
the boot.ini chances made no difference. 

ill try the chkdsk now, back in a while

---

### Post by Puj on 2007-12-31
I have done the chkdsk it detected and fixed some errors but it didn't help the system to boot. 

Any other ideas?

---

### Post by logos34 on 2007-12-31
> **Puj said:**
> I have done the chkdsk it detected and fixed some errors but it didn't help the system to boot. 

Any other ideas?

Did you change the boot.ini back to '...partition (2)...?

---

### Post by Puj on 2007-12-31
no, it was on 1 when i did it.

---

### Post by Puj on 2007-12-31
What's puzzling me is why the windows recovery install didn't work when i tried it. it should have worked. I might have to try it again, when it got to grub it just had the same problem.

---

### Post by logos34 on 2007-12-31
> **Puj said:**
> What's puzzling me is why the windows recovery install didn't work when i tried it. it should have worked. I might have to try it again, when it got to grub it just had the same problem.

maybe grub threw it for a loop...and the fact that your windows boot files disappeared along with that first partition.  who knows.  

what about restoring windows bootloader to the mbr, overwriting grub, THEN trying the windows recovery install once more, then reinstalling grub afterwards?

---

### Post by Puj on 2007-12-31
I don't think the boot files went with the dell partition as i can see them all when the drive is mounted on Ubuntu. 

I think i might have to give that a try though as there don't seem to be many options left after a lot of searching. 

I'll post back after i try it.

---

### Post by logos34 on 2007-12-31
> **Puj said:**
> I don't think the boot files went with the dell partition as i can see them all when the drive is mounted on Ubuntu. 

oh, ok

---

### Post by Puj on 2007-12-31
No luck, after starting the repair install when it rebooted it came to the "boot from disc" message again, i left it like you are meant to but it did nothing from there. Just froze. 

Next reboot  i tried pressing a button when it asked but it just started loading the xp cd as normal no install.

---

