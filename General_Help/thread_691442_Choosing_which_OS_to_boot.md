---
title: "Choosing which OS to boot"
date: 2008-02-08
forum: General Help
---

### Post by bmccorm2 on 2008-02-08
Like many of us, i am dual booting Ubuntu and Windows Vista.  I am originally from a mandriva-derived distro so my question is this: on mandriva, when you choose to restart the system, it gives you the option of which OS to boot (windows or linux).  Since i mainly use my system remotely, I'd like to have that ability to choose which OS to boot while in the OS itself.  Does anyone know a package or another way that accomplishes this?

Many thanks,
Bryan

---

### Post by neurostu on 2008-02-08
I know for grub this will work....

Copy your grub.conf file a couple times, name it things like grub.1.conf and grub.2.conf etc.... (or even grub.XP.conf, grub.Ubuntu.conf, grub.Fedora.conf) then write a script that copies a grub.#.conf file over the default grub.conf  You just need to edit each grub.#.conf  to boot a different os as default.  Then even remotely all you have to do is run a script then reset the machine and the new default os will boot.

---

