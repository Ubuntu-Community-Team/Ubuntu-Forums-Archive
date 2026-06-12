---
title: "Grub gone after cloning with Acronis boot-repair pastebin included."
date: 2023-07-13
forum: General Help
---

### Post by sim8t3 on 2023-07-13
I have a dual boot Ubuntu and I have tried the boot-repair auto option but it hasn't solved the problem, here is my pastebin  [https://paste.ubuntu.com/p/t85PHCJS88/](https://paste.ubuntu.com/p/t85PHCJS88/). I hope someone can help me get my GRUB back thanks

---

### Post by deadflowr on 2023-07-14
*Thread moved to **General Help***

---

### Post by tea for one on 2023-07-14
It looks like you have both your source disk and the cloned disk attached when booting.
Lines 279 to 284 for sda are identical to lines 337 to 342 for sdb.

Power off, remove the cloned disk and boot again.
What happens?

---

### Post by yancek on 2023-07-14
>  I have a dual boot Ubuntu and I have tried the boot-repair auto option

Generally a bad idea if you are not familiar with Grub which is why the boot repair developers suggest that you post the summary at a forum.

What exactly is the problem?  If you have cloned a device, you need to remove (detach) the first device to boot the 2nd as suggested in post 2 as they should be identical including UUIDs.

If you look at the boot repair output you will see that on Line 244 sda2 vfat  UUID  21BC-68FF is the EFI partition on that device and on Line 250 sdb1 vfat  UUID E68A-9B29 is the EFI partition on the 2nd device (sdb).  The Ubuntu / filesystem partitions have different UUIDs, Line 246 sda4 ext4   ca8b55f4-5c62-d009-0d66-45ffd5bc66e0
Line 255 sdb6 ext4     406e2ae3-6724-40fc-ad33-a32247d91f13

Lines 275 and 281 which are the grub.cfg file entries on the efi partition on sda and the ubuntu partition on sda as well as line 293,  the fstab entry on sda4, point to the UUID of the ubuntu install on sdb.  That means your system will always boot the Ubuntu sdb until you make these changes.

You should be booting to sdb.  When you boot Ubuntu, run the command:  df -h which will show which device has the / system partition.  This should be sdb, mount the / partition from sda (sda4) and the EFI partition (sda2) and make these changes using sudo.

---

### Post by sim8t3 on 2023-07-14
Same thing I get the emergency grub but no menu

---

### Post by sim8t3 on 2023-07-14
I keep getting the emergency grub menu

---

### Post by sim8t3 on 2023-07-14
So the only reason I'm using the drive I cloned from is because the Ubuntu live USB won't let me use the Wifi network I've tried everything so instead I just used the other drive. So boot-repair can't make the repair? So I have to make changes to the config file so it points to the the correct sda?  I"m still familiarizing myself with commands and what with Linux. I just remembered I tried to run BCD edit in Windows, could that be why the EFI looks the way it does? Just ran df -h but I don't find system this the closest I found "Filesystem      Size  Used Avail Use% Mounted on" but it doesn't say mounted on what? Can Rescatux maybe fix it?


Thanks

---

### Post by tea for one on 2023-07-14
Well, I am confused by your replies:-
> Same thing I get the emergency grub but no menu 
Which disk?
Or both disks?
> I keep getting the emergency grub menu 
Which disk?
Or both disks?
> So the only reason I'm using the drive I cloned from is because the Ubuntu live USB won't let me use the Wifi network
A live session and wifi is a separate problem.
Perhaps start a new thread?
> So boot-repair can't make the repair?
Repair the source disk or the cloned disk?
> I just remembered I tried to run BCD edit in Windows, could that be why the EFI looks the way it does? 
Which EFI - source disk or cloned disk?
> Just ran df -h but I don't find system this the closest I found "Filesystem Size Used Avail Use% Mounted on" but it doesn't say mounted on what? Can Rescatux maybe fix it?
You did not supply the output of the command. Therefore fix what exactly?

To be honest, I cannot figure out exactly what the problem is now?

Let's continue by looking at one question at a time.
Only have your original disk attached to the PC:-
Can you boot Ubuntu?

---

### Post by yancek on 2023-07-14
>   I tried to run BCD edit in Windows, could that be why the EFI looks the way it does?

What were you trying to accomplish when you did that.  Windows BCD does not boot Linux EFI installs.  That's a choice made by microsoft.

I've never used Acronis but the cloned drive has different partitions than the original.  Not sure how that happened o if that's the way Acronis works.  The df -h command shows only mounted partitions so if you are booting from sdb, it should show sdb6 as the / filesystem partition.  Example below showing mounted on / which is the symbol for the root filesystem.  The df -h command has 6 columns with Mounted on being the last and the root filesystem shows the symbol /

> /dev/sdb6   47G   16G   30G  35% /
  

You need to mount the partitions on sda (sda2 is EFI) and sda4 is the / filesystem partition on that device (sda).  There are countless sites explaining how to mount Linux partitions, do an online search as there is no point in repeating information readily available.  When you have mounted, you need  to be root (use sudo) to make any changes. Posting a link below on mounting, if you don't understand it there are many others available.  You just need to create a mount point (directory) then use the mount command with sudo

I don't see how you got to the point you are as the cloned disk should be identical to the original which would mean that you would boot sda as it should have the same UUIDs on both disks.  The purpose is to have the second disk available when the first fails.  So as pointed out in post 2, after doing the clone disconnect or disable the original and the cloned disk should boot.

---

