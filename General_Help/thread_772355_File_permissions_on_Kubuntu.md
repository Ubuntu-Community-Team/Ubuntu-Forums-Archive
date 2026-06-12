---
title: "File permissions on Kubuntu"
date: 2008-04-28
forum: General Help
---

### Post by reaper_rr on 2008-04-28
I have installed kubuntu 8.04 (with KDE4) and i wanted to set the resolution to 1024X768, but I can't do that. I've read that I should edit "xorg.conf", but I cant save the changes to that file because I need some permissions. How can I gain the permission to edit that file?

---

### Post by knutschr on 2008-04-28
Start Kate with
```
kdesu kate
```

---

### Post by reaper_rr on 2008-04-28
> **knutschr said:**
> Start Kate with
```
kdesu kate
```
I get an "Command not found" error when I try to to that.
I've also tried with
```
kdesu kate /etc/x11/xorg.conf
``` too, but the same error appears. 

```
risteristevski@risteristevski-desktop:~$ kdesu kate /etc/x11/xorg.conf
sudo: kate: command not found
```

---

### Post by Reg Editor on 2008-04-28
Hi,I had the same sort of problem until I found this

[https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434](https://answers.launchpad.net/ubuntu/+source/gedit/+question/3434)


This is the one that worked for me

QUOTE

If you want to avoid using the terminal then do this instead:-

ALT+F2 (in Gnome)
Type the following command

gksudo gedit

And you will then be prompted for your password, and can use gedit to edit "system" files.

QUOTE

---

### Post by reaper_rr on 2008-04-28
That is for Ubuntu. It doesn't work in Kubuntu :(

---

### Post by Reg Editor on 2008-04-28
Linux and ubuntu are still very new to me :-s  O:)

---

