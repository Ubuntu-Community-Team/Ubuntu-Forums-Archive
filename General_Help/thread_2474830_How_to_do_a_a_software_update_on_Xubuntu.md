---
title: "How to do a a software update on Xubuntu"
date: 2022-05-09
forum: General Help
---

### Post by jonfisher on 2022-05-09
please how does one do a software update, or tell computer to check for them, on Xubuntu?

---

### Post by #&amp;thj^% on 2022-05-09
```
sudo apt update
```
and 
```
sudo apt upgrade
```
to see available updates
```
apt list --upgradable
```
More:
```
man apt
```

---

### Post by Impavidus on 2022-05-09
In the terminal, use **sudo apt update** to check for updates, then **sudo apt upgrade** to download and install them. In rare cases, you may need **sudo apt full-upgrade**.

If you prefer the GUI, open de menu, go to settings, then update manager. That will open a tool that checks for updates and shows them to you. You can then click to confirm to download and install.

If you just keep the default settings, Xubuntu will check for updates automatically. Maybe it even installs the security updates automatically; I don't remember. Else the update manager will pop up.

---

### Post by bobunderwood99 on 2022-05-09
In Xubuntu 20.04 the GUI update tool is named "Software Updater"; the update configuration tool is "Software & Updates".

---

### Post by jonfisher on 2022-05-09
thanks all of you so much

---

