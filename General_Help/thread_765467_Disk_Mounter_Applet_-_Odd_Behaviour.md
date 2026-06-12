---
title: "Disk Mounter Applet - Odd Behaviour"
date: 2008-04-24
forum: General Help
---

### Post by issih on 2008-04-24
In my top gnome panel I have a disk mounter applet. In every version of ubuntu I've used up to now (since edgy), this has merrily ignored the existence of all my random hard disk partitions and has only ever sprung into action when I connected a memory stick/ipod/inserted a cd.

Now I've upgraded to hardy, however, it is showing me all the partitions I have mounted at startup, and also cdrom1 (which is umounted). To confuse matters this cdrom, is not actually the optical drive in my system at all, as sticking a cd in results in an extra device appearing and cdrom1 still being unmounted....

I'm guessing this is probably a change either in fstab/udev or possibly the applet itself, but I'm almost certainly wrong. Does anyone have any idea what might have caused this? it looks very untidy indeed :(

Issih

---

### Post by warjowuch on 2008-04-30
yep, same problem here. Quit annoying. I have searched everywhere (including Gconfig-editor) for entries using /dev/hdc and /dev/hdd (which are not present anymore since hardy's kernel, but still configured in the applet), but couldn't find a relevant item yet.
I reïnstalled my wife's pc this morning, it removed the non-existing drives from the drive-mounter. So the configuration should not be somewhere in /home (I re-used her old home partition).
This is my knowledge up till now.

---

### Post by warjowuch on 2008-05-01
Well well, I solved the thing.
I found out that the drivemounter-applet also uses entries in your /etc/fstab file.
I found out that the non-existent drives in the applet where /dev/hdc and /dev/hdd by trying to mount them. It gave me an error-message saying /dev/hdd (or hdc)  did not exist.

After mounting real cdroms (in my player and burner) I found out these now had devices /dev/sdc0 and /dev/scd1.

So, I looked into my /etc/fstab and uncommented the entries I did not want.
In my case, these specific entries looked like this:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And now look like this:
# /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And immediately after saving this, the unnneeded entries where removed from the applet. Woohoo :-)
I uncommented these entries first, because I want to try it this way. When I am sure it does not do any harm to my computer, I might remove them. But I never know when they come in usefull.
Good luck!

---

### Post by issih on 2008-05-01
I'd got as far as editing fstab to comment out the weird cdrom entry myself (although I too am not 100% sure it won't break something). In my case its actually the 5 other mounted partitions that I have on my system that really annoy me....For some reason when I first configured this pc 4 years ago I made lots of separate partitions on the drives, not really sure why, I guess it seemed like a good idea at the time. I have fstab set up to mount these partitions at boot. Since the upgrade to hardy, the applet shows a little icon for each of these statically mounted partitions..where before only dynamically mounted drives were being shown.

From my searches in the forum, it looks like this is probably a deliberate change in the behaviour of the applet, several people complained that they weren't seeing statically mounted drives when they felt the applet should allow them to see them and mount/unmount them as desired. I guess you can't please all the people all the time :)

For now I have just removed the applet, as it was crowding up my already rather full gnome panel, Hopefully someone will eventually code an applet where you can choose what mounted drives are displayed, rather than being forced one way or another.

Thank you very much for your help

I'm glad you got yours working how you want it :)

---

