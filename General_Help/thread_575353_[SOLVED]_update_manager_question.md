---
title: "[SOLVED] update manager question"
date: 2007-10-13
forum: General Help
---

### Post by lebihan1 on 2007-10-13
Im using gutsy gibbon 64 bit version with gnome and my update manager keeps wanting to install a bunch of KDE apps I don't want... so I can uncheck them so they are not installed but then everytime an update comes in I need I have to go through the process of unchecking all the KDE stuff I don't want, is there any way to remove these updates I don't want from the update manager?

---

### Post by r-mo on 2007-10-14
First of all if update-manager is telling you there are updates for them then the apps are already installed, probably as dependencies for other apps you do want. In which case update them.

To remove them completely goto System->Administration->Synaptic Package Manager
If you then click on the first column S to sort by status you should see all the packages for which upgrades are available at the top of the list (green box with a *).  To remove them just click on the green box and select mark for removal.  Pay attention to what else will be removed!!

If you really want to keep them as they are without updating, which isn't advisable!! select the package, then, in the package menu (menu bar) you can either select force version which will keep it as it is until the next update or lock version which will keep it as it is forever.

Hope this helps

Stephen

---

### Post by lebihan1 on 2007-10-14
thanks for the help, and yeah i didn't think about the apps already being installed, but I used a script to get the latest compiz fusion stuff and it did install a bunch of KDE stuff (don't know why it was in the script), but it really is stuff that I didn't need...

---

### Post by aparigraha on 2007-10-23
thx a bunch for that tip.
i have one old Windows app that uses an old version of wine a lot better in my opinion. i only use wine for this one app so this saves me plenty of time scrolling and unchecking.
thx again

---

