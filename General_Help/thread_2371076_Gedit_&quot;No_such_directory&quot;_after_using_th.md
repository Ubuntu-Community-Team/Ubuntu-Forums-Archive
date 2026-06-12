---
title: "Gedit &quot;No such directory&quot; after using thumb drive"
date: 2017-09-10
forum: General Help
---

### Post by eylrid on 2017-09-10
I opened some files from a thumb drive in gedit, used them, closed them, and ejected the thumb drive. Now when I open gedit it comes up with a message "An error occurred while loading directory: Error opening directory '/media/myname/UUI/directory/path': No such file or directory"

How do I stop this message from appearing every time I open gedit?

Ubuntu version: 16.04.3
gedit version: 3.18.3

---

### Post by Bashing-om on 2017-09-10
eylrid; Hello - Welcome to the forum :

When you say 
> 
closed them, and ejected the thumb drive.

 is that physically pushed the eject button ?

If you did not unmount/eject from the GUI file manager ( or Umount from terminal ) then the file system was left in an inconsistent state - the file system was left open while awaiting the flush of cache to the device .

So, we looking at repairing a file system ??
What then is the file system on the thumb drive ?
With the thumb drive connected show the output of terminal command - Between Code Tags, please -
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See then what we can do .
 

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

