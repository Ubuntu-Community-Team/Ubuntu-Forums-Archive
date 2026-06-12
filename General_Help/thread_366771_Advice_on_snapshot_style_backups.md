---
title: "Advice on snapshot style backups"
date: 2007-02-21
forum: General Help
---

### Post by arekun81 on 2007-02-21
Hello,

I'm relatively new to Linux but I've read that backing up your system is as easy as copying the folders in the root directory (as root user) and restoring your system is as easy as copying them back (also as root user).

I tried this not too long ago -- using **sudo nautilus**, I copied the contents of the root folder to an external USB hard disk.  Later I copied them back using the same graphical interface and rebooted.  However, I must have done some things wrong, because when the reboot finished I couldn't use my user password with sudo or gksu, and I seemed to have lots of problems with permissions.

I want to do this the right way, because it would be a great way for me to really learn Linux if I could mess around with things and still be able to restore back to a working configuration.

This time, I am going to use **rsync** to do the backup/restore.  Here is the command I will use to do the backup...

```
sudo rsync -a --delete --exclude="/media/" (more exclusions as needed) / /media/usbdisk/ 
```

**I'd like everyone's advice on which folders in the root directory I should exclude.**  I'm still learning the purpose of each of these folders, and obviously I don't want to waste space on my USB drive with folders and files that are temporary or virtual.

The only folder I'm 100% certain should be excluded is **/media/**, since that folder contains my mounted USB disk, which would cause a self-referencing backup.  It would also copy the contents of any other external storage media I had connected at the time.

But what about the other folders??

**/dev/** -- I know this folder contains ISO images of my hard disks & CD drive, which I certainly don't want to copy.  But will I lose other device settings if I exclude this folder?

**/mnt/** -- I don't know what the purpose of this folder is, since my mounted drives always show up under /media/.  It's also always empty.  Should I exclude it?
[B]
/proc/[/B] -- I think this folder contains processes that are currently running in memory.  If that's true, it should be excluded, right?
[B]
/sys/[/B] -- I don't know the purpose of this folder, but I've read here and there that it should be excluded.  Is this true?  Again, I don't want to lose any settings.

**/tmp/** -- Does this stand for "temporary"?  If so, this should be excluded, right?
[B]
/initrd/ /lost+found/ /opt/ /srv/[/B] -- Don't know what these folders are for, but it seems like they are always empty.


Lastly, I wonder if using rsync's -a (archive) argument will take care of all of this anyway, since it apparently handles symbolic links (which I also don't fully understand).

Thanks everyone for your attention.
Alex

---

### Post by arekun81 on 2007-02-28
NO ONE has any advice for me??

Surely there is someone out there who can explain the Linux directory structure to me.

And surely someone performs backups of their system.

---

### Post by tanguyr on 2007-03-06
Hello,

You could try something like this:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

/t

---

