---
title: "Edgy command-line install from alternate CD"
date: 2006-11-01
forum: General Help
---

### Post by veli on 2006-11-01
Does anybody know what will be installed in "command-line mode" form the alternate CD in Edgy.

Is this only the Edgy system, but without the desktop?

I'm asking because usually I do a server install and I'm adding only gnome-core and the programs I need.

---

### Post by taurus on 2006-11-01
If you pick the first option, text base, when you boot from the alternate CD, it will install everything, including Gnome, as you would have from the LiveCD.  So, if you want to install Gnome, then pick the first option...  The reason for the alternate is for those who are having trouble booting the LiveCD because of graphic card or don't care about the LiveCD and just want to install the whole thing right away.

---

### Post by Ramses de Norre on 2006-11-01
If you pick command line install you'll get everything except the GUI programs.
So everything you can run on command line only after a normal install.

And of course you can add the GUI stuff via aptitude/apt-get if you want.

---

### Post by veli on 2006-11-01
Thanks for the prompt reply,

what do you mean by "except the GUI programs"?

I need something like the "server install" but with the desktop generic kernel. (I can get it on the server via apt-get I know, but I want to save some time).

What will be the result when reboot from "command-line" installation?

---

### Post by taurus on 2006-11-01
Do you want to do a server or a desktop install???  If you want the server, use the server CD, if you want a desktop, then you can use either the LiveCD or the alternate CD...

---

### Post by veli on 2006-11-01
What I want is a minimal Ubuntu-desktop install based on the Gnome-core. With such a set-up I'm getting around 70 MB consumed when the system is idle (it's more than 100MB with the default install). I have only 256 MB RAM. That is why all this about.

---

### Post by Ramses de Norre on 2006-11-01
Well the alternate cd gives you the option to install a command line only system, so ubuntu-minimal gets installed but no xserver and thus no graphical programs.

And you can indeed then install xserver-xorg-core and gnome-core and then you'll have gnome without all the bloat of ubuntu-desktop.

I did the same for my edgy install and it works very well, just be aware that you'll need to be able to get around in cli to install some things and get the network up etc.

Also: watch out for vim, the one installed by default is vim-minimal and is _terrible_! So you'll want to install vim-full before using it.
Just a hint because it drove me nuts ;)

---

### Post by veli on 2006-11-01
Thanks for the suggestions Ramses. I'm using nano to modify the apt sources, and the DHCP network is up after the install. So, I'll give it a try today and report back to let you guys know.

---

### Post by veli on 2006-11-01
Hi Ramses, I installed edgy with command-line option. It worked generally, and the whole installation is below 1 GB. Unfortunately, I didn't get the sound working, I need to move PCM and master sliders of alsamixer a bit to get it right. Also, when I tried to open the preferences of the volume control on the tray I get this: "Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)". Do I need any additional package, I installed Gnome alsamixer, but no luck. Since my sound is off after reboot, I'd prefer to get it back by moving the sliders from the right click menu of the speaker on the tray.

Another thing is that I don't have users in the Administrative menu and I can't adjust the time and date now. Do you have any idea if something is missing?

Thanks a lot.

---

