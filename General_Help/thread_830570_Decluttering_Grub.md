---
title: "Decluttering Grub"
date: 2008-06-15
forum: General Help
---

### Post by jus71n742 on 2008-06-15
I recently upgraded to Ubuntu 8.04 and I noticed that grub suddenly has 3 mem tests' 3 kernels and 2 safe  modes. How would I clean this up a bit and return it to the original clean kernel, mem test, and safe mode?

---

### Post by iaculallad on 2008-06-16
> **jus71n742 said:**
> I recently upgraded to Ubuntu 8.04 and I noticed that grub suddenly has 3 mem tests' 3 kernels and 2 safe  modes. How would I clean this up a bit and return it to the original clean kernel, mem test, and safe mode?

You can remove those items by opening your menu.lst file:

Create a backup first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Open file for editing:

```
gksudo gedit /boot/grub/menu.lst
```

and delete/comment it (placing # before the line of text) the unecessary "mem test", "kernels", and "safe mode" things. Save file and do a restart to see changes.

You can delete those unnecessary old kernels using Synaptics afterwards. Search using the "linux-image" string on the search box(w/o quote).

---

### Post by kyphi on 2008-06-16
In addition to iaculallad's comments, while you are editing your grub menu, find the line that says Howmany=all and change it to Howmany=2

That way you will only ever display two kernels (effective after the next kernel update).

It is a good idea to retain 2 kernels in case of any of your devices suddenly not working as they should.  That way you can switch back to the previous working kernel.

---

### Post by drs305 on 2008-06-16
There is an easy and safe way to change the grub menu displays. You won't have to edit menu.lst Use startup-manager. You access it via System, Admin, StartUp-Manager. If it is not installed:
```
sudo aptitude install startupmanager
```

To read about it, visit this link:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

