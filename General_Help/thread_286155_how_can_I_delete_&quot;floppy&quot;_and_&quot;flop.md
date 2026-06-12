---
title: "how can I delete &quot;floppy&quot; and &quot;floppy1&quot; from nautilus places?"
date: 2006-10-27
forum: General Help
---

### Post by bionnaki on 2006-10-27
how can I get rid of these places in the sidepanel of nautilus:

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=18322&stc=1&d=1161974890[/IMG]

I never use a floppy disk...ever. well, not since 1996. so, I really dont want to see them anymore :mrgreen: 

thanks

---

### Post by reclusivemonkey on 2006-10-27
> **bionnaki said:**
> how can I get rid of these places in the sidepanel of nautilus:


I never use a floppy disk...ever. well, not since 1996. so, I really dont want to see them anymore :mrgreen: 


In /etc/fstab, just put a "#" in front of the floppy entry, like this;

```

# /dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

with your favourite text editor (I use 

```

sudo vim /etc/fstab

```

and viola, its gone! If you ever do need to use a floppy for some reason (like you want to lose some data ;-) ) then just remove the hash.

---

### Post by denzilla on 2006-10-27
I reported that bug in plenty of time for it too be fixed but I guess it wasn't important.

---

### Post by reclusivemonkey on 2006-10-27
> **denzilla said:**
> I reported that bug in plenty of time for it too be fixed but I guess it wasn't important.

...or someone decided it wasn't a bug...

---

### Post by marcozs on 2006-10-27
Hi,

I don't wanna erase the floppy drive (I need it :) ) but the "Floppy 1" is bothering me cause I don't have two floppies so I wanna see just one... is it possible to erase it without taking away the real floppy?

---

### Post by reclusivemonkey on 2006-10-27
> **marcozs said:**
> Hi,

I don't wanna erase the floppy drive (I need it :) ) but the "Floppy 1" is bothering me cause I don't have two floppies so I wanna see just one... is it possible to erase it without taking away the real floppy?

Just enter the hash in front of the second floppy drive in /etc/fstab, which is most likely floppy1 rather than floppy0. Just entering a hash in front of the line ensures you aren't "erasing" your floppy drive, just making the entry for it in fstab inactive.

---

### Post by marcozs on 2006-10-27
I thought about it... but I have only one floppy in my fstab!!!

---

### Post by reclusivemonkey on 2006-10-27
> **marcozs said:**
> I thought about it... but I have only one floppy in my fstab!!!

Can you post your fstab?

---

### Post by marcozs on 2006-10-27
Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e82ec3c9-0159-412a-a719-cb10db53b4c3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=4ccb0ff6-ea33-48b7-a9ef-e64fd02a2ec3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=D61C0D571C0D3451 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=DC10ACBC10AC9F50 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=444D-2954  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=321e8c3c-980c-471a-9024-1f1960aec054 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by reclusivemonkey on 2006-10-27
> **marcozs said:**
> Here it is:
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

With that exact same fstab line, I only get Floppy 1, so I don't know what's wrong there I'm afraid.

---

### Post by marcozs on 2006-10-27
> **reclusivemonkey said:**
> With that exact same fstab line, I only get Floppy 1, so I don't know what's wrong there I'm afraid.

I get "Floppy 1" and "Floppy Drive" but when I click on "Floppy Drive" then the floppy drives looks for a floppy to read while when I click on "Floppy 1" it doesn't do anything and just says that the system is unable to mount it... That's why I just wanna get rid of the "Floppy 1"

---

### Post by denzilla on 2006-10-27
> **reclusivemonkey said:**
> ...or someone decided it wasn't a bug...

It was confirmed.... In another thread, I was told to just delete the floppy line in fstab to see if that fixed it and it did. Bug should still have been fixed though.


**Just fresh installed 6.10 and the ghost floppy is still present. Opened fstab and deleted the floppy line as originally instructed and it worked as expected. Only 1 floppy is shown and it works like it should.

---

### Post by Cariboo1938 on 2006-11-05
> **denzilla said:**
> It was confirmed.... In another thread, I was told to just delete the floppy line in fstab to see if that fixed it and it did. Bug should still have been fixed though.
**Just fresh installed 6.10 and the ghost floppy is still present. Opened fstab and deleted the floppy line as originally instructed and it worked as expected. Only 1 floppy is shown and it works like it should.My fresh installed /etc/fstab had this line:> /dev/           /media/floppy0  auto    rw,user,noauto  0       0 I chanched it to:> [COLOR="Magenta"]/dev/fd0[/COLOR]           /media/floppy0  auto    rw,user,noauto  0       0and the ghost Floppy 1 (not serious but annoying) was gone. 
Who ever may decide if this is a bug or not is hard to tell????:-k

---

### Post by Leonivek on 2006-11-06
>  I chanched it to: 	Quote:
 	 	 		 			 				[COLOR=Magenta]/dev/fd0[/COLOR]           /media/floppy0  auto    rw,user,noauto  0       0 			 		 	 	 
and the ghost Floppy 1 (not serious but annoying) was gone. 

Hey, thanks!  That /dev/fd0 fixed my duplicate Floppy entry too! 

If you delete or comment the floppy line, it doesn't fix the problem.  It completely removes the floppy mount so that there are none whatsoever.  That isn't a fix.  But changing it to /dev/fd0 does fix the problem.

Thanks!

---

