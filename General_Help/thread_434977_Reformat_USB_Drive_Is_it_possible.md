---
title: "Reformat USB Drive? Is it possible?"
date: 2007-05-06
forum: General Help
---

### Post by bg1256 on 2007-05-06
Hello, everyone.

I have a 512 MB USB flash drive that is giving me problems.

I've spent the past month or so trying to solve this problem: it has become a read-only file system.

The problem originated when I switched from Gnome to KDE, and I've not had success fixing it.

I've tried several variations of chown and chmod to no avail.

I do'nt have anything valuable on the drive right now, so I'm thinking a reformat may be the best option.

Does anyone know if/how this occurs?

thanks!

---

### Post by bettlebrox on 2007-05-06
>I've tried several variations of chown and chmod to no avail.
You need to change the mount options for the drive.

---

### Post by RudolfMDLT on 2007-05-06
> **bg1256 said:**
> Hello, everyone.

I have a 512 MB USB flash drive that is giving me problems.

I've spent the past month or so trying to solve this problem: it has become a read-only file system.

The problem originated when I switched from Gnome to KDE, and I've not had success fixing it.

I've tried several variations of chown and chmod to no avail.

I do'nt have anything valuable on the drive right now, so I'm thinking a reformat may be the best option.

Does anyone know if/how this occurs?

thanks!

Hi - well, it may just be a faulty drive? or you did you forget it in your pocket and send it through the laundry? I did that once!

If not, then sure, if it's read only, then copy the files off of the thing and open up Qtparted\Gparted and format it FAT32. 

you can also try chmod -R 777 /mountfolder?

Post back with any results. 

Goodluck!

Rudolf

---

### Post by bg1256 on 2007-05-06
Alright...

Sorry for the ignorance, but how do I do that?

Btw, I realized I didn't post I am using Feisty, KDE.

Okay, so I run

```
 chmod -R 777 /meda/'my usb drive'
```

And 

chmod: changing permissions of `/media/myusbdrive/Documents/The Chapel/&#9577;¿i\030r&#9567;\033t.ç0&#9564;': Read-only file system

And it hangs here.

This is where it has been hanging in the past as well.  I've let it run for hours at a time, with no results...

---

### Post by bg1256 on 2007-05-06
Edit:

I successfully reformatted the drive using qtparted; however, when I was messing with the properties, and now the device does not mount automatically.

What could I do to find the mount point and then mount it?

The one thing I know for sure is that the drive is not corrupted, because I was able to read and write to it before I borked it up...

I was just trying to change the name so it appeared with my name on the desktop...oops...

Anyway, is there a command I can run to detect where it is?

---

### Post by strabes on 2007-05-06
lspci | grep usb -i

I had this problem one time and the solution was to change the *label* of the disk. I don't exactly remember how I did this though. Sorry.

---

### Post by bg1256 on 2007-05-07
That's helpful.  It should help me locate the drive, so I can mount it at least. From there, I should be able to adjust the settings I need.

Thanks!

---

