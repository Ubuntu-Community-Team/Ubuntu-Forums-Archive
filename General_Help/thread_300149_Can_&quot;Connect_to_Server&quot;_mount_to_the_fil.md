---
title: "Can &quot;Connect to Server&quot; mount to the filesystem?"
date: 2006-11-15
forum: General Help
---

### Post by danfluidmind on 2006-11-15
Hi all.

When I connect to a Windows Share with the "Places->Connect to Server..." command, it gives me an icon on the desktop, but it does not mount the volume into the filesystem, as can be seen by running "df" at the command line. This causes a problem for applications that don't know how to use the volume through the File Browser, and make it so that you can't get to those volumes from a terminal shell.

Does Ubuntu have anything in it's GUI tools for mounting volumes to the filesystem? Or do I just have to edit /etc/fstab manually?

Thanks
--Dan

---

### Post by ser1alsn1per on 2006-11-15
try installing samba just a thought

---

### Post by danfluidmind on 2006-11-15
Um. Yeah. Samba's already installed. (Comes pre-installed with Ubuntu.) Otherwise I wouldn't be able to even connect to a Windows machine and get an icon on my desktop. The problem is not that I can't connect to a Windows server. It's that the Gnome File Browser doesn't actually mount the volume to the filesystem.

Thanks for playing.
--Dan

---

### Post by koenn on 2006-11-15
there is something like smbmount, sounds like that is what you're looking for.

[http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html) , by the end of the page.

---

### Post by danfluidmind on 2006-11-17
Thanks koenn.

Mounting a Windows share manually through the command line is no problem. What I was wondering is whether Ubuntu has something in its GUI for mounting Windows shares to the filesystem. Or, more importantly, whether there is a way to do it when you go to "Places->Connect to Server...". As far as I can tell, "Connect to Server..." doesn't mount anything to the filesystem. (So, calling it a "mount" is really erroneous.)

--Dan

---

### Post by gosh on 2006-12-03
Hi Dan,

I have the same question as you have.
It is called "mounting" but I can't seem to find the mount point.
Have you come up with anything yet?

---

### Post by gosh on 2006-12-03
Well, actually I do have solved it!

With fusesmb you can mount your network shares at any point in the filesystem you like.
This: [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131) and this: [http://ubuntuforums.org/showthread.php?t=71797](http://ubuntuforums.org/showthread.php?t=71797) helped me get it working.

---

