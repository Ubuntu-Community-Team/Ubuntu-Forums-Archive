---
title: "&quot;No Bootable Device&quot;"
date: 2013-03-18
forum: General Help
---

### Post by Thornisdan on 2013-03-18
Hello,
I accidently dropped coffee on my laptop and now whenever I boot up my laptop I get "No Bootable Device". Linux does not boot up. My desktop has only ubuntu as an operating system.
I absolutely need to get some information saved on my laptop. Is there a way to boot it up so I could move my information to my desktop.
I was thinking of reinstalling linux but would that loose my saved information?
My desk top has windows 8.

---

### Post by sudodus on 2013-03-18
> **Thornisdan said:**
> Hello,
I accidently dropped coffee on my laptop and now whenever I boot up my laptop I get "No Bootable Device". Linux does not boot up. My desktop has only ubuntu as an operating system.
I absolutely need to get some information saved on my laptop. Is there a way to boot it up so I could move my information to my desktop.
I was thinking of reinstalling linux but would that loose my saved information?
My desk top has windows 8.
The coffee has probably not damaged the internal HDD, so at least you can take it out of your laptop and connect it to your desktop or another computer. And Ubuntu is portable. You might need to change the UEFI settings to BIOS temporarily, similar to what is explained in many recent threads in the Ubuntu Forums about dual booting with Windows 8. It's tricky, so a better solution might be to connect the drive to an older computer with BIOS.

A friend of mine destroyed a computer in a similar way. Did you try to boot it from a CD or USB drive, for example your Ubuntu install drive? If it does not boot, something is damaged: the keyboard or something underneath. Would it help to connect an external (USB) keyboard?

Edit: another way to save the files is to install drivers for linux ext file systems into Windows, and read/copy the files from Windows. See this link [[COLOR=#ff0000]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by Thornisdan on 2013-03-18
> **sudodus said:**
> A friend of mine destroyed a computer in a similar way. Did you try to boot it from a CD or USB drive, for example your Ubuntu install drive? If it does not boot, something is damaged: the keyboard or something underneath. Would it help to connect an external (USB) keyboard?

Edit: another way to save the files is to install drivers for linux ext file systems into Windows, and read/copy the files from Windows. See this link [[COLOR=#ff0000]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")


I can boot from the CD, but it doesn't show my files from my HD. I figure it's cause I'm running of the CD. 
I will check out the link you gave. I don't have a scewdriver since I'm at school right now so I can't remove my hard drive. I will pick one up when I leave this evening.




When boot up without the CD it says
"PXE-E61:Media test failure, check cable
PXE-M0D: Exiting Broadcom PXE ROM
No Bootable device --- insert boot disk and press any key"

---

### Post by sudodus on 2013-03-18
> **Thornisdan said:**
> I can boot from the CD, but it doesn't show my files from my HD. I figure it's cause I'm running of the CD. 
I will check out the link you gave. I don't have a scewdriver since I'm at school right now so I can't remove my hard drive. I will pick one up when I leave this evening.




When boot up without the CD it says
"PXE-E61:Media test failure, check cable
PXE-M0D: Exiting Broadcom PXE ROM
No Bootable device --- insert boot disk and press any key"

Well, try again to*** boot from the CD and try to mount the internal drive***. Maybe the situation is not too bad. Maybe 'only' a problem with a corrupt file system because of a dirty shut down.

Please post the output of the following commands
```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```
and I or someone else will suggest what command to run (without knowing more I suggest something like this)

```
sudo umount /dev/sdxy
```
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter (probably a) and y is the partition number. x and y are to be found by the output of those three commands above.

After the e2fsck command you can try to reboot from the internal drive.

---

