---
title: "Wrong Permissions on a Mac Hard Drive"
date: 2008-02-15
forum: General Help
---

### Post by dethredic on 2008-02-15
My friend owns a mac, and he uses an external hard drive to store his pictures, music and other things. His hard drive corrupted and stopped working. He bought another one after many of his attempts were futile. 

So, he brought them both over to my house, I connect them both and boot up. The "broken" hard drive works and I can copy stuff over to my desktop. He wants to transfer all his files over to his new hard drive, but when I drag something (anything) over to the "new" hard drive I get this error:
> You do not have permissions to write to this folder.

So I did this in terminal:
> 
phil@phil:~$ sudo chmod 777 /media/External
chmod: changing permissions of `/media/External': Read-only file system
phil@phil:~$ 


I get the same error as before. The hard drive is formated mac (journaled) but so is the "broken" one so I don't see why this is a problem. Also he set full permissions for everyone.

Does anyone know how I can gain write permissions so we don't have to burn everything to DVD's?

---

### Post by dethredic on 2008-02-15
anyone?

---

### Post by dethredic on 2008-02-16
anyone?

---

### Post by LO Matt on 2008-02-16
Linux doesn't support writing to HFS+ journaled. You can read though.  Tell your friend to make it unjournaled or you can format it as fat32 and you both can read/write

Has your friend tried "Repair Permissions" "Repair Disk" from os-x on the external?

Also, I just had a problem when upgrading a machine to tiger (yes, old skool) and the firewire external drive would kernel panic the os.  A driver update from the hard drive manufacturer was required to fix.

---

