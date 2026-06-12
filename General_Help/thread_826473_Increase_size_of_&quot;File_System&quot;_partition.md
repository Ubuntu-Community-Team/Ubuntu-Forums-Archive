---
title: "Increase size of &quot;File System&quot; partition?"
date: 2008-06-11
forum: General Help
---

### Post by khanis on 2008-06-11
Is this possible in anyway?
 I accidentally installed Ubuntu on the wrong partition, and really do not want to reinstall it again. Is there any way I can "add" additional storage space on to the partition? 

Currently in Ubuntu 8.04
(And loving it so far!)

Thanks in advance.

---

### Post by molotov00 on 2008-06-11
Is there free space on the hard drive?

sudo apt-get install gparted
gksu gparted

That's the partition editor. ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)). You can increase the size that way.

If you installed onto the wrong drive then you can use a command called 'mount' in Linux. i.e. if HDD1 is /dev/sda1 and HDD2 is /dev/sda2 then you can literally make the second hard drive appear as a folder in /home/molotov or wherever you want.

I'm a little confused by your question because Ubuntu installs onto multiple partitions. Hopefully gparted will show you what I mean, when you run it.

Hope that helps.

---

