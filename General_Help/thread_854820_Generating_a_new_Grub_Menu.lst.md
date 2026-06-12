---
title: "Generating a new Grub Menu.lst"
date: 2008-07-09
forum: General Help
---

### Post by Gannon8 on 2008-07-09
I notice that Ubuntu has a great GRUB autodetector for other operating systems, but only when installing it. Is there anyway to re-generate a new Menu.lst?

---

### Post by drs305 on 2008-07-09
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo update grub

```

update-grub inspects the /boot folder and will regenerate the grub menu. You can read about it at "man update-grub". There are a few steps the man page recommends after running the above command.

For tweaking grub's menu.lst, I highly recommend StartUp-Manager:
```
sudo aptitude startupmanager
```

For tweaking the menu.lst with StartUp-Manager:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Gannon8 on 2008-07-11
No, that didn't do anything.
The command went through, but it did not change the file.

---

### Post by drs305 on 2008-07-11
Maybe you'd better explain what you are trying to do. Is your grub menu currently working? Are you having problems that need fixing or tweaking? Do you just want to see what the orginal menu.lst looks like?

---

### Post by Butthead on 2008-07-11
Just rename (or delete :shock: ) the old menu.lst.  A new one will be generated automatically for you. \\:D/

---

### Post by Gannon8 on 2008-07-13
> **drs305 said:**
> Maybe you'd better explain what you are trying to do. Is your grub menu currently working? Are you having problems that need fixing or tweaking? Do you just want to see what the orginal menu.lst looks like?I installed some other OS's after Ubuntu, and I cannot get them to boot. I don't know what to type for the parameters.

> **Butthead said:**
> Just rename (or delete :shock: ) the old menu.lst.  A new one will be generated automatically for you. \\:D/Will it have all the options preset like after installing Ubuntu?

---

### Post by WRDN on 2008-07-13
> **Gannon8 said:**
> I installed some other OS's after Ubuntu, and I cannot get them to boot. I don't know what to type for the parameters.

What other OS' did you install?

---

### Post by Butthead on 2008-07-13
> **Gannon8 said:**
> Will it have all the options preset like after installing Ubuntu?

You might have to edit menu.lst exactly to your liking, but the different OS'es themselves should boot up when you choose them. :guitar:

Anyway, doesn't hurt anything to try doing it (I would suggest you back up your current menu.lst first though (if only to use as a template to "gussy up" your new one after Ubuntu generates it again)).

---

### Post by Victormd on 2008-07-13
Type and that will update your grub and detect any other kernel and OS installed
```
sudo update-grub
```
If this doesn't do it for you, download [supergrub]("http://supergrub.forjamari.linex.org/?section=download").

---

