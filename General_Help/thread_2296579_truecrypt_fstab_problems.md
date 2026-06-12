---
title: "truecrypt fstab problems"
date: 2015-09-26
forum: General Help
---

### Post by drm200 on 2015-09-26
I have a truecrypt volume that is formatted fat32.  When i manually mount the truecrypt volume, Ubuntu considers all the text files as executables.  As this is only a data drive, none of the files are executable.  So, I'd like to click on any file and not see: "Do you want to run?"  Instead, I want the text editor to immediately open.

So I modified my fstab as follows by adding the noexec and fmask and dmask arguments:

/dev/disk/by-uuid/D558-90BA /mnt/D558-90BA auto nosuid,nodev,noexec,nofail,dmask=007,fmask=117,uid=1000,gid=1000,x-gvfs-show 0 0

But I still get the message "Do you want to run?" .... and if I look at the permissions in the terminal, I see this:

     lrwxrwxrwx 1 root root  10 Sep 27 09:52 D558-90BA -> ../../dm-0

So, Ubuntu still considers the files executable.   I think, that the permissions are not being updated by the fstab because the actual mount point of the truecrypt volume is something different, but am unsure on how to resolve this.

---

### Post by DK1993 on 2015-09-27
Quick question. Does this happen with text files globally on your system (i.e. text files that are located elsewhere on your computer) or is it just in the TrueCrypt volume? If it is only with the TrueCrypt volume, I would recommend migrating the data into an ext3 or ext4 filesystem, as those two natively support file permissions, whereas your edit to permissions will actually stick in Terminal. FAT32 does not support file permissions as it is originally a Microsoft filesystem, which doesn't use the executable flag in its system (only r/w). Hope this helps.

---

### Post by drm200 on 2015-09-27
> **DK1993 said:**
> Quick question. Does this happen with text files globally on your system (i.e. text files that are located elsewhere on your computer) or is it just in the TrueCrypt volume? If it is only with the TrueCrypt volume, I would recommend migrating the data into an ext3 or ext4 filesystem, as those two natively support file permissions, whereas your edit to permissions will actually stick in Terminal. FAT32 does not support file permissions as it is originally a Microsoft filesystem, which doesn't use the executable flag in its system (only r/w). Hope this helps.

I'm not having this problem with the Linux partitions.  It is only a problem for the truecrypt partition.  The truecrypt partition is shared with Windows so, I'd like the file system to remain fat32 or ntfs ... I understand that FAT32 does not support file permissions, but I had understood that the fstab would be able to set the permissions for all the files by setting [COLOR=#000000][FONT=Ubuntubeta]fmask=117.


[/FONT][/COLOR]

---

### Post by drm200 on 2015-09-27
Ok ... I figured it out.  This is now the line in my fstab:

> /dev/mapper/truecrypt1 /media/truecrypt1 auto rw,dmask=007,fmask=117,uid=1000,gid=1000,x-gvfs-name=myData 0 0


Now when I mount the truecrypt volume (that has FAT32 file system) the text files are no longer seen as executable ... So when I click on a text file, the editor immediately opens.

---

