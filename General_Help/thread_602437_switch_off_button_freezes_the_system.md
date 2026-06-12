---
title: "switch off button freezes the system"
date: 2007-11-04
forum: General Help
---

### Post by matrooswolf on 2007-11-04
Hi, 
I recently upgraded to Gutsy and I am experiencing some weird behavior.

Clicking on the switch off button on the upper panel, freezes the system. The dialog window does not show.  I can still move my mouse, but cannot click on anything anymore.  Only ctrl-alt-backspace works.

Any ideas as how to fix this?

---

### Post by por100pre1 on 2007-11-04
Please check if [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308") applies to you.

---

### Post by matrooswolf on 2007-11-04
Hi por100pre,

thank you for the link.

Yes it could be related. 
They are proposing different solutions, most of which unfortunatly I do not understand at the moment.  I will try them out once I can figure out which would be the best thing to do.

Thanks!

---

### Post by matrooswolf on 2007-11-04
Hi por100pre

so, as explained in the link to the bug report I did
```
sudo gedit /etc/modules
```
Added the following line:
```
apm power_off=1
```
then did
```
sudo gedit /boot/grub/menu.lst 
```
and added
```
acpi=off apm=power_off
```
to the kernel line.
Now the shutdown logoff dialog appears but only after a long time, a full minute or so.
Why is it so slooooow?

---

