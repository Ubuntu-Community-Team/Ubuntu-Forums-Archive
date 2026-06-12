---
title: "xserver"
date: 2006-08-23
forum: General Help
---

### Post by hemple on 2006-08-23
yesterday morning, i installed new updates. and restarted my computer. and the x server has been broke since then. i realize now that it happened to everyone who installed the new update. the only available thing is the command line. can anyone help me?

---

### Post by someusernoob on 2006-08-23
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

The new version is in the repositories now, so if you do an upgrade you get the new version > reboot and you'll get into x again. If not, come back here :)

---

### Post by rockrhino27 on 2006-08-23
WOW!!  I'm not the only one.  i did try a few things however.  I reverted to an old copy of my xorg.conf file, restarted gdm, and that did not help.  I then went from using the "nvidia" driver back to using the "nv" driver and no love there either.  Finally I decided to run the automated dpkg configuration program, I believe the command was "dpkg -r xserver-xorg".  it got me no where.  Still looking to find a fix.  

Rock

---

### Post by win_zik on 2006-08-23
The problem should be fixed now. All you have to do is install the newest update.

To do this, simply log in (type in you username, press enter, then type in your password and press enter).
Then run:
sudo apt-get update
sudo apt-get upgrade

after the update is installed simply reboot with:
sudo reboot.

Hope this helps! :D

---

### Post by someusernoob on 2006-08-23
Look above you. 

BTW, the command line you see is the same thing as the terminal. Log in with your own name, and use it like you use the terminal in x. so you can just do an update with the commands i gave above.

---

### Post by hemple on 2006-08-23
i did exactly what you said twice. and it didnt work. still displays the same error message 'Failed to start the X server...' i did notice that when i tried to install the update...the last line of the code say ' 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded' does that mean that nothing changed? 

thanks so much for your help so far.

---

### Post by ciscosurfer on 2006-08-23
The xserver-update-crash-issue [was documented yesterday]("http://ubuntuforums.org/showthread.php?t=241254&highlight=xserver") and the routine to fix this problem is documented at the link I mention in this sentence.

[This page]("http://www.ubuntu.com/FixForUpgradeIssue") will also describe what to do to overcome the problem, especially if you hosed your system and can't get to a GUI.

---

### Post by halfvolle melk on 2006-08-23
Try downgrading first as suggested here:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)
and then do the routine mentioned above.

---

### Post by rockrhino27 on 2006-08-24
Now that everyone is working again, do we know what was wrong with the bad upgrade x-windows package?  I'm only curious.

---

