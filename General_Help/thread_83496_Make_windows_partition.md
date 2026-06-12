---
title: "Make windows partition?"
date: 2005-10-28
forum: General Help
---

### Post by Donnut on 2005-10-28
Hi.  After many attempts to install the ATI drivers correctly, to no evail, I want to make a 4gb partition to let windows run in.  But, the "create" partition on any partition program is always greyed out, even in root.  How do I make one?

---

### Post by Remmelas on 2005-10-28
well, if your friendly with the command line, us fdisk or cfdisk(cfdisk is a little more friendly).  I hear of ati issues a lot, may I ask what you did to install them?  or more accurately, offer these steps that have worked for me over 3 different installs now with the same video card(my wifes pc, my own, and my childrens)

sudo apt-get install fglrx-control xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

Then, answer the questions in approximately this order
   1.      Autodetect
   2.      2 fglrx
   3.      yes
   4.      yes
   5.      yes
   6.      131072 (very specific to my own video card 128MB of ram, replace with a number that is accurate for the machine specific card)
   7.      No(kernel framebuffer question, not sure what real effect this has)
   8.      Yes
   9.      Enter
  10      us
  11.     xorg
  12.      Enter
  13.      microsoftoffice (my own keyboard type, need to replace with whatever maches the keyboard)
  14.      enter
  15.      leave blank
  16.      enter
  17.      blank
  18.      no
  19.      yes
  20.      enter
  21.      enter
  22.      star all modules listed except record
  23.      Yes
  24.      Yes
  25.      Yes
  26.      Enter
  27.      star the resolutions you want
  28.      Enter
  29.      Advanced
  30.      30-70(specific to my own monitor, customize for current monitor)
  31.      50-160(specific to my own monitor, customize for current monitor)
  32.      Enter
  33.      24

It's also on my wiki page in a little easier to read format.

---

### Post by Donnut on 2005-10-28
I have tried the commands to install the drivers, in root, and it gives me the following errors...

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Remmelas on 2005-10-29
disable your backports repositories, and those errors will go away.

---

