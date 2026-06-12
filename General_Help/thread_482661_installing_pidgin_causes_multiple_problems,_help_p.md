---
title: "installing pidgin causes multiple problems, help please!"
date: 2007-06-23
forum: General Help
---

### Post by bfarzan on 2007-06-23
Being a Linux beginner, I wanted to give Pidgin a try. So I attempt to install Pidgin but I seem to have to uninstall gaim first. So I go to the Synaptic Package Manager and I search for Gaim and I remove all files installed that show up under the search. Then I install Pidgin and it works fine. But the following problems have arisen. On my top menu, under Places, Computer and Home and all those folders have disappeared... the only thing left is Desktop and upon click the following error pops up:

Could not open location 'file:///home/*username*/Desktop: There is no default action associated with this location.'

Now if I try to in any way uninstall Pidgin, install Gaim and hopefully undo whatever I've done to cause this I get the following message:

E: /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb: trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin

Worst of all... if I try to use the update manager to update ubuntu, the following message shows:

Software Index is Broken: It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Any help to fix this would be appreciated ;)

---

### Post by bfarzan on 2007-06-23
*update* No matter what I have on my desktop, the icons don't show up.

---

### Post by raul_ on 2007-06-23
Well, did you run "sudo apt-get install -f" ?

---

### Post by bfarzan on 2007-06-23
> **raul_ said:**
> Well, did you run "sudo apt-get install -f" ?

Yes I did, here's the output it came up with:

-----------------------------------------------------------------------------------------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gaim
Suggested packages:
  libmeanwhile1 libzephyr3 tcl8.4 tk8.4
The following NEW packages will be installed:
  gaim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1741kB of archives.
After unpacking, 4923kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 128654 files and directories currently installed.)
Unpacking gaim (from .../gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/share/dbus-1/services/gaim.service', which is also in package pidgin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gaim_1%3a2.0.0+beta6-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------------------------------------------------------------------

---

### Post by raul_ on 2007-06-24
Could you show me the output if you try to remove piding?

---

### Post by bfarzan on 2007-06-24
> **raul_ said:**
> Could you shopdw me the output if you try to remove piding?

I was able to uninstall Pidgin successfully using the Synaptic Package Manager. Then I successfully installed Gaim back on my machine. The update manager can now update properly. However I still can't access the Places and Folders I have and my desktop is still iconless.:(

Thanks for the help, this is getting somewhere!

**update**: On reboot, or startup, the wallpaper doesn't load. Maybe this can clue you in what's wrong here.

---

### Post by bfarzan on 2007-06-24
I fixed the problem. It was too simple. I went into Synaptic Package Manager and used a very handy button called "History". Then I looked at the packages that I had accidentally removed:

Removed the following packages:
gaim
gaim-data
gnome-user-guide
libbeagle0
nautilus
nautilus-cd-burner
nautilus-sendto
ubuntu-desktop
ubuntu-docs
yelp

I reinstalled them and everything is fine now. Thank you for the help!

---

