---
title: "Cannot save files from Chrome to my home NAS"
date: 2023-07-13
forum: General Help
---

### Post by dorlow on 2023-07-13
So, I just noticed I cannot save files from Google Chrome to my home NAS.  I just recently switched so I'm not sure if I've tried doing this yet. I'm trying to print a PDF and save the PDF to my NAS. I can browse the NAS and pick the folder.  But, then I click save.  No error but it doesn't make the PDF.  I can make the PDFs local on my local hard drive... no problem.  I was thinking maybe a permission issue.  I changed my home directory for Everyone full access and it didn't fix it.  (Not that worried about being hacked on my home network.)  I can copy files outside of Chrome to the NAS without issue.

---

### Post by miguelpires on 2023-07-14
Hi, 
this is a bug affecting "portals". 
Have the same problem in firefox and chrome 
My bug report please subscribe.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1992255](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1992255)
This is another bug about firefox, something to do with      **       [xdg-desktop-portal]("https://github.com/flatpak/xdg-desktop-portal")     **
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1971168](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1971168)
I don't know how long this going to last
Regards
Miguel

---

### Post by Holger_Gehrke on 2023-07-14
Is that 'Chromium' or actual 'Chrome' ? 'Chromium' is the open source browser which takes out a lot of Google specific ... features ... and usually is installed as snap on Ubuntu. So if it is Chromium you're using, then it's the portal issue that miguelpires describes, and is basically down to snaps being confined from accessing anything outside of $HOME and /run/user/$(id)/. Portals are a way to get around that in a controlled way, but still have some serious problems especially with accessing network resources. If you're using Chrome that usually comes as a Debian package downloaded from Google and doesn't need to use portals, so your problem would have a completely different cause.

Holger

---

### Post by miguelpires on 2023-07-14
But no, even Chrome from Google have the problem.

Please try save or upload anything from a NAS or any samba share, it simply don't work
But if you have a solution, please share, I'm waiting from 2022 for this solution.


Regards
Miguel

---

### Post by Holger_Gehrke on 2023-07-14
I'm sorry to say that I just tried it and it just worked as it should. Installed Google Chrome from the 94mb Debian Package, ran it, visited archive.org, downloaded a small video from the electric sheep collection to a Samba share, closed Chrome, played the video, removed Chrome again (Nope, I'm too used to Firefox to keep this thing installed ...). So whatever the problem is, it doesn't happen for me on XUbuntu 22.04.

Holger

---

### Post by miguelpires on 2023-07-15
Are you using Xubuntu?

I tested and for me dont worked in Ubuntu 2204 :(

If is Xubuntu maybe something is different I really dont know
Regards

---

### Post by Holger_Gehrke on 2023-07-15
Should not make a difference since XUbuntu is just regular Ubuntu but XFCE instead of Gnome; it's just a different top layer for the GUI, everything below that is the same.

Holger

---

