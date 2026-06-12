---
title: "keep grub"
date: 2007-06-11
forum: General Help
---

### Post by dracule on 2007-06-11
Sorry but I have searched and searched and I know this has been asked many many times before but all i can find is how to uninstall grub with ubuntu.

what i want to know is if i simply format my ubuntu partition, if grub will still function correctly. the reason i ask is that the etc/boot/grub (i think that that is it) is on the ubuntu partition so i have no idea if it will screw it up.

again sorry but the search is kinda bad and keeps coming up with unrelated thread

---

### Post by kevinlyfellow on 2007-06-11
It will not function correctly unless there is a separate boot partition.  BTW its /boot/grub.  So if /boot is on a different partition, you will be ok.

---

### Post by dracule on 2007-06-11
all i will have is windows and soon 10.4 (why i want to keep grub) so can i make it C:/boot? or will that not work?

---

### Post by kevinlyfellow on 2007-06-11
Sorry, I'm a bit confused.  10.4?  If you want to completly remove grub (which you may as well do if you want to run windows or completly reinstall a new linux os) then just restore the windows mbr (master boot record).  [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s05.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s05.html)

Oh, and moving the files in /boot over to c:\boot on your windows partition will not work.

If your dying to keep grub at all costs, I suggest making a separate boot partition and just installing grub on that.

---

