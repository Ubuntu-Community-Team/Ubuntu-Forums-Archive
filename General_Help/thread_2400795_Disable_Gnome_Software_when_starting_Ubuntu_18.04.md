---
title: "Disable Gnome Software when starting Ubuntu 18.04"
date: 2018-09-10
forum: General Help
---

### Post by lynx6 on 2018-09-10
Hello,
Can I disable *Gnome Software* when starting **Ubuntu 18.04**?
And how to disable it?
*Gnome Software* consumes a good amount of memory when starting with **Ubuntu 18.04**, I would like to disable it.

Thank you.

---

### Post by #&amp;thj^% on 2018-09-10
> **lynx6 said:**
> Hello,
Can I disable *Gnome Software* when starting **Ubuntu 18.04**?
And how to disable it?
*Gnome Software* consumes a good amount of memory when starting with **Ubuntu 18.04**, I would like to disable it.

Thank you.
Try to disable it in gsettings
```

gsettings set org.gnome.software download-updates false

```
If that fails .. mask (disable) the backend service, PackageKit, the service used by Gnome Software via.

```
sudo systemctl mask packagekit.service
```

---

### Post by lynx6 on 2018-09-10
Thanks for the answer.

I logged in with the first command, restart the computer.
*gsettings set org.gnome.software download-updates false*

I logged in with the second command and also rebooted the computer.
*sudo systemctl mask packagekit.service*

But Gnome Software keeps showing up on the System Monitor with ***115 Mb***.

---

### Post by #&amp;thj^% on 2018-09-10
> **lynx6 said:**
> 
But Gnome Software keeps showing up on the System Monitor with ***115 Mb***.
If you mean that there is an active desktop app of PackageKit that is still starting - yes. But if you have masked those 2 services, that desktop app should not be doing anything: no metadata is downloaded, and there are no conflicts or confusion.
Also have a look here: [https://forums.fedoraforum.org/showthread.php?315410-How-to-disable-Gnome-Software-autostart](https://forums.fedoraforum.org/showthread.php?315410-How-to-disable-Gnome-Software-autostart)

---

### Post by lynx6 on 2018-09-10
*@1fallen*, thanks a lot for the reply, **Ubuntu 18.04** after the changes starts faster.
Greetings!

---

