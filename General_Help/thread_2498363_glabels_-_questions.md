---
title: "glabels - questions"
date: 2024-06-10
forum: General Help
---

### Post by jgw on 2024-06-10
I have a previous posting about a problem I was having with glabels.  I have been rooting about with glabels and there seems to be several of them or just one distributed by several.  I have no idea which is which.  There is glabels-data_3.4.1-3_all.deb and there is gnome glabels and possibly more.  I have a glabels installed in my system.  The interesting thing is that I cannot check which it is because ubuntu does not know that it is installed, even though its in its list of stuff installed (bet strange).  

My main problem is that I cannot make my dymo labels printer give me labels the size of my labels (2.125"x2.75") it insists in only printer up to something around 1/3 of that size.  I have requested help from all over but am either ignored or mis-understood.  So, I am trying to start anew and am trying to make sure which I should install.  I have two choices: gnome glabels and glabels-data_3.4.1-3_all.deb  The glabels-data says to:
# sudo apt-get update
# sudo apt-get install glabels-dev

this will not only give me glabels but, apparently a pile of other files.  
You can find it at: [https://ubuntu.pkgs.org/22.04/ubuntu-universe-arm64/glabels-dev_3.4.1-3_arm64.deb.html](https://ubuntu.pkgs.org/22.04/ubuntu-universe-arm64/glabels-dev_3.4.1-3_arm64.deb.html)

Then there is the gnome glabels:
sudo apt update
sudo apt install glabels

There are, as far as I know, not anything else.

I have no idea which will be correct to install and, right now, I have no idea which I have installed.  I don't even know that either one can actually use the label I want to use.  What I do know is that this printer used to do the whole libel.  I have not used it in a very long time and now it no longer will fill a label and only print so big and no bigger.  I have also contacted dymo but they are no help on this one as, apparently, they have no idea how to force their printer to print a label that is 2.75"x2.125"

Any thoughts on this would be appreciated.

---

### Post by jgw on 2024-06-10
I have just spent a pile of time trying a variety of stuff from the net.  The last one I did was:
[https://installati.one/install-printer-driver-dymo-ubuntu-22-04/](https://installati.one/install-printer-driver-dymo-ubuntu-22-04/)

This worked!  I no longer have a problem!  

this can be marked done.

---

### Post by Holger_Gehrke on 2024-06-10
Like a lot of programs, glabels is split up into multiple packages. 'glabels-data' is the data files needed by the program. It's split off into a package of it's own so you can have packages for glabels for different processors and don't have to include that data in each of them. 'glabels-dev' contains stuff for developers who want to use the library that is the core of the glabels program (libglabels5) in their own programs; it's mostly header files and documentation. So the package to install is 'glabels' and that will pull in 'glabels-data' by dependency; you can see that by looking at the output of 'apt show glabels'. 
For looking at what's installed, you can use dpkg. dpkg is the lower level of package management; it's only concerned with local files and know nothing about sources for files or downloading them. It just installs local packages and keeps track of them and their dependencies on each other. To see what glabels packages are installed, you'd use "dpkg-query --list 'glabels*' ". To find out what package a file belongs to you can use 'dpkg -S /path/to/file' e.g. 'dpkg -S /bin/ls/' will tell you that the 'ls' command is part of the package coreutils. If you don't know where an executable is stored, you can use 'which' e.g. 'which glabels-3'. To feed that information into dpkg, use a command substitution like so: 'dpkg -S $(which glabels-3)'.

Another thought: have you checked the units of measurement in Edit->Preferences ? I think it defaults to millimeters ...

Holger

Edit: Just saw you had solved it yourself. So it was the printer driver ...

---

### Post by jgw on 2024-06-10
I have two labels I use.  I had to give this one the size of each.  I then did a test and they both worked just fine. So, basically this one was a single dandy.  I have no idea how much time I spent on this before I got smart enough to start actually looking (its always amazed me the questions you can ask and actually get a reply).  Its a little embarrassing as well.  I am simply getting too old for this stuff and dementia is not helping at all!

---

### Post by dragonfly41 on 2024-06-11
I remember buying a labelling gadget for a family member. Never used one myself. If you are interested in creating custom labels with themes then Scribus Desktop Publisher (in repo) is a nice tool combined with [ScribusGenerator]("https://berteh.github.io/ScribusGenerator/") (Python script designed for custom business cards). Then print using a box of label sheets.
This way you can customise.

---

