---
title: "editing xorg"
date: 2006-12-10
forum: General Help
---

### Post by solinent on 2006-12-10
sudo dpkg-reconfigure -phigh xserver-xorg

That's what I used to configure my screen resolution.  However, it's outputting at 1024x768 when in reality it should be native: 1280x1024

Now I go through the configuration (two steps) and the first one tells me to select drivers.  I have a nVidia grahpics card, so I chose the one that sounded most like it, and I got it (nv).  If there's a better one please tell me.  Then I tabbed to ok and pressed enter.  After that, there was a bunch of checkboxes telling me what resolutions I support.  This may seem extreme newbish, but I have no idea whatsover how to clear the checkbox.  I tried all the keys...

Can you help me choose the best driver (I heard nv doesn't support 3d?) and how to clear the 1280x1024 checkbox.

Thanks!

---

### Post by riven0 on 2006-12-10
I haven't done a reconfigure in a while, but if I'm not mistaken I think you hit the space bar.

---

### Post by PriceChild on 2006-12-10
> **riven0 said:**
> I haven't done a reconfigure in a while, but if I'm not mistaken I think you hit the space bar.Indeed, space selects, return moves to the next page.

Fooled me when I first started out too :)

---

### Post by majoridiot on 2006-12-10
if you want the best performance, you should be running nvidia's closed
source driver.  you can get it a variety of ways... from automatix or
from nvidia.

nvidia's drivers: [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

(1.0-8776 is what i run and it is very stable on three screens)

---

