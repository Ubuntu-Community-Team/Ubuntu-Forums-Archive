---
title: "installing other programs into ubuntu"
date: 2005-07-13
forum: General Help
---

### Post by kaybel on 2005-07-13
hello all,

will really appreciate your help with these. i have just finished reading a lot about Ubuntu linux distro, and is seriously considering moving over to it from fedora.
Actually i'm looking for a light weight linux distro i can use for my development purpose ( i develop various softwares using Java language, PHP, Jython and Python.) my questions are:

1. can i download and install other applications like java,php,jython,Tomcat etc into Ubuntu, apart from the default applications it comes with. if yes how can an alien application be installed, is it same as in fedora or any new thing.

2. what is the basic difference between KUbuntu and Ubuntu.

3. is ubuntu great for networking purposes and does it support wireless usb adapters, usb flash drives and usb hard disks.

4. Is it possible by any way other than using VMWare, to install Ubuntu inside a windows system without dual booting.

5. can Ubuntu dual boot with windows xp.


thanks alot for your kind replies.

kaybel

---

### Post by Navin_Johnson on 2005-07-13
*1. can i download and install other applications like java,php,jython,Tomcat etc into Ubuntu, apart from the default applications it comes with. if yes how can an alien application be installed, is it same as in fedora or any new thing.*

You can.  The best/most common way is to use Synaptic which is a frontend for apt-get.  This uses the debian deb structure.  It is a great system which I like better than rpm.  Many programs are Synaptic available in the repositories but you could use alien for an rpm that was not, or build from source.

*2. what is the basic difference between KUbuntu and Ubuntu.*

Ubuntu uses Gnome as the desktop, KUbuntu uses KDE.

*3. is ubuntu great for networking purposes and does it support wireless usb adapters, usb flash drives and usb hard disks.*

As far as I know it does.  It had no problem with my USB connected camera and USB connected palm pilot.  Not sure about the others but I'd assume it is fine.

*4. Is it possible by any way other than using VMWare, to install Ubuntu inside a windows system without dual booting.*

For Ubuntu inside of Windows VMWare is probably the only way, although there is an opensource alternative to VMWare that may or may not work in Windows like this.

If you wanted to go the othe way (Windows inside Linux) there are more options.  Wine/Cedega/Crossover Office, Win4Lin, VMWare (and the aforementioned free alternative whose name escapes me at the moment).
[I]
5. can Ubuntu dual boot with windows xp.[/I]

Yes.  I do just this (although I hardly ever boot into windows anymore).

---

