---
title: "Installed software works well but is not shown in synaptic and cannot remove it"
date: 2016-09-05
forum: General Help
---

### Post by ineuw on 2016-09-05
On the weekend, I installed Autokey from a tarball and everything is working well. Now, I need to remove it, but it is not showing up in synaptic, and apt-get says that it's not installed. I can see numerous files installed in the system files and these are what I thought to be the most relevant files listed by using the "locate" command.

/usr/local/share/applications/autokey-gtk.desktop
/usr/local/share/man/man1/autokey-gtk.1
/usr/share/applications/autokey-gtk.desktop

Below are installation files in the repository listed by synaptic under uninstalled, but they are slightly older and missing some minor enhancements.

autokey-common
autokey-gtk
autokey-qt

How would be possible to uninstall the current installation? There is no PPA.

---

### Post by cariboo on 2016-09-06
Open the tarball and check the readme, it should tell you how to uninstall it.

---

### Post by Impavidus on 2016-09-06
Synaptic, apt-get and friends only know about software installed from .deb packages. These can come from the official repositories, PPAs or stand-alone .debs. You installed software from a tarball. With some luck you can find uninstall instructions in the tarball. If not, you have to locate all files and directories used by this application manually and remove them. That's why we prefer .debs.

---

### Post by ineuw on 2016-09-06
cariboo, thanks for the suggestion. unfortunately checked all text files and there are no instructions for removal. 

Impavidus, thanks for the enlightenment. That is what I had to do the last time I removed it. (I am testing the software for its shortcomings). So now, I will try to convert the software into a .deb package.

---

