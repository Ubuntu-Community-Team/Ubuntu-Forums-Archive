---
title: "grub loads old kernel instead of latest (?)"
date: 2013-08-30
forum: General Help
---

### Post by matrooswolf on 2013-08-30
Hi,
Since upgrading to 13.04 my desktop randomly crashes (shuts down all programs and goes back to the login screen) see this thread [http://ubuntuforums.org/showthread.php?t=2168534](http://ubuntuforums.org/showthread.php?t=2168534).
I'm still looking for what the cause might be, but so far no luck.

But in the process I saw that grub loads an old kernel.

When I type```
 uname -r
``` I get```
 3.0.0-32-generic-pae
``` It should be ```
3.8.0-29-generic
```
When I open Grub-Customizer the right kernel is there, on top on the list, but for some reason, the old one is loaded.

Anyone know how to fix this?

---

### Post by matrooswolf on 2013-08-30
I see now that /boot/grub/menu.lst is not updated.
So, altough grub-customizer shows the latest kernel, the latest one in /boot/grub/menu.lst is still 3.0.0-32-generic-pae
I ran ```
sudo update-grub
``` which finds all the kernels and returns ```
Updating /boot/grub/menu.lst ... done
``` but when I open menu.lst it is not updated, the new kernels are not there

---

### Post by matrooswolf on 2013-08-30
I have deleted menu.lst and ran ```
sudo update-grub
``` again. This time it generated the new kernels.
Still I wonder why grub didn't update menu.lst automatically

---

