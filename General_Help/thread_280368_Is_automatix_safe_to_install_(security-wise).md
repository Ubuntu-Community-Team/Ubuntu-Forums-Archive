---
title: "Is automatix safe to install? (security-wise)"
date: 2006-10-19
forum: General Help
---

### Post by Pri0n on 2006-10-19
Is automatix safe to install (from a security standpoint)?  Is it open source?  Given that it messes around with your repositories and automatically downloads and installs applications for you (from who knows which repositories), I'm worried about the possibility of it downloading trojaned applications from questionable sources. (i.e. rootkits)

---

### Post by taurus on 2006-10-19
I say it's safe (but according to me) because I use it!  However, it doesn't download and install anything unless you tell it to...  Therefore, you have an option to tell it what to install and what not to install so it's not a hidden secret or anything.  And if you don't think it's safe to use, then you shouldn't install it.

---

### Post by raul_ on 2006-10-19
I prefer Easy Ubuntu because automatix installed me a lot of stuff i didn't need and it was a pain in the *** to remove all the packages. Easy ubuntu has the option to uninstall. But security wise, it's safe (you're in Linux =P there are no such things as trojans, at least that i know of)

---

### Post by Pri0n on 2006-10-19
> **raul_ said:**
> I prefer Easy Ubuntu because automatix installed me a lot of stuff i didn't need and it was a pain in the *** to remove all the packages. Easy ubuntu has the option to uninstall. But security wise, it's safe (you're in Linux =P there are no such things as trojans, at least that i know of)

There are certainly root kits.  Don't you usually have to sudo root in order to install applications? (meaning that the install script can do whatever it wants since its running as root, including installing a server type application that opens up a port and enables remote access - backdoor access).  Isn't that one of the main reason why we (should) check the md5sum (or sha1sum) hash of downloaded applications to confirm that the packages haven't been tampered with?

Isn't there also an application called "Check Rootkit" that does exactly that (checks to see if you've been "rootkit").

---

### Post by raul_ on 2006-10-19
That's not a trojan. It's more like a backdoor. And it's not probable that you'll find that in any heavily publicised linux application. and if u have a firewall running, that shouldn't be a problem, but i'm not a security expert :) People who use those kind of malicious software often use it to attack Windows :D

EDIT: oh i forgot, software available on synaptic isn't likely to contain root kits

---

### Post by Reshin on 2006-10-19
While on the subject, is there any way to make it use mirror (fi.archive.ubuntu.org) instead of the unnoingly slow main server (archive.ubuntu.org)? :???:

---

### Post by taurus on 2006-10-19
> **Reshin said:**
> While on the subject, is there any way to make it use mirror (fi.archive.ubuntu.org) instead of the unnoingly slow main server (archive.ubuntu.org)? :???:

You can change the servers by editing /etc/apt/sources.list.  Open a terminal, Applications -> Accessories -> Terminal, and type

```

gksudo gedit /etc/apt/sources.list

```

---

### Post by dagnabit dang doohickey on 2006-10-19
If it's not to much trouble, could someone post the Automatrix file that contains the list of packages that it can install. The similar file in EasyUbuntu is packagelist-dapper.xml and you can easily get to that file by downloading the tar.gz nightly build of EasyUbuntu. But, as far as I can tell, Automatrix is only available as a .deb, which I can't crack open without installing it.

---

### Post by taurus on 2006-10-19
Maybe they have that over at [http://www.getautomatix.com/](http://www.getautomatix.com/)!!!

---

### Post by dagnabit dang doohickey on 2006-10-19
> **taurus said:**
> Maybe they have that over at [http://www.getautomatix.com/](http://www.getautomatix.com/)!!!

Thanks, but they only have a .deb over there.
They have a nice list of descriptions of the software it can install, but I'm looking for the package list.

---

### Post by raul_ on 2006-10-19
i'll get it for you from a guy who hated automatix and invented manumatix, where u install the same packages with synaptic :D give me 5 min

EDIT: Here u go

> First, some background...

There's a program for Breezy called Automatix that's supposed to help newbies install some of the latest software and neat tweaks in a user-friendly manner; unfortunately, I'd seriously recommend not installing it: I've found that not only does it modify your system without doing a good job of explaining the changes that its going to make beforehand, it doesn't have an option to undo the changes once they have been made because the author "belong[s] to the school of thought which believes that removal of software shd [sic] not be automated"! What's worse is that the information he provides to uninstall these changes does not cover all of them.

As of mid-January, 2006, these (about a third of the total) did not have uninstall information:

 1) Installs multimedia codecs
 2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
18 ) Enables Numlock on (turns numlock on Gnome startup)
21) Installs MS true type fonts
22) Configures ctrl-alt-del to start gnome-system-monitor (aka windows)
25) Installs ndisgtk (WiFi configurator Graphical user interface)
26) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer. (no support for AMD64 and ppc packages)
27) Adds 3 nautilus scripts (open any file with gedit as root; open a nautilus window as root in any folder; open gnome search tool in any folder (Right click in a nautilus window and look under "scripts")
28 ) Installs SUN'S JAVA JRE version 1.5
29) Installs SUN'S JAVA JDK version 1.5
31) Enables ejection of CD when CDROM drive button is pressed.
34) Gamepads (Makes USB gamepads work)
35) Turns DMA ON on Intel and AMD machines (needs a restart)
36) NVIDIA cards (Detects Nvidia cards and installs drivers) (Needs a restart)

The final straw for me was when I discovered that it completely changed my sources.list file without asking me first or even telling me after the fact. This sort of software behavior is very naughty!


That was just an entree. Here's the link. U can find the complete list of packages (or almost complete)

[http://members.shaw.ca/Limulus/manumatix.html]("http://members.shaw.ca/Limulus/manumatix.html")

---

### Post by dagnabit dang doohickey on 2006-10-19
Thanks, raul_

That's exactly what I was looking for.

8)

---

### Post by beerorkid on 2006-10-19
now that they have automatix2 out it is pretty simple.  in fact it does not have as much stuff as it used to.  Plus there is a remove utility built into it.

There were problems back in the day, but those days are history.

It is basicaly apt-getting stuff for you.

---

### Post by beerorkid on 2006-10-19
for full list of what automatix can install go here: [http://getautomatix.com/wiki/index.php?title=Automatix2_for_%28K%2CX%29Ubuntu_6.06_i386#Capabilities](http://getautomatix.com/wiki/index.php?title=Automatix2_for_%28K%2CX%29Ubuntu_6.06_i386#Capabilities)

---

### Post by arnieboy on 2006-10-20
> **beerorkid said:**
> now that they have automatix2 out it is pretty simple.  in fact it does not have as much stuff as it used to.  Plus there is a remove utility built into it.

There were problems back in the day, but those days are history.

It is basicaly apt-getting stuff for you.
AX2 has the same number of options as AX1 (it looks lesser because of the categories). AX2 will be expanded to have even more interesting install options in the future.

---

