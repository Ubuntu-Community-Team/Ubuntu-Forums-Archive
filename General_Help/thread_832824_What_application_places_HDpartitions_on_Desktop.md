---
title: "What application places HD/partitions on Desktop?"
date: 2008-06-18
forum: General Help
---

### Post by CD Baric on 2008-06-18
Here is what my /etc/fstab looks like:

/dev/sda3   /               ext3    relatime,errors=remount-ro   0   1
/dev/sdb2   /media/data     xfs     relatime                     0   2
/dev/sdc1   /media/disk-1   ext2    relatime                     0   2
/dev/sdd1   /media/disk-2   ext3    relatime                     0   2
/dev/sda4   /media/movies   xfs     relatime                     0   2
/dev/sda2   /media/tv       ext3    relatime                     0   2
/dev/sda1   /media/xp       ntfs    defaults,umask=007,gid=46    0   1

Here is what my /media looks like:

data
disk-0
disk-1
disk-2
movies
tv
xp

Here is what my Desktop looks like:

 [--  ]
316.0 GB

 [--  ]
300.1 GB

 [--  ]
200.0 GB

 [--  ]
 81.8 GB

 [--  ]
 81.8 GB

 [--  ]
 74.6 GB

 [--  ]
 77.0 GB

See the problem? Even though all the HDs and partitions are named, they are presented on my Desktop as anonymous storage capacities.

I want to know what utility presents this crap on my Desktop so I can change it.

Incidentally, Feisty Fawn presented the HDs/partitions BY THEIR NAME!

Thanks for your help,

CD Baric

---

### Post by sdennie on 2008-06-18
Hardy no longer uses the mount point as the name but the partition label as the name.  You have three options:

1) Completely remove the mount points from the desktop.  To do that, hit Alt-F2 and type "gconf-editor".  Then navigate to /apps/nautilus/desktop and turn off all the "visible" options.

2) Change /etc/fstab to mount things outside of /media (for instance /mnt).  Gnome won't automatically place those on your desktop so, you can make symlinks to them with whatever name you like.

3) Rename your partitions to have more pleasing names.  It looks like you have a mix of partitions types so, you will probably need this guide: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) (don't let the name mislead you, it's the right thing to do).  You'll have to reboot before those changes are reflected.

---

### Post by CD Baric on 2008-06-20
Thank you vor for your prompt reply. Please excuse my late reply in turn.

I read your choices with interest and reviewed the page instructing me on how to rebadge all my partitions/HDs.

I read you stated that Hardy no longer supports mount point names.

All I can say is that is Just Plain Stupid - whose idea was that?

What possible benefit could there be to this change?

Who is responsible for this stupidity?

I appreciate change, even difficult change, when there is a reasonable positive side but this is just plain STUPID!

CD Baric

---

