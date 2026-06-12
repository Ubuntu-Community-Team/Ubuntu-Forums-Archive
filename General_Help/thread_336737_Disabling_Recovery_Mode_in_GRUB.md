---
title: "Disabling Recovery Mode in GRUB"
date: 2007-01-12
forum: General Help
---

### Post by Brando569 on 2007-01-12
i never use recovery mode since i could just edit the boot options of my regular kernel if i needed to get into it and it it just clutters up my grub menu. is there a way to permanentyl disable it from coming up in grub. i saw that it was listed under altoptions, would just removing it from there help??

---

### Post by taurus on 2007-01-12
Just remove it from /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Brando569 on 2007-01-12
sorry i wasnt clear, i dont want it to be put in there at all. for example, if i install a new kernel i dont want it to put recovery mode into my menu.lst

---

### Post by taurus on 2007-01-12
It's automatically updated your /boot/grub/menu.lst with two entries, one for a kernel and a recovery mode, so you just have to remove the recovery mode by hand then!

---

### Post by SeanHodges on 2007-10-01
I don't know if you fixed this already, but you can dictate how Ubuntu rebuilds your menu.lst by editing the commented options in the AUTOMAGIC KERNEL LIST section contained inside menu.lst itself.

The important thing to remember is DON'T UNCOMMENT THE OPTIONS, just edit the values.

So edit /boot/grub/menu.lst, and find this section:

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

Change to say this:

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false


After you've made the change and saved the file, back it up, and run "sudo update-grub" to rebuild your grub settings using the new rule.

---

### Post by Brando569 on 2007-10-22
no this was never fixed. now it is, thanks. :)

---

### Post by thenetduck on 2007-12-04
> **taurus said:**
> It's automatically updated your /boot/grub/menu.lst with two entries, one for a kernel and a recovery mode, so you just have to remove the recovery mode by hand then!

It I right a little script for this, it will remove all of (recovery modes) found in the bootloader? 

The Net Duck

---

### Post by Brando569 on 2007-12-04
just do what seanhodges said, works perfectly :D

---

