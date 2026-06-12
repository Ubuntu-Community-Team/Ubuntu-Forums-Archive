---
title: "How can I reconfigure GRUB to detect a newly installed distro"
date: 2008-04-24
forum: General Help
---

### Post by Canis familiaris on 2008-04-24
Is there a program in Ubuntu which will automatically detect all OS and will append the newly installed OS especially Linux Distributions and append them to GRUB.

---

### Post by ajgreeny on 2008-04-24
Ubuntu is very good at doing this if it is the last linux OS added, but most others will not pick up other linux installations in my experience.  None of them will add windows if you install it after linux, in fact windows will take over the MBR again and you will have to reinstall grub and edit the menu.lst file to include the windows install.  As far as I'm aware there is nothing available to do exactly what you seem to be hoping for.

---

### Post by kpkeerthi on 2008-04-24
There is nothing that I'm aware of. Are you looking for something to [chainload GRUB]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html")s?

---

### Post by Canis familiaris on 2008-04-25
> **ajgreeny said:**
> Ubuntu is very good at doing this if it is the last linux OS added, but most others will not pick up other linux installations in my experience.  None of them will add windows if you install it after linux, in fact windows will take over the MBR again and you will have to reinstall grub and edit the menu.lst file to include the windows install.  As far as I'm aware there is nothing available to do exactly what you seem to be hoping for.

OK Is there a tool like in YAST in SUSE which will automatically redetect all distros and reconfigure GRUB. Even if Windows does not work, it does not matter, I do not use windows anymore,

---

### Post by zvacet on 2008-04-25
@ **Anurag_panda**

If you don´t know on which partition is your other distro then 

```
sudo fdisk -lu
```

Now when you know where it is add it to the grub,but first back up menu list

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

edit menu list

```
gksudo gedit /boot/grub/menu.lst
```

find this line 

### END DEBIAN AUTOMAGIC KERNELS LIST

Below this line you wil add new distro and you can use link  **kpkeerthi ** posted and use it to add new distro to the grub.Save file and close it.

---

