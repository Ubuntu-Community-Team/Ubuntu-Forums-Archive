---
title: "How to find large files"
date: 2007-01-05
forum: General Help
---

### Post by GrumpyBob on 2007-01-05
I'm running Edgy on an IBM Thinkpad R52.  My home folder is on /dev/sda3, which is a 19.9Gb partition.  Just recently I've been suffering from "disk full errors".  Using System Monitor to check on how full the drives are, I see that of the 19.9Gb, only 1.7GB is free, 665.8Mb available.  I went through the drive a few days ago, and manually removed large files to a USB drive, and ended up freeing up 20% of the drive.  Now it's pretty much gone again.

Can anyone suggest how best to find large files or folders (including hidden files/folders) - it may be that some app is writing data to a file or folder somewhere on the drive.

Robert

---

### Post by Ramses de Norre on 2007-01-05
```
du|sort -nr|less
```
Or [baobab](http://www.marzocca.net/linux/baobab.html) for a gui.

---

### Post by ffi on 2007-01-05
> **GrumpyBob said:**
> I'm running Edgy on an IBM Thinkpad R52.  My home folder is on /dev/sda3, which is a 19.9Gb partition.  Just recently I've been suffering from "disk full errors".  Using System Monitor to check on how full the drives are, I see that of the 19.9Gb, only 1.7GB is free, 665.8Mb available.  I went through the drive a few days ago, and manually removed large files to a USB drive, and ended up freeing up 20% of the drive.  Now it's pretty much gone again.

Can anyone suggest how best to find large files or folders (including hidden files/folders) - it may be that some app is writing data to a file or folder somewhere on the drive.

Robert
If you use KDE there is a very handy function in Konqueror which will give you a graphic representation of all files and folders according to size, it's called filesize view and can be selected from view

---

### Post by GrumpyBob on 2007-01-05
> **ffi said:**
> If you use KDE there is a very handy function in Konqueror which will give you a graphic representation of all files and folders according to size, it's called filesize view and can be selected from view

Blimey, what a rapid response from the forum.  Unfortunately I'm using gnome - but I might give baobab a go...

I ran 

 find /home/robert/ -size +10240000c -exec du -h {} \;

and in the output it would seem that beagled is the principal space hog:
789M	/home/robert/.beagle/Log/2007-01-04-16-46-37-Beagle
22M	/home/robert/.beagle/Log/2006-12-31-10-54-38-Beagle
21M	/home/robert/.beagle/Log/2006-12-31-10-54-38-BeagleExceptions
825M	/home/robert/.beagle/Log/2006-12-31-13-10-51-Beagle
453M	/home/robert/.beagle/Log/2007-01-02-19-30-52-Beagle
430M	/home/robert/.beagle/Log/2007-01-02-19-30-52-BeagleExceptions
2.6G	/home/robert/.beagle/Log/2007-01-03-04-55-02-Beagle
749M	/home/robert/.beagle/Log/2007-01-04-16-46-37-BeagleExceptions
419M	/home/robert/.beagle/Log/2007-01-05-05-48-41-Beagle
406M	/home/robert/.beagle/Log/2006-12-29-11-48-22-Beagle
386M	/home/robert/.beagle/Log/2006-12-29-11-48-22-BeagleExceptions
995M	/home/robert/.beagle/Log/2006-12-30-14-41-40-Beagle
945M	/home/robert/.beagle/Log/2006-12-30-14-41-40-BeagleExceptions
783M	/home/robert/.beagle/Log/2006-12-31-13-10-51-BeagleExceptions
2.4G	/home/robert/.beagle/Log/2007-01-03-04-55-02-BeagleExceptions
398M	/home/robert/.beagle/Log/2007-01-05-05-48-41-BeagleExceptions
42M	/home/robert/.beagle/Indexes/FileSystemIndex/PrimaryIndex/_t7m.cfs
14M	/home/robert/.beagle/Indexes/FileSystemIndex/FileAttributesStore.db
14M	/home/robert/.beagle/Indexes/EvolutionMailIndex/PrimaryIndex/_6iw.cfs

Is it safe to delete these?  Will beagle just do it again?  I have beagled in my startup session list.

Robert

---

### Post by ffi on 2007-01-05
I don't use beagle but with files this big I would certainly have deleted them, if I had used it.

But I guess the worse that could happen would be that you would loose your searches and beagle would have to reindex. Maybe there is a setting to prevent those log etc. from growing so big. Try deleting ~/.beagle/Log first and don't forget to empty the trash...

---

### Post by GrumpyBob on 2007-01-05
I think I found the solution here:
[http://ubuntuforums.org/showthread.php?t=321654&highlight=beagled](http://ubuntuforums.org/showthread.php?t=321654&highlight=beagled)

(the log files totalled 12.7Gb!)
Robert

---

### Post by GrumpyBob on 2007-01-19
> **GrumpyBob said:**
> I think I found the solution here:
[http://ubuntuforums.org/showthread.php?t=321654&highlight=beagled](http://ubuntuforums.org/showthread.php?t=321654&highlight=beagled)

(the log files totalled 12.7Gb!)
Robert

No, that's still not helping, beagle is still accumulating huge log files.
Can anyone recommend a solution?  Otherwise I shall get rid of Beagle.

Robert

---

### Post by kerry_s on 2007-01-19
How often is it making logs? Maybe a hourly cron job to delete it would help. You could also link log to /dev/null, which is like sending it straight to the trash(deleted)

sudo gedit /etc/cron.hourly/clear-log
put
#!/bin/sh
rm -r /home/robert/.beagle/Log

save and make it executable

chmod +x /etc/cron.hourly/clear-log

or

to make it delete automatically

ln -s /dev/null /home/robert/.beagle/Log


Also if you want you can delete /usr/share/doc and /usr/share/man which usually takes up alot of space but is rarely used, i usually use the on line man and doc pages.

---

### Post by David Corrales on 2007-01-19
If you're using Edgy, use Accesories/Disk usage analizer.

---

### Post by GrumpyBob on 2007-01-22
> **kerry_s said:**
> How often is it making logs? Maybe a hourly cron job to delete it would help. You could also link log to /dev/null, which is like sending it straight to the trash(deleted)

sudo gedit /etc/cron.hourly/clear-log
put
#!/bin/sh
rm -r /home/robert/.beagle/Log

save and make it executable

chmod +x /etc/cron.hourly/clear-log

or

to make it delete automatically

ln -s /dev/null /home/robert/.beagle/Log


Also if you want you can delete /usr/share/doc and /usr/share/man which usually takes up alot of space but is rarely used, i usually use the on line man and doc pages.

The easiest solution would be to get ride of beagle, I think.  I don't search for files very often anyway.  The huge beagle log file issue seems quite widespread judging from a quick  web search.

Robert

---

### Post by GrumpyBob on 2007-01-29
> **GrumpyBob said:**
> The easiest solution would be to get ride of beagle, I think.  I don't search for files very often anyway.  The huge beagle log file issue seems quite widespread judging from a quick  web search.

Robert

Right, I've just deleted another pair of 1.9Gb log files.  The time has come to ditch Beagle.  Are there any likely problems associated with doing this?

Robert

Edit 1st feb 07 - I removed beagle last week using synaptic, then reinstalled it.  This time I didn't install the beagle-backend-evolution package.   So far beagle hasn't been generating those vast log files, and those it does generate seem to have a fairly rapid turnover.

---

