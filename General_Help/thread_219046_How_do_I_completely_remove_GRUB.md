---
title: "How do I completely remove GRUB?"
date: 2006-07-19
forum: General Help
---

### Post by AhrenBa on 2006-07-19
Hello,
I know this is an ubuntu forum, but I thought you guys would have an answer to this:

I had MEPIS installed on my system and I just used a windows boot disc to format the entire hard drive so that I could take off MEPIS and reinstall Windows 98. 

I formatted the whole drive, deleted the partitions, and then reinstalled windows. However, now when I boot, a text line comes up displaying something about GRUB and will not let me continue to windows. How do I completely remove GRUB? Thanks.

---

### Post by Joeb on 2006-07-19
Normally installing Windows 98 will rewrite the master boot record and overwrite grub.  However, if this did not happen and since you can't boot into Windows, if you have the floopy disk that came with Windows 98 you can boot from it and run fdisk /mbr to rewrite the master boot record which will remove all traces of grub (or any other boot loader that may be there).

edit: you don't need the Windows 98 floppy, any bootable floppy with fdisk on it will work.  If you were able to boot into windows through grub, then you could run the fdisk command from there.

---

### Post by Xecuter on 2006-07-19
> **AhrenBa said:**
> Hello,
I know this is an ubuntu forum, but I thought you guys would have an answer to this:

I had MEPIS installed on my system and I just used a windows boot disc to format the entire hard drive so that I could take off MEPIS and reinstall Windows 98. 

I formatted the whole drive, deleted the partitions, and then reinstalled windows. However, now when I boot, a text line comes up displaying something about GRUB and will not let me continue to windows. How do I completely remove GRUB? Thanks.

You can't actually remove Grub, since it's located at the beginning of the harddrive. What you have to do is rewrite it again. I'm not shure about Win98, but you can try to start Windows in MS-Dos via the CD or something and write 'fixmbr'. This will rewrite it and you should be out of trouble.  It works on WinXP. 

You might have to get a disc that boots MS-Dos for you or something.

---

### Post by mlind on 2006-07-19
If you want to remove grub from MBR, but keep the partition table record
```

dd if=/dev/zero of=*/dev/xxx* bs=446 count=1

```
If you want to wipe out the whole MBR
```

dd if=/dev/zero of=*/dev/xxx* bs=512 count=1

```

where */dev/xxx* is the physical drive, like /dev/hda or /dev/sda.


I would personally grab win98 bootdisk from bootdisk.com and execute 'fdisk /mbr' after booting, or use winxp's recovery console and command 'fixboot'.

---

