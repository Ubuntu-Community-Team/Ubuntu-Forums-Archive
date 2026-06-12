---
title: "show mounted volumes (Solved)"
date: 2006-11-01
forum: General Help
---

### Post by dcherryholmes on 2006-11-01
I would like to have removable media show up as an icon on the desktop, but I don't want my hard drive partitions shown.  I know you can toggle "show mounted volumes" under gconf-editor -> nautilus -> desktop, but that also prevents removeable media from showing up.  Anyone know of a solution?

---

### Post by taurus on 2006-11-01
If you don't want your harddrives to show up on your desktop, then change the mount points to something else besides the /media in /etc/fstab...  Assuming that you have /dev/hda1 mounts on /media/hda1 in /etc/fstab, you can change that to something like /mnt/hda1!

Open a terminal, Applications -> Acessories -> Terminal, and type

```

sudo mkdir /mnt/hda1 <-- create a new mount point
sudo cp /etc/fstab /etc/fstab.bak <-- make a backup copy
gksudo gedit /etc/fstab <-- edit /etc/fstab...

```
Now, just change it from "/media/hda1" to /mnt/hda1" and save it.  Reboot and it won't show up on your desktop but you still can access your /dev/hda1...

---

### Post by dcherryholmes on 2006-11-01
Sweet!  I had no idea that /media had special status.

---

### Post by taurus on 2006-11-01
Yip!  Everything mounts on /media will have an icon on your desktop.

---

### Post by dcherryholmes on 2006-11-03
It appears that you were wrong.  I changed my mount points, re-enabled the show mounted volume option in gconf-editor, and all three hard drive partitions re-appeared on my desktop.  I have the option enabled in nautilus that shows the text box, and when I click on one of the icons, it definitely shows /mnt/foo.  Further, the original directories in media have been deleted.  So, mounted volumes in other than /media also show up.  Perhaps /mnt is "special" too?  I'll try mounting them straight off / and see if that behaves differently.

---

### Post by dcherryholmes on 2006-11-03
Yeah, no difference even if I mount them off /.  How do you unmark a thread "solved"? :)

---

### Post by ravenon on 2006-11-03
Did you reboot? I have my other disks mounted in /mnt via fstab and after reboot, they are off the desktop.

---

### Post by dcherryholmes on 2006-11-03
No, I didn't.  I'll give it a try, although needing to reboot?  Bit windows-ish, isn't it?

---

### Post by dbott67 on 2006-11-03
[QUOTE=taurus]If you don't want your harddrives to show up on your desktop, then change the mount points to something else besides the /media[/QUOTE]

I'm not so sure that it is restricted to just the **/media** folder, as I have a shared folder mounted on **/home/dbott/music** that automagically appeared on my desktop.
```
dbott@thedrake:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[COLOR="Red"]//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0[/COLOR]
```
 -Dave

BTW: Dapper 6.06.1

---

### Post by dcherryholmes on 2006-11-13
The reboot seems to have done it.  I've got my shared partitions mounted off of root now, and they aren't showing up on my desktop with "Show volumes" options checked in gconf-editor->apps->nautilus->desktop.

---

