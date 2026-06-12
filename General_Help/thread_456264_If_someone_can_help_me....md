---
title: "If someone can help me..."
date: 2007-05-27
forum: General Help
---

### Post by Crafty Kisses on 2007-05-27
I'll paypal them money.

Here is my problem.

I'm trying to install my Video Card drivers, but everytime I do It gets messed up.

For example when I Install my NVIDIA Drivers, when I change my wallpaper, parts of the wallpaper I had before are on my current one. And everything is really messed up like that, FireFox appears to be apart of my background when I open it too. (Envy Attempt)

Then I tried AutoMatix, and I couldn't even get to the Login screen.

So my question is, how do I install my Graphics Card Drivers without them glitching.

Thanks In Advance.

I'm using Ubuntu 6.06 Dapper LTS

My Specs are

AMD Athlon 1.8
1GB Of Ram
GeForce 6800 GT

---

### Post by dagrump on 2007-05-27
I haven't used dapper in awhile , but you should be able to use synaptic to install nvidia-glx. Enable the universe & multiverse repositories under settings & hit the reload button. Open the search box & enter nvidia-glx, it should get you there, then you need to edit /etc/X11/xorg.conf.
But lets just see if they will install, then worry about editing xorg.

---

### Post by Crafty Kisses on 2007-05-27
Could the glitches possibly be the scripts? I havn't tried to install them manually, and also how do I know which driver to download, I have a NVIDIA 6800, unless the driver is Universal?

---

### Post by dagrump on 2007-05-27
In the package manager you will just want one with the highest version number. I have just nvidia-glx, but there is one listed as nvidia-glx-new, you could try that or use the older one. I used envy once & it seemed to work well. Automatix sometimes works real well & sometimes will turn your box to a paperweight, so I have avoided using it.

---

### Post by Crafty Kisses on 2007-05-27
Yeah thanks, I appreciate it, so after I install it, do I have to edit my X.org config file right, and  I should back it up right if something goes wrong.

---

### Post by dagrump on 2007-05-27
Yes do back it up first, then you always restore it. Good Luck.

---

### Post by x1a4 on 2007-05-27
Hi,

Do a backup of your _xorg.conf_.  

Ctrl+Alt+F2, login, *sudo /etc/init.d/gdm stop*

Edit _/etc/X11/xorg.conf_ to include the main,security,medibuntu Feisty repositories.  

Update aptitude, search for restricted drivers, nvidia kernel,  

install the appropriate nvidia kernel version (the one designated for your hardware)

install appropriate *glx* packages

install the appropriate restricted package and restricted-manager.  

Start GUI: *sudo /etc/init.d/gdm start*

...

---

### Post by Crafty Kisses on 2007-05-27
What if I have Dapper?

---

### Post by dagrump on 2007-05-27
I assume he thought you were using feisty, synaptic should mark the restricted modules & assorted stuff you'll need, w/o dropping into a command line. No need to do things the hard way.

---

