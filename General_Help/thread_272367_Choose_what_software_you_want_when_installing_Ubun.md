---
title: "Choose what software you want when installing Ubuntu?"
date: 2006-10-06
forum: General Help
---

### Post by Leiki on 2006-10-06
I was installing Ubuntu (6.06 Desktop) on my 2GB external HD and everything was going well until it ran out of space (should have read the system requirements). Anyway, I'm wondering if there is a way to choose what exactly you want regarding software when installing Ubuntu to minimize the space? Thanks!

---

### Post by kerry_s on 2006-10-06
Yes, you can grab the alternate cd( [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-i386.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-i386.iso) ) and do a server install, then build it up from there. A server install doesn't have a gui to start it's just the base system, but it is very easy to build any system you want from there. Here's a quick run down->

Do the server install and login
sudo su   <this makes you root
nano /etc/apt/sources.list   <comment(#) out the cdrom and uncomment all the repos, they start with "deb". ctrl and x and y and enter to save.

apt-get update
apt-get install x-window-system-core xterm (select a login manager) (select a DE or WM)
reboot   <type to reboot the system and login to the gui

login managers= xdm(basic) wdm(just above basic) gdm(a very good one,gnome standard) kdm(also very good,kde standard)

DE= desktop enviroment(ubuntu-desktop, kubuntu-desktop, xubuntu-desktop) They come with just about everything you need for a desktop eviroment

Wm= window manger( fluxbox, openbox, wmaker, icewm,...)

In your situation where you need space, you can build up from a wm or instead of installing the full desktop just grab the core> kde-core, gnome-core, xfce4.

for example for Gnome:
apt-get install x-window-system-core xterm gdm gnome-core

for example for KDE:
apt-get install x-window-system-core xterm kdm kde-core

for example for xfce4:
apt-get install x-window-system-core xterm gdm xfce4

When installing a WM, you have to select everything you'll need like a filemanger,editor,... everything. It's the most flexable
be cause you choose everything, but it's the longest to set up.

Almost forgot: The first thing i do after logging in to my desktop is launch a terminal and grab synaptic(the gui package manager) so i can remove what ever i don't need and install whatever else i need.> sudo apt-get install synaptic <then just type> sudo synaptic <to run it real quick with out having to look for it in the menu. You'll defintly need to trim it down after install. I'm running a basic kde and i've done alot of trimming and i'm at 730mb installed. Just come back after you get installed and i'll try and help on that.

---

### Post by Jagot on 2006-10-06
You could do a server install which essentially gives you the bare minimum, then add what you want through apt-get/aptitude.

EDIT:  Looks like kerry_s beat me to it - and far more thorough as well!

---

### Post by kerry_s on 2006-10-06
Also i'm not sure what your specs are, but if you want the most full feature, go for the kde-core, konqueror is very multipurpose and can do many things by itself including web browsing, where as the others you will still have to install a web browser. konqueror is already a webbrowser.

---

### Post by Leiki on 2006-10-06
Thank you so much for the help, kerry_s. When I boot from the iso I burned, it doesn't ask if I want to install server or desktop...or is server the default option?

---

### Post by lemonsCC on 2006-10-07
> ***grab the alternate cd( [http://releases.ubuntu.com/6.06.1/ub...rnate-i386.iso](http://releases.ubuntu.com/6.06.1/ub...rnate-i386.iso) ) *** .

---

### Post by Leiki on 2006-10-07
...Yes, that is what I downloaded.

---

### Post by lemonsCC on 2006-10-07
When you pop the CD in it will come up with a screen, with the ubuntu graphic on top...

Choices are:
Text Installer
Install an OEM
Install a Server  <---- YOU WANT THIS ONE!

---

