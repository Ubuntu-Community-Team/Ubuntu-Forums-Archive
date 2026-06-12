---
title: "&quot;Install Problem&quot; Help!"
date: 2008-04-14
forum: General Help
---

### Post by Fraser484 on 2008-04-14
Hey guys. When I boot into Ubuntu with Gnome it boots me into a completely different theme that isn't Human at all. It has no icons in the Application, Places, and System menus and has the little green running guy on the top left.

In the bottom right corner, as soon as I log in, i get a:

 "Install Problem!" The Configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.

I also am not able to run much without the error popping up, such as system updates.

Please help! Thanks in advance!

---

### Post by Duckyspetrie on 2008-04-14
I would verify the install disc you used and check for errors, then if that turns out ok, reinstall.

---

### Post by tango_ninja on 2008-04-14
is this a fresh install or did it happen all of a sudden to a previously working install ?

---

### Post by Fraser484 on 2008-04-14
I've been using a previously working install now for about 6 months.

---

### Post by BaffledMollusc on 2008-04-14
I guess you could try removing Gnome power manager and reinstalling it. If you can't get into Synaptic, you can do it with the command line by entering

sudo apt-get remove gnome-power-manager
sudo apt-get install gnome-power-manager

If that doesn't work you could try removing the manager *and* its configuration scripts before reinstalling by doing
 
sudo apt-get --purge remove gnome-power-manager
sudo apt-get install gnome-power-manager

---

### Post by Fraser484 on 2008-04-15
ok that uninstalled "ubuntu-desktop" and "gnome-core" as well. i restarted X and it put me right into the KDE environment. 

i'll try redoing the Core and Desktop.

---

### Post by Fraser484 on 2008-04-15
really am not understanding this problem. 

as you could guess when I got to System > Preferences > Power Management the "Install Problem" box in the bottom right corner pops up Three Times. Hmm.

---

### Post by BaffledMollusc on 2008-04-15
Hold on... you did reinstall gnome-power-manager, right?

---

### Post by Fraser484 on 2008-04-15
Yes. Correct. I purged. Then re-installed. Version 2.22.1-1ubuntu4

---

### Post by BaffledMollusc on 2008-04-15
Very strange.

Well, then I'm out of ideas. Sorry, hopefully someone else can help!

---

### Post by Fraser484 on 2008-04-15
Ah. Well appreciate all the help mate. Hopefully some solution will come up.

---

### Post by BaffledMollusc on 2008-04-15
I found something else. This thread is about a similar problem: [http://ubuntuforums.org/showthread.php?t=630839](http://ubuntuforums.org/showthread.php?t=630839)

The upshot is that if you run
sudo dpkg --configure -a
sudo apt-get -f install

it might solve the problem.

The first command reconfigures all packages that have been downloaded. I'm not sure what the second does, although the -f probably means "force", i.e. ignore integrity checks.

---

### Post by Fraser484 on 2008-04-15
ahh nope. still nothing! i wonder why it worked for him... i'll keep lookin

---

