---
title: "Where have the terminals gone?"
date: 2005-10-22
forum: General Help
---

### Post by MasterXandrex on 2005-10-22
:confused: :confused: :confused: :confused: :confused: 

I thought I posted this last night... but I can't find it. Anyway, I am relatively new to linux and even newer to ubuntu. I used 5.04 and liked it and thought I would upgrade to Breezy, however there are a few things I don't like. Where are the terminals in the GUI. I usually right click and click open terminal, but that seems to be gone. Also it doesn't seem to be in the System Tools menu. I like Ubuntu and don't want to switch distro's but this is enough to drive me nuts, also, the make command in the terminal seems to be gone... is there some package I need to install to get these features back... some special installer kernal.

Please Help

---

### Post by dtfinch on 2005-10-22
I miss the feature as well. It was a good feature. It seems that Gnome becomes less and less complete with every release.

You can go to preferences->keyboard shortcuts and map a key combination to it. That's almost as good.

---

### Post by makhand on 2005-10-22
Yes, this bugged me a bit too. Its in Applications>Accessories>Terminal. 

I've added a launcher for it and placed it in the 'quicklaunch' area. now I just click on the little icon when i need a terminal. 

You'll probably have to install a package for 'make'. I think it might be in build-essential.

---

### Post by landotter on 2005-10-22
install nautilus-terminal (think it's called that) and you can rightclick for a terminal on the desktop or in a file manager.

---

### Post by bionnaki on 2005-10-22
yup.
apt-get install nautilus-open-terminal

---

### Post by MasterXandrex on 2005-10-22
Can't get "apt-get install nautilus-open-terminal" to work... output follows:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nautilus-open-terminal


help...?

---

### Post by Leigh on 2005-10-22
You need to enable all the respositories. Then try the command again. After doing that, you will have to log off and log in again to see "Terminal" in the right-clikc menu.

The solution is in this thread [http://www.ubuntuforums.org/showthread.php?t=75432](http://www.ubuntuforums.org/showthread.php?t=75432)

---

### Post by MasterXandrex on 2005-10-22
Thank You, Worked Perfectly

---

