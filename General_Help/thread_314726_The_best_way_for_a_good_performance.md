---
title: "The best way for a good performance?"
date: 2006-12-08
forum: General Help
---

### Post by Somenoob on 2006-12-08
I'm not very interested in the applications that ship with the Ubuntu Edgy Eft Desktop edition. I mostly just want the OS it self with the DE, and then install preferred programs.

Installing the server edition of edgy/dapper + X + DE(Core Gnome for example). Would this be the best manner?

---

### Post by aysiu on 2006-12-08
I wouldn't necessarily use the Server CD, but you can do a server (i.e., minimal) install from the Alternate CD and then install what you want after that: ```
sudo aptitude update
sudo aptitude install x-window-system-core gnome-core gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by K.Mandla on 2006-12-08
You can get away without a DM too, if you're willing to log in at the terminal and start X manually. 

Or you could [build an automatic login]("http://www.ubuntuforums.org/showthread.php?t=152274") that jumps straight to X ... thereby lightening the load even further, and speeding up the boot process considerably.

---

### Post by Somenoob on 2006-12-08
> **aysiu said:**
> I wouldn't necessarily use the Server CD, but you can do a server (i.e., minimal) install from the Alternate CD and then install what you want after that: ```
sudo aptitude update
sudo aptitude install x-window-system-core gnome-core gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

And where is this minimal choice in the Alternate CD?

---

### Post by aysiu on 2006-12-08
It's called "Install a Server." I don't think this is the same as installing from the Server CD, though, as the server CD uses a different kernel.

---

### Post by K.Mandla on 2006-12-08
Edgy's alternate CD calls it a "command-line system."

---

### Post by Somenoob on 2007-01-01
Where exactly is the minimal install or "install a server" on the Alternate CD. I've looked on both Dapper and Edgy disks, I only find the regular desktop installation.

---

### Post by aysiu on 2007-01-01
> **Somenoob said:**
> Where exactly is the minimal install or "install a server" on the Alternate CD. I've looked on both Dapper and Edgy disks, I only find the regular desktop installation.
Maybe you don't have the Alternate CD. Maybe you have the Desktop CD?

---

### Post by Somenoob on 2007-01-01
> **aysiu said:**
> Maybe you don't have the Alternate CD. Maybe you have the Desktop CD?

yea, how silly of me. I'm downloading it via torrent right now, and i know how to perform the desired installation.

thanks for the help.

---

