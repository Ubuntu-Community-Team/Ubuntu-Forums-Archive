---
title: "Change name of partitions"
date: 2008-04-25
forum: General Help
---

### Post by Yellowbelly on 2008-04-25
All previous ubuntu versions had my drives or partions labeled but now they're labeled by the size they are which is super confusing to me and completely illogical as they'll change kinda frequently. At least when it was labeled hdb1 or something, I new exactly what that was but I have 2 ~100 gb drives and I don't know which one's which. Can I relabel it in the fstab easily?

---

### Post by natrixgli on 2008-04-25
Hi, 

Check out [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

If you want to rename your root partition, you will likely need to use a LiveCD to do so.

Cheers,

-n8

---

### Post by verbage on 2008-04-25
Yellowbelly, I have noted the same thing as well.  Basically, it seems to be a change in the default naming convention of mounted partitions.  Before (well, using Ubuntu 7.10), Gnome used the device name as the automatically chosen name for mounted volumes, for example, "sda1" or "sda4".  Now it puts up the size of the volume, for example, "41.9 GB Media".  If you have your hard disks carved up into various partitions of equal size (like I do, several 40 GB partitions for different OSes), well, this new naming convention is obviously frustrating, and it would be great to be able to revert back to the former naming convention (i.e. based on device names).

I have hunted around in gconf-editor etc., but did not find any obvious options for this.

Also, for cross-reference, please note that this same issue/question was pointed out a few days ago in the following thread:

[http://ubuntuforums.org/showthread.php?t=762508]("http://ubuntuforums.org/showthread.php?t=762508")

Anyway, does anybody know how to have Gnome revert to the former behavior of using the device name for mounts instead of the volume size?

Thanks in advance for your help.

---

### Post by rbmorse on 2008-04-25
The disk command e2label might help here. The syntax (in a terminal window)

sudo e2label /dev/device *newlabel*

i.e.,

sudo e2label /dev/sda1 sda1 

would give the label sda1 to the partition /dev/sda1 and Nautilus should show that under *places*.

---

### Post by verbage on 2008-04-25
Thanks, **rbmorse**, for the suggestion.  I should have mentioned in my first post that I realize I could work around the issue by applying a label as you have suggested, but that would actually require modifying the disk (albeit just the label) which I personally don't want to do.  I'd rather just be able to revert to the former behavior of Gnome using the device name instead of the size like it does now in 8.04.  So I'll keep the labeling option option as a last resort, but maybe in the meantime somebody intimately familiar with Gnome would be able to point an actual config setting to revert to the former behaviour.

---

### Post by verbage on 2008-04-25
I've been doing a bit more research about this issue.  Here are some related links.  In some cases, the links reference issues back to 2006 after which point the issue seemed to be cleared up only to reappear again in Hardy (see Bug #190366 which is apparently current).  At least that's my interpretation, but Gnome/Ubuntu experts, please feel free to set me straight.

Whatever the case, it does appear to be a confirmed bug (#190366) as can be seen in the link below, but it is given a low importance rating.

Here are the links to the current bug and supposed behavior:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/190366")
[https://wiki.ubuntu.com/DesktopVolumesRepresentation]("https://wiki.ubuntu.com/DesktopVolumesRepresentation")


Here are historical links that appear to be related:

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016197.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016197.html")
[https://launchpad.net/ubuntu/+source/nautilus/+bug/30867]("https://launchpad.net/ubuntu/+source/nautilus/+bug/30867")
[https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/38764]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/38764")

---

### Post by Yellowbelly on 2008-04-25
That's seriously bullcrap. How is this low importance? I have to click on my drives for music players to read my library:

[img]http://img146.imageshack.us/img146/9771/screenshotgn0.jpg[/img]

As you can see, my drives aren't labeled at all according to the library. When I first got to this window, none of the drives were there. I clicked on each of them in Places and one by one they started showing up in the amarok menu thing. And the drives aren't recognized every time I restart too. I've had weird problems with gutsy but i'm pretty sure it was due to a bad burn. But I burned this as slow as it'd go so I don't think that's the fault here.

And here's my fstab that should have 3 more drives on it:






# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=17c53f8b-70da-4d01-bed6-36ae253a2fa1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=a4ff4758-3a44-4029-a131-a60fe9709edc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Awalton on 2008-04-29
> How is this low importance?
Because it's not a real security risk, it's not a crash, and it's an additional feature, albeit a sorely missed one for a set of users. Features like this are usually wishlist items, but seeing as this is a slight regression (I should rather say "change in behavior"; not all changes are regressions unlike many people believe), it's promoted from wishlist to low. This of course is my reasoning, but it seems pretty well supported under [https://wiki.ubuntu.com/Bugs/Importance](https://wiki.ubuntu.com/Bugs/Importance).

Right now, we get the names for media from HAL, HAL gets them from the volume's label, with a fallback of "%s Media" where %s is the media's human readable size when the volume label isn't set, end of story. We have an open bug about implementing it the way Ubuntu wants ([https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/190366](https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/190366)), but nobody has stepped up to do the work (I could... but I'm way too busy as it is, and it really is of extremely low importance to me because I set my drive labels, and in the interest of sanity I'd advise you do the same).

Per AmaroK seeing nothing but mount paths, that's an AmaroK (Qt?) issue, not at all a GNOME one. Mount paths are hideously evil, especially in file selectors. If you've got a lot of USB drives and they're mounted at differing times, they dance around like little devils, making you play "guess the mount point" games, instead of choosing the same mount point based on drive UUIDs (this, of course, is probably bug-worthy too, but I digress). Of course I have no knowledge at all of how [Qt] picks locations or how it interacts with HAL, you'll have to ask one of their developers about that.

If anyone wants to do the work on this, it's the GIO-Hal module, located here:
[http://svn.gnome.org/viewvc/gvfs/trunk/hal/](http://svn.gnome.org/viewvc/gvfs/trunk/hal/) 
grab a copy with SVN, fix it up, send us patches. Should be a great bug to fix for a beginner (knowledge of C required of course). If you've got questions, Freenode (#ubuntu-devel usually) or GimpNet IRC (#nautilus always), I'm usually there to answer them. And the GVFS mailing list ([http://mail.gnome.org/mailman/listinfo/gvfs-list](http://mail.gnome.org/mailman/listinfo/gvfs-list)) if nobody's around or to get your patch reviewed by more developers. 

Or barring all of that you could always attempt to bribe me to do it one of these days when I have time... I'm a fan of chocolate ;)

---

