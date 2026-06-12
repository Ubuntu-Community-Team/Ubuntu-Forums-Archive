---
title: "Cloning Problems"
date: 2007-06-04
forum: General Help
---

### Post by cccnutty on 2007-06-04
I am relatively new to ubuntu and linux, so hopefully my problem makes sense.  

I am using ubuntu 7.04 (Feisty Fawn) and trying to clone one computer to a new hard drive that then goes into a different computer that has different hardware.  I have tested the cloned disk in the original machine and it works fine. 

The problem I get is that when it boots up I get some garbage output on the screen, with "Failed to start the x server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to ...(garbage)".  I can hit esc during startup and get to the terminal using the "recovery mode" option.

Another problem I get when I try the drive in a different machine is that it will run just fine, but it doesn't show the splash screen and it takes over 5 minutes to start up, where it sits at a black screen with nothing on it.

I am guessing that both of these problems can be fixed in the same way of somehow telling ubuntu it is on a new hardware configuration so it can change some settings, but I don't know how.  If someone could help me fix this or point me to a solution elsewhere I would be very thankful.

---

### Post by jimbob on 2007-06-04
Generally speaking when you clone a disk and then put it in a different computer, unless the second computer's hardware is *_exactly_* like the original one you are bound to have hardware mis-match problems.  I believe that is what is causing your X-configuration (and other things) to fail.  You can probably fix X by running dpkg-reconfigure -phigh xserver-xorg and then restarting gdm with /etc/init.d/gdm restart.

If I was you, to avoid continuing grief down the road, I would do a new install on the second machine (it really doesn'take that long) and then copy over your personal stuff in your /home directory afterwards.  Many people create a separate /home partition specifically for this purpose as well as for simplifying backups.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by gerscht on 2007-06-04
you can do a
```

sudo dpkg --get-selections > /root/installed-packages.txt

```
on machine A and copy the file /root/installed-packages.txt with your /etc/apt/sources.list to computer B.
There you do a 
```

sudo apt-get update
sudo dpkg --set-selections < installed-packages.txt

```
to get exact the same packages installed 
See 
```

dpkg --help

```
for more info

---

