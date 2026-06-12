---
title: "Issues with X"
date: 2007-07-30
forum: General Help
---

### Post by Theory? on 2007-07-30
I've got Feisty installed, but when it boots, I get a black screen in lieu of GNOME.  I can go into the terminal and log in from there, but no matter what I try, I can't get into X.

Halp!

---

### Post by rocknrolf77 on 2007-07-30
Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And pick the vesa driver.

What graphics card do you have?

---

### Post by Theory? on 2007-07-30
An ATI Radeon X1900 X

---

### Post by rocknrolf77 on 2007-07-30
Ati linux drivers aren't the best out there. So there's some problems with your card I think.

Did you try what I wrote in the last post? If you can get into x you can install the drivers with System > administration > restricted driver manager

Edit : forgot to tell you. After you have picked the vesa driver. Write ```
sudo /etc/init.d/gdm restart
```

To try starting the x-server.

---

### Post by Theory? on 2007-07-30
Oops, didn't get to type in that last line, but it worked just fine.  I'm going to install the ATI drivers once I get apt-get to work.

EDIT:  Balls, I got in and did the package updater.  Now when I boot, GRUB has a new Linux install to boot to with an updated kernel I assume and your solution no longer works.

---

### Post by rocknrolf77 on 2007-07-30
What's wrong with your apt-get? Why not just use the restricted driver manager?

---

### Post by Theory? on 2007-07-30
Eh, no diffence.  Right now I have the same problem and your solution isn't working this time.

I'm scared.  Hold me.

---

### Post by rocknrolf77 on 2007-07-30
In this thread there is instructions to install the driver with envy from the command line. Just install the ati driver instead of the nvidia driver :)

[http://ubuntuforums.org/showthread.php?t=507411](http://ubuntuforums.org/showthread.php?t=507411)

---

### Post by Theory? on 2007-07-30
This is so stupid.  I've tried this several times and Envy keeps hanging up in random places.  First it was during the unpacking, then it was during the installer, now it's "(Reading database ...)" and not doing anything.

EDIT: I installed fglrx myself and it works just fine.

Thanks for your help man.

---

