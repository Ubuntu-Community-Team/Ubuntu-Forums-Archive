---
title: "Ack! I broke automount!"
date: 2008-02-02
forum: General Help
---

### Post by shaggy999 on 2008-02-02
Ok, so I was trying to change the default location where a usb drive mounts to when I mount it. It previously mounted as /media/disk. I right-clicked the icon and clicked on the Volume tab and clicked "Settings". I changed the mountpoint option to "/media/maxtor", then I unmounted the drive and unplugged it. But when I plugged it back in I get this error:

Cannot Mount Volume. Details mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /).

But now I have no way to change it because I previously changed it by right-clicking the mounted icon!!! Can anybody help?

---

### Post by shaggy999 on 2008-02-02
Ok, so I'm only partially stupid. I figured out I can just right-click the unmounted volume in nautilus to get back to the properties page... but how do I set up the mountpoint? It makes no sense that I can't include a / in the mountpoint. Perhaps I have to use an escape character of //? Any help appreciated!

---

### Post by shaggy999 on 2008-02-02
Ok, looks like I fixed it and realized a limitation of automount. I changed /media/maxtor to just maxtor and it mounted to /media/maxtor, so I'm thinking the automounter is hard-coded to mount to the /media directory and you can only define the subdirectory/link name.

---

### Post by noah.bronstein on 2008-02-03
After you broke it, how did you edit the auto mount point?  I am having the exact same problem, but do not see how to edit that again.

Thanks.

---

### Post by noah.bronstein on 2008-02-03
Ah, I fixed it.

I had to run gconf-editor

and then navigate to System->Storage

And then change the options under both drives and volumes from attempting to mount at "/media/whatever" to "whatever".

Exit gconf-editor and then everything works again.

---

### Post by shaggy999 on 2008-02-03
I found an easier way to do that. I went to Places -> Computer which brought up nautilus showing all my drives on my system *regardless of whether they were mounted or not*! By right-clicking the appropriate drive I got the same tabbed properties panel that you get when you right-click->properties on a mounted drive.

---

### Post by VanHammersly on 2008-04-09
Thanks Noah.  That's what I needed to fix mine.

---

