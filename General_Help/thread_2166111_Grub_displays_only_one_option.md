---
title: "Grub displays only one option"
date: 2013-08-07
forum: General Help
---

### Post by futura2000 on 2013-08-07
I'm using Ubuntu 10.04 and grub 1.98

The boot menu only displays this Ubuntu installation.

/dev/sda4 is a openSUSE 11.3 install.

Gparted : 
[[IMG]http://s14.postimg.org/idaaqyvtp/screenshot22.jpg[/IMG]]("http://postimg.org/image/idaaqyvtp/")

Also tried ***sudo update-grub*** but with no results. Still after reboot got the same boot options.

Don't know how to go on from this point. 
Thank you

---

### Post by oldfred on 2013-08-07
Another thread. 

You may be able to copy the entry this user had in his bootinfoscript into your 40_custom and update with your drive, partition and UUID.
       [http://ubuntuforums.org/showthread.php?t=1740690](http://ubuntuforums.org/showthread.php?t=1740690)

---

