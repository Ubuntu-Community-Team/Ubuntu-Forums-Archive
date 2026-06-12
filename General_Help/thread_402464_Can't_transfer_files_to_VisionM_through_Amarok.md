---
title: "Can't transfer files to Vision:M through Amarok"
date: 2007-04-05
forum: General Help
---

### Post by squirrelplayingtag on 2007-04-05
I'm trying to transfer files to my Vision:M through Amarok. I can connect to the device and it even shows all the files on the device but when ever I try to transfer any music from my hard drive to the vision:m it says can not transfer file. Running from console, the line "PTP: Access Denied" appears.  tried to run Amarok as root but still got the same error. I'm using libmtp 0.1.5. I would just use gnomad2 but when I run that it can not even detect the device.

---

### Post by sushii. on 2007-04-05
EDIT: sorry didn't read the full post. :(

---

### Post by strabes on 2007-04-06
Where is your vision:m mounted? It could be that you don't have permissions to write, in which case a simple chmod/chown should fix it.

---

### Post by squirrelplayingtag on 2007-04-06
> **strabes said:**
> Where is your vision:m mounted? It could be that you don't have permissions to write, in which case a simple chmod/chown should fix it.
Well that's an interesting question to which I do not have the answer. I can not actually find where it is mounted. It's not listed in my /mnt or /media directories. I don't have an entry in fstab, but it must be mounted somewhere if Amarok can read the information off of it right?

With it plugged in stuff like "mtp-folders" and "mtp-detect" both work...

---

### Post by strabes on 2007-04-06
In amarok, on the left part (the sidebar) on the bottom, there is a "devices" section. Open that. On the top, above your collection, it should say the /dev location and where it is mounted. For example, my ipod says "iPod Grayscale at /dev/sdb2 (mounted at /media/STRABALA)

---

### Post by squirrelplayingtag on 2007-04-06
Oh wow, this is embarrassing.  There was nothing wrong with Amarok, I just filled up my player. I guess lack of space would be a reason for being unable to transfer the files. :oops:

---

### Post by macogw on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

Do what that says, but use the compile method.  The ones in the repos don't work.  Don't do checkinstall on libmtp though.  Just use make install.  Checkinstall doesn't work for it.  If you compile them instead of using the craptastic ones from the repos, it'll work.  If it wasn't working, you either didn't use --prefix=/usr or you need to add it to the rules set (my Vision M wasn't listed either).

---

