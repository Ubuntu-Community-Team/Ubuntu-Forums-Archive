---
title: "XFCE For Ubuntu server"
date: 2008-05-11
forum: General Help
---

### Post by -grubby on 2008-05-11
I'm testing out Ubuntu server in a VM (QEMU) , since I don't yet have a CD to burn the ISO to. Also, this gives me time to set up how I'll do my minimal install. 

Cut to the chase: I installed it on my VM, then installed "xfce4" to get all the needed x packages. I then installed GDM. OK, so starting GDM doesn't work. It doesn't complain of errors, it simply starts and I'm just left at the terminal still. I tried startx, to which it complained this :

```
X: cannot stat /etc/X11/X (No such file or directory), aborting. 
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

So what can I do to fix this? And I'm trying a minimal install from the ground up, as I mentioned, so nothing that installs bunches of unneeded packages please.

UPDATE: Thanks p_quarles, I'm trying that now. I'll report back on how it works

---

### Post by p_quarles on 2008-05-11
The X server isn't automatically configured when you install the DE and login manager. I'm not sure why that is, but it's easy to fix:
```
sudo apt-get install xserver-xorg
```

---

### Post by -grubby on 2008-05-11
Didn't seem to work, I get the error (along with a bunch of other stuff, but I can't exactly just copy and paste from a VM, especially in a terminal) when running "startx"

```

No valid FontPath could be found

waiting for X server to begin accepting connections 
giving up.

xinit: connection rest by peer [...]
xinit: No such process

```

EDIT: Now it started gdm, and it gave me an error about the x server not being set up correctly

---

### Post by p_quarles on 2008-05-12
You probably don't have any rc file set up for X, and the default isn't right for your setup. Try:
```
sudo /etc/init.d/gdm start
```
or, create an ~/.xinitrc file with the XFCE startup command as the contents. I'm not sure what the command is, but for KDE it's startkde, and for Gnome it's gnome-session. It has to be something similar for XFCE, and you should be able to find it by typing:
```
apropos xfce
```

---

### Post by -grubby on 2008-05-12
Well the top command just said "starting gnome display manger" and then it didn't go into an x session, startx still displays the same thing. And using apropos, I couldn't figure out how to start xfce, entering ```
apropros xfce4
``` didn't work 

EDIT: Apparently "startxfce4" is the command
EDIT: Well startxfce4 has the same effect as startx

---

### Post by p_quarles on 2008-05-12
Hmm. This isn't going so well, is it? 

Btw, the "startxfce4" command should be the contents of the ~/.xinitrc file, which the startx script uses to run the X server. The startxfce4 command won't work by itself unless X is already running. 

Aside from that, maybe try running dpkg-reconfigure xserver-xorg? I'm kind of stumped, since the process I've outlined so far has never failed me.

---

### Post by daengbo on 2008-05-12
The x server isn't installed by default because it's not necessary for terminal servers.

> sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm
should fix the problem for you. 

If this isn't your real install and you want minimal, for your real server, I'd suggest using the mini.iso or if you have Grub already installed, even just the kernel/initrd from the netinstall CD.

---

### Post by -grubby on 2008-05-12
After trying both of the above suggestions, I still get the same error

---

### Post by daengbo on 2008-05-12
Make sure the following packages are installed:
xorg
xfce4
Those should be all that's required to run a desktop. The others come from dependencies.

---

### Post by -grubby on 2008-05-12
OK, I'm checking now. I'm edit this post with the results

EDIT: Well starting x this time got a different result. It gave that same screen (Blue background, gray text background, the works) Saying that it has a FATAL warning. That it can't insert my battery, but I don't have a battery 
```

FATAL: Error inserting battery
(/lib/modules/2.6.24-16-server/kernel/drivers/acpi/battery.ko): No such device

```

EDIT1: Oh and, I'm installing xorg now

UPDATE: Well, after installing xorg, running "GDM" almost works now. Apparently X tried to use failsafe mode, but faied

---

### Post by -grubby on 2008-05-14
I am bumping this thread for it has been a 24 hour period and I still have no solution

---

### Post by -grubby on 2008-05-15
Well, it's been another 24 hours. Time to *bump*

---

### Post by p_quarles on 2008-05-15
Part of what I'm unsure of here is what role QEMU is playing in this trouble. I've never had such issues with Virtualbox -- perhaps you could give that a try? At the very least, a successful attempt there would help narrow down the issue. Even if you decide you like QEMU better, it would be helpful to know whether that -- or X itself -- is the root problem.

---

### Post by -grubby on 2008-05-16
I would be running Virtualbox- and, I used to, but it never can get it's kernel thing running again. And this is the first time I've run QEMU. Perhaps I'll change the video card it uses

---

