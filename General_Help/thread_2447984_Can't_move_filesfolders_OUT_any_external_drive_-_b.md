---
title: "Can't move files/folders OUT any external drive - but can move them in and view them."
date: 2020-07-30
forum: General Help
---

### Post by crazybear on 2020-07-30
I want [mostly] to move files from an older Ubuntu on a desktop to a newer Ubuntu on a Dell XPS 15 9550 laptop. As the laptop has no LAN port and the desktop no wiif, I settled on using a USB-C external drive. So, now I have filled the external drive with files I need to put in the laptop. To put them in, I had to chown the external drive. Done. On the laptop I can see everything, I can view photos and open files, BUT I CAN NOT move them to the laptop. It is NOT ONLY true for the external drive, but for any USB flash drive or a memory stick from my camera. What is going on - and how can I fix it?!?! Thanks

---

### Post by TheFu on 2020-07-30
Don't use move. Use **rsync** to copy all the files.

Or  fix the permissions on the external disk. Depending on the file system it has then either chown or mount options will be necessary.  FAT32, exFAT, NTFS don't support chown.

---

### Post by crazybear on 2020-07-30
> **TheFu said:**
> Don't use move. Use **rsync** to copy all the files.

Or  fix the permissions on the external disk. Depending on the file system it has then either chown or mount options will be necessary.  FAT32, exFAT, NTFS don't support chown.

I can't use rsync, as I have NO way to connect the two computers at the moment without a lot of work and buying some hardware.
Tried Chown, but didn't work. Don't know what you mean by mount options. Drive is ext4, but the laptop will NOT let me move things in from a fat32 zip drive either - nor my camera's memory stick [don't know how it is formated]; so the problem seems NOT to be type of formating of the drive dependant.

---

### Post by TheFu on 2020-07-30
> **crazybear said:**
> I can't use rsync, as I have NO way to connect the two computers at the moment without a lot of work and buying some hardware.
Tried Chown, but didn't work. Don't know what you mean by mount options. Drive is ext4, but the laptop will NOT let me move things in from a fat32 zip drive either - nor my camera's memory stick [don't know how it is formated]; so the problem seems NOT to be type of formating of the drive dependant.

The format on the source storage matters, hence the problem with "move" - which is implemented across different file systems as "copy + delete".  It is not ext4 on the source storage.  Sure, the target storage is ext4, but assuming you are trying to move the files to your HOME or a directory where the current userid has rights to write, that wouldn't matter.  It is the source which is probably read-only, hence "move" doesn't work.

rsync works between network or directly connected storage.  Any two directories - local or remote or both local or both remote.  Whenever there is a large number of files, I prefer rsync, so if something bad happens, restarting from the beginning isn't necessary.

---

### Post by ActionParsnip on 2020-07-30
What file system did you format the USB drive to please?

---

### Post by crazybear on 2020-07-31
> **ActionParsnip said:**
> What file system did you format the USB drive to please?

It is an MVM.2 556GB in an external case connected to the USB-C formatted in ext4.

---

### Post by TheFu on 2020-07-31
> **crazybear said:**
> It is an MVM.2 556GB in an external case connected to the USB-C formatted in ext4.

When both the SOURCE and TARGET are mounted, please run 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and post the results with "code tags".  Let us know which is the SOURCE and which is the TARGET. Please.

---

### Post by kurt18947 on 2020-07-31
> **crazybear said:**
> It is an MVM.2 556GB in an external case connected to the USB-C formatted in ext4.

I use rsync with a GUI to sync folders between folders on my /home and folders in a flash drive. I think I did format the flash drive to FAT32 in case I needed to access the files with a non-linux system.

---

### Post by QIII on 2020-07-31
Several impolite posts removed.  Keep it civil, please.

---

