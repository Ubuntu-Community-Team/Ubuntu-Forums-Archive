---
title: "Multiple Hard Drives"
date: 2006-11-02
forum: General Help
---

### Post by dontgetshocked on 2006-11-02
I have a raid setup which right now only uses 1 80gig hd. My questions is, if i add another drive to it as striped as one, will ubuntu freak out?

---

### Post by matthewstory on 2006-11-03
interesting question . .. well if you'll have to tweak grub, to tell it that the default boot disk is mdX and not hdaX, and add multiple boot options on the menu.lst file for each disk, as well as creating a new initrd file to have it initialize properly with the raid device, and then use the grub terminal to configure the raid device properly.  If all this is done, then no, Ubuntu won't freak out . . . see this howto:

[http://xtronics.com/reference/SATA-R...n-for-2.6.html](http://xtronics.com/reference/SATA-R...n-for-2.6.html)

---

