---
title: "boot problem"
date: 2007-04-16
forum: General Help
---

### Post by rogerrus on 2007-04-16
I deleted my boot partition when installing windows, and now I obviously enough cant boot anymore.
So now I want to install grub again to /boot on the same partition as the rest. 
But how can I do this? I guess i would somehow have to compile a new kernel to boot, and then re-install grub and set it up again... But how?
The grub install is easy, bot how do i compile a new kernel? Or, preferably: how can i make ubuntu auto-generate a new kernel for me?

---

### Post by Seisen on 2007-04-16
This should help you fix Grub, you need a ubuntu live cd  or you can use knoppix also.
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by rogerrus on 2007-04-16
I think you misunderstood a little bit...
I lost everything on the /boot. So its not that easy.
I will need a new source that grub can load.

---

### Post by Seisen on 2007-04-16
It will automatically compile your grub menu list after you finish with the directions.

---

### Post by rogerrus on 2007-04-16
So i wont have to compile a new source for grub to load?

---

### Post by Seisen on 2007-04-16
No you won't.

---

### Post by rogerrus on 2007-04-16
Yes, I do have to do something like that. 
Because when trying to setup grub it cant find /boot/grub/stage, because I have deleted it with the rest of the /boot partition.
So how do I get this?

---

