---
title: "Terminal the Only Way to Change Owner?"
date: 2006-10-29
forum: General Help
---

### Post by mwandaw on 2006-10-29
Is there any way to change the owner of a file without using the terminal and sudo chown  ?

Can I do that within GNOME somehow?

Thanks

---

### Post by pay on 2006-10-29
You sure can. ```
gksudo nautilus
``` Then right click the file that you want to chane and go to the permisions tab.

---

### Post by aysiu on 2006-10-29
Note that in Dapper, Breezy, Hoary, and Warty, Nautilus cannot do recursive ownership/permission changes. Those can be achieved only through the terminal or Konqueror.

As of Edgy, Nautilus can do recursive (folders and files within folders) permission/ownership changes.

---

### Post by mwandaw on 2006-10-29
Got it... thanks!

---

### Post by aysiu on 2006-10-29
I don't know if you're using Edgy or not. If you're not using Edgy, and you are using Ubuntu or Xubuntu (not Kubuntu), you'll need to use the terminal to change ownership recursively: ```
sudo chown -R mwandaw:mwandaw /home/mwandaw/*nameoffolder*
```

---

### Post by faithsnathan on 2007-02-07
> **pay said:**
> You sure can. ```
gksudo nautilus
``` Then right click the file that you want to chane and go to the permisions tab.


That sure helped me.  I've been trying to solve a problem I'm having with an external hard drive.  I just bought it and, of course, it's in NTFS with instructions only for Windows 2000 or XP.  So after digging around on the forums, I found out that GParted could at least format the drive to a Linux compatible version (I used ext3).  Well, that made everything only accessible by root only, so I couldn't backup my folders like that.  But after using your suggestion above, it works.

I'm backing it all up so I can try to upgrade to Edgy (and for general good measure, of course) in a fresh install.  That's my next headache ... uh, I mean *adventure* in computing.:lolflag:

---

### Post by aysiu on 2007-02-07
If it's Ext3, you don't need *gksudo nautilus*.

Read more here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

