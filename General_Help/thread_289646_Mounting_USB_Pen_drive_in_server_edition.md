---
title: "Mounting USB Pen drive in server edition"
date: 2006-10-31
forum: General Help
---

### Post by ngms27 on 2006-10-31
Hi,

I'm running a server edition i.e. no GUI and do not know how to mount a usb pen drive. Anyone know how to do this?

Thanks

JonnyT

---

### Post by kidders on 2006-10-31
Hi there,

You should be able to do this the same way as you'd mount anything else. Something like **mount /dev/sda1 /mnt/pendrive** should work for you.

---

### Post by reclusivemonkey on 2006-10-31
> **ngms27 said:**
> Hi,

I'm running a server edition i.e. no GUI and do not know how to mount a usb pen drive. Anyone know how to do this?

Thanks

JonnyT

Firstly you need to find out what the pen drive is being mounted as. Use;

```

sudo tail -f /var/log/messages

```

then plug it in. You will see some messages telling you which device it is. Lets says its /dev/sda. Then, use mount;

```

sudo mount /dev/sda -t auto /pathto/mount

```

Although you may want to just plug the pen drive in and have a look in /media to see if it is already being mounted for you...

---

### Post by maudmoonshine on 2007-10-14
Please forgive me jumping in...

I have a pen-drive that works just fine with 7.04 Desktop and numerous Windows XP machines, but it will simply not work with 7.04 server.

It sees it ok (as a SCSI drive?!) but won't mount it.

The errors I get are:

   FAT: Invalid media value (0xb9)
   VFS: Can't find a valid FAT filesystem on dev sda

i've tried it with auto, vfat and FAT16 none of which work.

Since, as I said, 7.04 desktop has no problem with it (nor countless Windows machines) I don't understand...

Any help appreciated.    I've spent hours on this now and read, literally, hundreds of posts: nothing works!

...

As to my 40gig external USB hard disc 7.04 server does not want anything to do with that either; but I'll leave that for the time being.

---

### Post by kidders on 2007-10-14
> **maudmoonshine said:**
> Please forgive me jumping inNo worries... this thread is from 2006.

> **maudmoonshine said:**
> It sees it ok (as a SCSI drive?!)That's by design.

> **maudmoonshine said:**
> Can't find a valid FAT filesystem on dev sdaThat's also normal. /dev/sda describes a physical device, not one of its filesystems. By typing "mount /dev/sda ...", you are essentially instructing Linux to mount a *partition table*, which (obviously) won't work.

Try **mount /dev/sda1 /mnt/somewhere** instead.

---

### Post by maudmoonshine on 2007-10-14
>  
Try **mount /dev/sda1 /mnt/somewhere** instead. 

 
Thanks; that gives:
 
**cramfs: wrong magic**
**ET3-fs: unable to read superblock**
**FAT: bogus number of reserved sectors**
**mount: you must specify the filesystem type**
 
but when I have done so, over many tests in the last 2 days, it does not like it anyway.
 
What I do not understand is why 7.04 desktop has no problem with mounting this usb pendrive (either a full install or running from a live CD).
 
I've, in the last hour, managed to borrow a Phillips mp3 player which will mount on 7.04 server, although it gives a number (10 just now) of errors all along the line of:
 
**Buffer I/O error on device sda1, logical block [COLOR=black]<so-and-so>[/COLOR]**
 
when initially plugged in; and then the same set of errors when mounted... but it will mount and function.
 
So I can now move files from one machine to another easilly; which is all I wanted to do (to save typing, you know). 
 
[COLOR=blue](It'd have been easier to install GNOME on the server).[/COLOR]

---

### Post by kidders on 2007-10-14
> **maudmoonshine said:**
> Thanks; that gives:
 
**cramfs: wrong magic**
**ET3-fs: unable to read superblock**
**FAT: bogus number of reserved sectors**
**mount: you must specify the filesystem type**Try specifying the filesystem type. Assuming there's nothing wrong with your Linux, that should work fine. (Fingers crossed hehe.)
 
> **maudmoonshine said:**
> What I do not understand is why 7.04 desktop has no problem with mounting this usb pendrive (either a full install or running from a live CD).Hopefully, your current install won't either, but you do have to use the correct arguments in your "mount" command.
 
> **maudmoonshine said:**
> [COLOR=blue](It'd have been easier to install GNOME on the server).[/COLOR]Installing gnome on a server wouldn't be at all advisable, really.

---

### Post by maudmoonshine on 2007-10-15
>  
Try specifying the filesystem type.

 
As I said previously:>  but when I have done so, over many tests in the last 2 days, it does not like it anyway. neither does it like my 40 gig single partition usb hard disc (it thinks it got 4 partitions, for a start, that upsets it somewhat).
 
Thankfully it will mount this Philips mp3 player, so I can now do what I want to do; which does kind of demonstrate my understanding the correct mount arguments (after 3 days of fiddling I could probably wite a book on it).
 
>  
Installing gnome on a server wouldn't be at all advisable, really 

 
;-) better not go there.

---

