---
title: "Edubuntu on XFCE"
date: 2006-08-05
forum: General Help
---

### Post by seshomaru samma on 2006-08-05
Can I install Xubuntu and then run Edubuntu's educational packages without having to download Gnome ? 
(correct me if I'm wrong but edubuntu runs on Gnome ,right?)

I have both Xubuntu and Edubuntu on CD
Can I install XFCE and then get the educational packages from the Edubuntu CD?

---

### Post by aysiu on 2006-08-05
> **seshomaru samma said:**
> Can I install Xubuntu and then run Edubuntu's educational packages without having to download Gnome ? 
(correct me if I'm wrong but edubuntu runs on Gnome ,right?) Yes. Paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install edubuntu-desktop
``` Before it installs Edubuntu, it'll list a bunch of packages to be installed and then ask if you want to go ahead and do so. Answer **no**. Then highlight the list of packages to be installed and copy and paste them to a text file. Delete all the packages except the ones that look educational. Then type ```
sudo aptitude install
``` but before pressing **Enter**, paste back from the text editor the educational packages you want.

> I have both Xubuntu and Edubuntu on CD
Can I install XFCE and then get the educational packages from the Edubuntu CD? If the Edubuntu CD is the **Alternate CD**, then, yes. If it's the **Desktop CD**, the, no.

---

### Post by 3rdalbum on 2006-08-05
As long as the Edubuntu CD is the Alternative CD, then yes.

Go into Synaptic and insert the Edubuntu CD. Go to the Edit menu and "Add CD-ROM..." and then add the disc.

Now you'll be able to install the educational packages which are on the Edubuntu CD; however they may pull in Gnome and KDE dependancies. The GTK libraries have been updated since the CD images were created, so you may need to do a "lock version" on the libraries if you don't want to download them from the Internet.

---

