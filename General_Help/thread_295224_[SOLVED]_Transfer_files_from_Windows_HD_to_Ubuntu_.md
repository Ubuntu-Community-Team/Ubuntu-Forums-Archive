---
title: "[SOLVED] Transfer files from Windows HD to Ubuntu HD"
date: 2006-11-07
forum: General Help
---

### Post by noerrorsfound on 2006-11-07
Is there any way to transfer files from my Windows hard drive to my Ubuntu hard drive, other than using a flash drive or uploading and downloading the files somewhere?

---

### Post by sethmahoney on 2006-11-07
If your Windows HD is still connected to a Windows computer, you can enable ext3 in Windows (search the forums for how to do that - its all over) and just copy files over like you normally do.  If the HDs are on different computers, you can use Samba to transfer files between them over a network.  If they're on the same computer but you don't have Windows installed anymore, Linux can read both FAT32 and NTFS filesystems, so you can transfer files in Linux as well.  Any way you look at it, you have options, and if you need help on how to work any of them out, just ask!

---

### Post by marianom on 2006-11-07
You could use PSCP, too:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Download pscp.exe to your windows machine and use it as you would use scp when transferring files from a linux box to another linux.

---

