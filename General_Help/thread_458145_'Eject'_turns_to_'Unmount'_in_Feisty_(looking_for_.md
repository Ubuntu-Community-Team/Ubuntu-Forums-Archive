---
title: "'Eject' turns to 'Unmount' in Feisty (looking for a workaround)"
date: 2007-05-29
forum: General Help
---

### Post by arsenic23 on 2007-05-29
I use a 500gig external Sata/USB hard drive for most of my work.  It has three partitions on it an ext3 / of another system, an ext3 storage partition, and a small ntfs partition for windows installer/iso storage.  In all versions of Ubuntu prior to Feisty that I've used right clicking on one of the mounted volumes on my desktop and choosing 'Eject' would unmount all of the partitions and spin down the drive, pretty much turning it off.  I really loved being able to do this as hitting the power switch on my enclosure is pretty much like pulling the plug on the drive.

Now in Feisty I can unmount the volumes one at a time, or all at once (by highlighting them), but I don't know how to tell my USB drive to spin down.  Is there a terminal command or script or anything I can use to do this with the version of Gnome that's running on Feisty?

---

### Post by kerry_s on 2007-05-29
in nautilus you can right click the drive and unmount/eject the whole drive.

---

### Post by arsenic23 on 2007-05-29
When I open Nautilus I see disk, disk-1, and disk-2, which are the 3 partitions on the drive.  I can unmount them sucsussfully, but the drive still does not spin down.  Is there someplace other then the desktop and the location I show in this screenshot that your talking about?

[[IMG]http://img504.imageshack.us/img504/6954/screenshotnj3.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=screenshotnj3.jpg)

---

### Post by dexter on 2007-05-29
Go to Computer in nautilus, there you should see the disk, not the partitions. Try unmounting/ejecting it there.

---

### Post by BLTicklemonster on 2007-05-29
My problem is pretty much the opposite. 

I have a sony camera, and when I attach it to the computer with the usb cord, then go to turn off the camera, I get a message saying that I just did a no no. But if I go to the icon to kill the drive, the only option is eject, which does not work. Unmount is not an option. I know I'm not hurting anything by just turning the camera off, so it's no big deal, but I'd like to know how to do this properly anyway.

---

### Post by arsenic23 on 2007-05-29
> **dexter said:**
> Go to Computer in nautilus, there you should see the disk, not the partitions. Try unmounting/ejecting it there.

Nope and nope.  As you can see in the included screenshot I do not see the disk there, just the three individual partitions.  Also right clicking them gives me the exact same results as rightclicking them on the side of a Nautilus window or on the desktop.  All I can do from the gui seems to be to unmount thme and leave the drive running.

Thanks for the sugestion though, I don't think I've ever used the computer:/// in Nautilus.

[[IMG]http://img253.imageshack.us/img253/4888/screenshotei9.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=screenshotei9.jpg)

So lemme ask again.  Does anyone know a way to spin down a USB hard disk?

---

### Post by clem-vangelis on 2007-05-30
here is the solution to spin down your hardrive :
[PHP]sdparm --command=stop /dev/foo    [/PHP]
 if it's recognized like a scsi disk ( sudo aptitude install sdparm )
and for ide
[PHP]hdparm -y /dev/foo[/PHP]
of course replace foo by your harddrive node
you can additionnaly use this script to spin down your harddrive after unmounting it (zenity required ):
[PHP]
#!/bin/sh
#wait for mtab to be updated
sleep 5
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/foo' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
#we can spindown the hardrive
sdparm --command=stop /dev/foo  #or hdparm -y /dev/foo
zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi
[/PHP]

---

### Post by arsenic23 on 2007-05-30
Thanks alot, I was unaware of sdparm.  It does the trick nicely.  I can even spin down the drive wihle leaving it mounted without causing problems, which is pretty awsome.

---

