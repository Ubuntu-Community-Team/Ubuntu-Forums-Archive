---
title: "Remove an entry from grub"
date: 2007-02-04
forum: General Help
---

### Post by ade234uk on 2007-02-04
I want to be able to remove an entry from Grub.

Grub shows me that I have two versions of windows installed, one of these if selected reinstalls the Laptop to its factory settings. Yuk. 

I have messed my whole installation of Windows and Ubuntu before by selecting this link in the past. So the only thing I can do is remove this entry from the Grub Menu.

Thanks

---

### Post by moshuptrail on 2007-02-04
The grub menu is located at /boot/grub/menu.lst

It should be easy to figure out.  Make a backup copy just in case.

e.g.
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
$ sudo nano /boot/grub/menu.lst

(I had the same problem - I just changed the title)

---

### Post by ade234uk on 2007-02-04
thank you

---

### Post by PurplePenguin on 2007-02-04
This sounds like a good one to just delete... but if you ever want to get something out of the grub menu, you can add # to the beginning of each line and this will make grub disregard it.  Then, later on, if you realize that you want it back, just remove the #s.

---

### Post by Steve H on 2007-02-09
That worked perfectly. I have just  had the new kernel update and had ended up with 2 entries for Ubuntu's normal boot.

I just wanted to tidy up GRUB (as I'm easily confused).

---

### Post by nickoli_02 on 2007-02-09
I'd recommend against removing the windows recovery partition altogether, as if you do this you will be unable to boot into the recovery partition if something happens and you need to reinstall windows. If you really want to remove it from grub's boot options, just do like the previous post suggested and comment it out using #'s before that boot entry. 

A better idea would be to rename the title to something like "Windows Recovery Partition" and moving it to the bottom of grub's boot menu. That way you won't get it confused with XP and you still have it available if you need it ;)

---

