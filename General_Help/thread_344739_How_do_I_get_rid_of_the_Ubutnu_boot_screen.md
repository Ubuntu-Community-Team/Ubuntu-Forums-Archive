---
title: "How do I get rid of the Ubutnu boot screen?"
date: 2007-01-23
forum: General Help
---

### Post by AceRimmer on 2007-01-23
Hello, how do I get rid of the ubuntu screen with the progress bar that is shown while the system is booting up?  I want to see the processes as they are going on to try and figure out where I am having a lockup problem on boot.  

Thanks!

---

### Post by Choad on 2007-01-23
tap ctrl-alt-f1 as soon as the progress bar shows.

---

### Post by Choad on 2007-01-23
also, to hazzard a guess, try booting with the options

acpi=off noapic nolapic

---

### Post by AceRimmer on 2007-01-23
Thanks.  But is there a way to stop that screen from loading at all by editing a config file or something?

Edit:  I see your second reply now.  Thanks for the help.

---

### Post by taurus on 2007-01-23
Remove both **quiet splash**  from the kernel entry in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by AceRimmer on 2007-01-23
> **taurus said:**
> Remove both **quiet splash**  from the kernel entry in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```


That is the answer I was looking for!  Thanks to the both of you for helping me out. =D>

---

