---
title: "Drag effect on Ubuntu's desktop"
date: 2013-10-12
forum: General Help
---

### Post by Helvio_Vairinhos on 2013-10-12
Hi,

I am experiencing a problem with Ubuntu 13.04. After I mounted an external hard drive the desktop started behaving erratically out of nowhere. The wallpaper disappeared, and everything I drag over it gets imprinted all over the place (reminds me of old times, when MS Windows froze...)

[ATTACH=CONFIG]246893[/ATTACH]

I disconnected the hard drive, I restarted Ubuntu, restarted lightdm, and I even reinstalled nVidia's driver, to no avail. This has never happened before, and I have no idea what triggered it or how to solve this problem. Do you have any ideas?
By the way, everything else works perfectly fine. Only the desktop is misbehaving.

Thanks,
Helvio

---

### Post by Helvio_Vairinhos on 2013-10-13
UPDATE: the desktop still shows the same symptoms, but after a software update it got worse. The system font looks horrible in any program (see picture), and Ubuntu keeps informing very frequently that the software is up to date. Any help is welcome. I have no idea what is going on...

[ATTACH=CONFIG]246913[/ATTACH]

---

### Post by Jonathan Precise on 2013-10-13
For the desktop problem, launch the File manager (the program that handles the Desktop). If it fails, post the system specs and revert to the open-source driver.

---

### Post by Helvio_Vairinhos on 2013-10-13
Hi Jonathan, thanks for your reply.

I have both nemo and nautilus as file managers, and they both open fine. I followed the instructions from
[http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html](http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html) to have nemo as the only file manager dealing with the desktop. In fact, only the desktop and the system fonts have problems, everything else opens and works fine.

I reverted to the open source display driver (Nouveau) and I got an error message after reboot, plus loss of resolution, and the symptoms persist. The error message said: "Could not apply the stored configuration for monitors"

System specs:
Laptop Model: ASUS G73SW
RAM/Memory: 16GiB
Processor: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Video Card: NVIDIA GeForce 460M GTX
Current installed Ubuntu version: 13.04 64 bit
Hard Drive Space: 1TiB

---

### Post by jawilljr2 on 2013-10-13
Helvio, I was having the same problem, after I upgrading the Cinnamon desktop to 2.0. A 'workaround' is to make nautilus the default manager using these commands:

```
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
gsettings set org.gnome.desktop.background show-desktop-icons true
gsettings set org.nemo.desktop show-desktop-icons false
```

I hope and update fixes the rendering problem.

I also [found this.]("http://askubuntu.com/questions/358584/nemo-2-0-does-not-render-desktop-correctly-with-compiz")

Hope this helps.

---

### Post by Helvio_Vairinhos on 2013-10-13
Thanks jawilljr2! Your suggestion solved my desktop rendering problems.
However, the issue with font rendering persists... but since this seems to be a different issue, I should mark this particular problem as solved. :)

---

