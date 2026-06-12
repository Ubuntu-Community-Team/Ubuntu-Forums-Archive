---
title: "Cdrom permissions..."
date: 2008-05-15
forum: General Help
---

### Post by jtraveller on 2008-05-15
Hello, im new, just a week since i installed. 
 
**The Problem:**

whenever i insert a data disk (usually burned at work in a mac or from windows) it mounts, it allows me to browse the disk, but i cant copy a thing, since only root have permission to do that.

i should have done something wrong, but i dont know what, or where. in users and groups im allowed to, basically, use and do everything in the list.

---

### Post by chrisccoulson on 2008-05-15
Are you trying to copy from the CD? If so, where to?

---

### Post by jtraveller on 2008-05-15
in this particular case it was a dvd with music inside, i was triying to copy it the hard drive.

actually, now i see i cant even unmount it

---

### Post by pbeesley on 2008-05-15
i had this issue yesterday, so I'll be watching this for an answer...to un mount the cd, open up a terminal, log in as root su umount /dev/scd0 (SCD0 is my cdrom drive, your might be different)

---

### Post by jtraveller on 2008-05-15
one more thing, i can burn with brasero wthout a problem, the thing even ejects the disk O_o

---

### Post by partom24 on 2008-05-25
I've been trying to get my computer to write a CD for about a week now unsuccessfully, I've tried the "sudo chown" command to try and set the permissions for my drive, but that only works for the mount point in the /media folder.

I've also tried using the "gksudo Nautilus" line, I know its dangerous, but I'm pretty desperate, and when I open up the Permissions tab, the only thing it says for ALL of my drives is "The permissions for "XXX Drive" could not be determined"... is there anyway to fix this?

Also here is my fstab file in case there is something not correct here..
# /etc/fstab: static file system information.
#
# <file system>                             	<mount point>   	<type>  <options>                               <dump>  <pass>
proc            				/proc          		proc    defaults        			0       0
# /dev/sdb1
UUID=bff3db44-0069-4bc9-b34b-0cab21585f6c 	/               	ext3    relatime,errors=remount-ro	 	0       1
# /dev/sdb5
UUID=a2023467-cbf6-4c57-9825-7bd4de826a14 	none            	swap    sw              			0       0
/dev/scd1       				/media/cdrom0   	udf,iso9660 user,noauto,exec,utf8		0       0
/dev/scd0       				/media/cdrom1   	udf,iso9660 user,noauto,exec,utf8		0       0
/dev/fd0        				/media/floppy0  auto    rw,user,noauto,exec,utf8 			0       0

---

