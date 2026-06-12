---
title: "please help, feisty upgrade disaster"
date: 2007-04-20
forum: General Help
---

### Post by Naegling23 on 2007-04-20
I was trying to upgrade to feisty, but the upgrade manager crashed on my nvidia glx drivers.  Now I cannot get to a command prompt, the system hangs before I can get to the login screen.  I have tried recovery mode, and older kernals, they all hang before the login.  

Please help!!!!!!

update: When I select recovery mode, it gets to checking file system.  It fails activating swapfile swap, then hangs on setting up console font and keymap.

---

### Post by beaudoin996 on 2007-04-20
Press Ctrl+Alt+F2 to access a prompt.  Then reinstall the NVIDIA drivers and restart the X server

---

### Post by Naegling23 on 2007-04-21
ctrl+alt+f2 just brings me to a blinking _  No prompt...I cant even get it that far.  Will I be able to burn a disk and install the OS over again without loosing all of my data?

---

### Post by Naegling23 on 2007-04-21
OK, wow, I solved the problem...not easy, but I got through it.  Im posting a reply because I often find these threads through google, and I hate when there is no resolution.

I burnt a feisty live cd, and booted up using it.  After booting, I chroot'ed into my hard drive install using:

sudo mkdir /media/drive
sudo mount /dev/sda1(my drive ID, yours might be different) /media/drive

that mounts the drive then chroot

sudo chroot /media/sda1

Now I had control of my install (this lets you "fix things" from a live cd, which a lot of users in the irc channel were telling me was not possible).

the next command is sudo apt-get -f install  i guess this is to finish the install?  anyway, it didnt work because of dpkg errrors, so

sudo dpkg --configure -a

after that was done, sudo apt-get -f install

I got a bunch of errors and all sorts of stuff, I rebooted, and I got to a command prompt!!!!!

I edited the xorg.conf file to allow me to use the nv drivers (this was the cause of all of my problems originally)  I also removed nvidia-glx.  I dont know exactly what I did here, I just know that I switched to the nv drivers, and removed nvidia-glx.
sudo nano /etc/x11/xorg.conf
I changed driver "nvidia" to "nv"  this uses the free nvidia drivers, no 3d, but it got the system up and running.

Rebooting again brought me to my feisty desktop!!

From there, I used adept to clean up the rest of my upgrade, and installed the nvidia-glx drivers.  

Hopefully this helps someone in the future, I was about to reformat and start over.  Glad I didnt have to.

---

### Post by wavell2003 on 2007-04-28
Naegling23,

   The chroot is just what the doctor order for my system.  Worked like a charm!

---

