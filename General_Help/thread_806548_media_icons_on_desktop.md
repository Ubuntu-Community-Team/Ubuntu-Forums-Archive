---
title: "media icons on desktop"
date: 2008-05-25
forum: General Help
---

### Post by eggman jr. on 2008-05-25
First, here's the relevant line from my /etc/fstab:
/dev/sdb1   /home/vidars/media   xfs     defaults   0 2

What I want is for this drive to mount without showing its icon on the desktop, but for removable media to still show up. This worked in all previous releases, until I upgraded to Hardy. I have tried other mount points, without success...

---

### Post by eggman jr. on 2008-05-25
So I found [this]("http://gnomesupport.org/forums/viewtopic.php?t=11831"), but all that happened was that the icon changed name from "300G Media" to "media"

---

### Post by lswest on 2008-05-25
type ```
gconf-editor
``` in the terminal and go to apps-->nautilus-->desktop and uncheck volumes_visible (it will remove the icon for all external media i believe)

---

### Post by eggman jr. on 2008-05-27
That's not what I want, I want the pre-Hardy behavior back, where external media would show on the desktop, and this particular permanently mounted, internal SATA-drive would *not* show.

---

