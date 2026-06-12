---
title: "removing an &quot;immutable&quot; file"
date: 2005-08-07
forum: General Help
---

### Post by mbaile17 on 2005-08-07
I'm trying to use the Ubuntu LiveCD to remove a very stubborn bit of code from a Windows system.  The program is called pokapoka62.exe and resides in C:\WINDOWS\etb.  

I started by booting from the CD and mounting the partition rw.  I then moved to the directory (/mnt/windows/WINDOWS) and typed:

rm -rf etb

And got:

rm: cannot remove `etb/etb.ini': Operation not permitted
...for everything in the file.

 ](*,) 

I searched around for a bit and found that the problem could be an immutability flag of some kind.  I tried to remove it:

chattr: Inappropriate ioctl for device while reading flags 

 :mad: 

I'm not even entirely sure what that means; I've never had this problem before.  I have su privileges; what should I do?

Thanks!
Meg

---

### Post by aveline on 2005-08-07
[QUOTE=mbaile17]I'm trying to use the Ubuntu LiveCD to remove a very stubborn bit of code from a Windows system.  The program is called pokapoka62.exe and resides in C:\WINDOWS\etb.  

I started by booting from the CD and mounting the partition rw.  I then moved to the directory (/mnt/windows/WINDOWS) and typed:

rm -rf etb

And got:

rm: cannot remove `etb/etb.ini': Operation not permitted
...for everything in the file.

 ](*,) 

I searched around for a bit and found that the problem could be an immutability flag of some kind.  I tried to remove it:

chattr: Inappropriate ioctl for device while reading flags 

 :mad: 

I'm not even entirely sure what that means; I've never had this problem before.  I have su privileges; what should I do?

Thanks!
Meg[/QUOTE]
 is it an ntfs partition?? I assume yes... from what you've said in which case you need to mount it in a special fashion.  Search the forums for mounting NTFS drives/partitions or post back & i'll give you a post to a script that will mount it for you if you like assuming ubuntu is an installed OS.

aveline

---

