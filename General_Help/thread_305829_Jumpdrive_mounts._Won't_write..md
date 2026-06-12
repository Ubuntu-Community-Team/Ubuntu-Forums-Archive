---
title: "Jumpdrive mounts. Won't write."
date: 2006-11-24
forum: General Help
---

### Post by Roasted on 2006-11-24
I can put things on my jumpdrive without any issues. I've tried copying/pasting, flat out dragging and dropping, and also used a sudo mv command in terminal to move the file to the jumpdrive.

Everytime it transferred over, I got no error. If I unplugged the jumpdrive and plugged it back in, the file I JUST wrote to it was gone.

I tried this with two jumpdrives. Each had the same issue.

Why?

---

### Post by brianC on 2006-11-24
I was having the same problem. After you transfer the file, right click on the drive icon and click eject, works for me

---

### Post by futz on 2006-11-24
> **brianC said:**
> After you transfer the file, right click on the drive icon and click eject, works for me
Eject == unmount. Unmounting flushes buffers, forcing any unwritten data in the buffer to be written before the device is unmounted.

Unix/Linux is funny that way. At least for removable drives/devices, unless you set it up differently, it buffers data until the buffer is full before turning on the drive and writing it.

I learned that the hard way back in the 80's with floppies. Lost some data. Much confusion ensued. :mrgreen:

---

### Post by Roasted on 2006-11-24
Oh wow. Imagine that. Thanks!

---

### Post by futz on 2006-11-24
You can fix the confusion easily enough for the floppy by specifying the "sync" mount option in your fstab file instead of "async"

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
> sync and async How the input and output to the filesystem should be done. sync means it's done synchronously. If you look at the example fstab, you'll notice that this is the option used with the floppy. In plain English, this means that when you, for example, copy a file to the floppy, the changes are physically written to the floppy at the same time you issue the copy command.

However, if you have the async option in /etc/fstab, input and output is done asynchronously. Now when you copy a file to the floppy, the changes may be physically written to it long time after issuing the command. This isn't bad, and may sometimes be favorable, but can cause some nasty accidents: if you just remove the floppy without unmounting it first, the copied file may not physically exist on the floppy yet!

async is the default. However, it may be wise to use sync with the floppy, especially if you're used to the way it's done in Windows and have a tendency to remove floppies before unmounting them first.

But how to do it for USB sticks I don't know offhand. I'm sure it's not too difficult.

I tend to do the same as most people - write the file and grab the stick out of the socket. Carry it over to the other box, plug it in and... hey! Where's the file? Oh ya. Damn!

The sync option would make that work. Just gotta get it set up.

---

### Post by futz on 2006-11-24
Now **this** is interesting:
[http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

Maybe I'll just leave well enough alone for now...

---

