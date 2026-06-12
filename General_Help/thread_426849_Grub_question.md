---
title: "Grub question"
date: 2007-04-28
forum: General Help
---

### Post by Imsati on 2007-04-28
I personally love things to be very organized and tidy. That being said, I absolutely HATE  installing KDE over Gnome or Gnome over KDE. So I took my 80G HDD and made a 2 GB shared Swap, 15 GB Ubuntu, 15 GB Kubuntu, and 46 GB shared Home partitions. Ubuntu is 6.06 with the 686 kernel, and Kubuntu is 7.04 generic. My Grub list is super long and I'm not quite sure exactly how to edit it so I can tone it down a bit. I only want it to show Ubuntu 686 (and Recovery mode), Kubuntu (and it's recovery mode), and XP. I've no need for the older Ubuntu kernels or the both memory tests.

Thanks!

--Jay

---

### Post by dizee on 2007-04-28
Edit it by typing 
```
sudo gedit /boot/grub/menu.lst
```
in a terminal, and then comment out or delete the entries you don't want to see. Might be a good idea to back it up first though. Replace "gedit" with "kate" if you're using KDE of course.

---

### Post by fwojciec on 2007-04-28
The first thing would be to use Synaptic to uninstall some old kernels that you no loner use - that's the tidy way of doing it.  I would recommend leaving at least one older kernel as a backup for each partition.

If you want to further trim the list you can manually edit "/boot/grub/menu.lst" file, and comment out/delete the entries you don't want to see.

If you leave older kernels installed but remove them from the menu.lst, they will keep on reappearing in your grub menu whenever the system automatically updates it.  I think there is a way of telling Ubuntu which kernels should/shouldn't be used when updating Grub, but I don't know how to do it - sorry ;)

I hope that helps!

---

### Post by Imsati on 2007-04-29
I uninstalled the old kernels and it seemed to work. Now I have another question that spawned from it, but not grub-related, so I'll make a new post.
Thanks!
--Jay

---

### Post by dondad on 2007-06-28
> **dizee said:**
> Edit it by typing 
```
sudo gedit /boot/grub/menu.lst
```
in a terminal, and then comment out or delete the entries you don't want to see. Might be a good idea to back it up first though. Replace "gedit" with "kate" if you're using KDE of course.


You can run into problems if you use sudo with gedit. Better to use gksudo. (under some conditions, you can lose ownership of your home directory)

---

