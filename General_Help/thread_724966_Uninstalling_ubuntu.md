---
title: "Uninstalling ubuntu"
date: 2008-03-15
forum: General Help
---

### Post by ftpvk on 2008-03-15
I just completely messed up my ubuntu 7.10  (don't ask). I have vista installed on the same laptop and I have a seperate disk partition for ubuntu. My laptop came with vista installed, so I do not have the cd. How do I unistall ubuntu completely and get rid of Grub. In other words - resotore it to the time when I only had vista?

Can I go into disk managment, delete the ubuntu volume and extend my vista one?

Thanks for the help

---

### Post by oldb0y on 2008-03-15
You can fix MBR(Master Boot Record) with [Super Grub Disk](http://supergrub.forjamari.linex.org/). After that you boot regularly into Vista and delete the Ubuntu-partition and extend your Vista-partittion.

---

### Post by ftpvk on 2008-03-15
Okay, but do I uninstall Grub?

---

### Post by gfg on 2008-03-15
> **ftpvk said:**
> Okay, but do I uninstall Grub?

Yes by doing what's suggested you will uninstall/remove grub.

---

### Post by ftpvk on 2008-03-15
If I uninstall Grub, will the windows loader appear, or will there just be no loader?!

---

### Post by sandysandy on 2008-03-16
> **ftpvk said:**
> If I uninstall Grub, will the windows loader appear, or will there just be no loader?!

u will first have to restore windows MBR. 

after restoring windows MBR check that u can boot into windows properly.

after that only should u delete the ubuntu partition.

[COLOR="Blue"]to help u do[/COLOR] that please have a look at these links

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

[http://ubuntuforums.org/showthread.php?t=475281](http://ubuntuforums.org/showthread.php?t=475281)

[http://ubuntuforums.org/showthread.php?p=2728880](http://ubuntuforums.org/showthread.php?p=2728880)

regards

---

### Post by ugm6hr on 2008-03-16
I would suggest using EasyBCD:
[http://ubuntuforums.org/showpost.php?p=2668386&postcount=14](http://ubuntuforums.org/showpost.php?p=2668386&postcount=14)

After installing EasyBCD, then delete the Ubuntu partitions and extend the Vista partition (from within Vista).

---

### Post by ftpvk on 2008-03-16
that worked perfectly, thanks!

---

