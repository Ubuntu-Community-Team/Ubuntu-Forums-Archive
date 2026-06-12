---
title: "Libre office calc crashed"
date: 2024-07-24
forum: General Help
---

### Post by skippylou on 2024-07-24
It has become corrupted and unusable.  How to I reload it?

Ubuntu 20.04.6 LTS

---

### Post by currentshaft on 2024-07-24
How did you install it? apt, Flatpak, snap?

What happens exactly when you launch it?

---

### Post by skippylou on 2024-07-24
> **currentshaft said:**
> How did you install it? apt, Flatpak, snap?

What happens exactly when you launch it?

Came installed with the OS when I bought the computer.  Nothing happens when I launch.

---

### Post by #&amp;thj^% on 2024-07-24
> **skippylou said:**
> Came installed with the OS when I bought the computer.  Nothing happens when I launch.

It came with the OS is not what currentshaft wanted, is it a snap, .deb, flatpak?
If it's a .deb:
```
sudo apt install --reinstall libreoffice

```
```
apt policy libreoffice-common
libreoffice-common:
  Installed: 4:24.2.5-0ubuntu1
  Candidate: 4:24.2.5-0ubuntu1
  Version table:
 *** 4:24.2.5-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
I don't do snaps so this is a mute point, but flatpak
```
flatpak info org.libreoffice.LibreOffice
error: org.libreoffice.LibreOffice/*unspecified*/*unspecified* not installed

```
If your still having problems then show us this:
```
libreoffice

```

---

### Post by deadflowr on 2024-07-24
Try moving or removing the user configuration folder
located at ~/.config/libreoffice

You can either try deleting it outright or simply try to rename it. Any name other than libreoffice will do, really.
Either way after that when you launch or try to launch a new instance it'll generate a fresh configuration.

---

### Post by skippylou on 2024-07-24
sudo apt install --reinstall libreoffice

This goes through an installation process but calc still doesn't work

**************************************************

I can't find ~/.config/libreoffice

*************************************************
apt policy libreoffice-common  gives this:

skippy@skippy-ThinkStation-P620:~$ apt policy libreoffice-common
libreoffice-common:
  Installed: 1:6.4.7-0ubuntu0.20.04.10
  Candidate: 1:6.4.7-0ubuntu0.20.04.10
  Version table:
     1:7.4.7-0ubuntu0.22.10.1~bpo20.04.1 100
        100 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/main amd64 Packages
        100 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports/main i386 Packages
 *** 1:6.4.7-0ubuntu0.20.04.10 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 Packages
        100 /var/lib/dpkg/status
     1:6.4.2-0ubuntu3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main i386 Packages
skippy@skippy-ThinkStation-P620:~$

---

### Post by deadflowr on 2024-07-24
> I can't find ~/.config/libreoffice

.config is a hidden folder so enable show hidden folders (ctrl + h)

---

### Post by #&amp;thj^% on 2024-07-24
Focal huh? are you on ESM "Expanded Security Maintenance (extra 5 years)" if not your no longer supported.
Or Legacy support (years 11 and 12)
But give this a try:
```
rm -rf ~/.config/libreoffice
```
Now launch it again

---

### Post by deadflowr on 2024-07-24
Focal support ends next year.

---

### Post by #&amp;thj^% on 2024-07-24
So it dose....LOL my bad.

---

### Post by skippylou on 2024-07-24
> **deadflowr said:**
> .config is a hidden folder so enable show hidden folders (ctrl + h)

Renamed ~/.config/libreoffice to~/.config/Xlibreoffice.

Ran sudo apt install --reinstall libreoffice again.  Still doesn't work.

---

### Post by &amp;KyT$0P# on 2024-07-24
What happens if you try to run it in Terminal?
```
libreoffice --calc
```
If there is any terminal output when it fails, could you please post the output?

---

### Post by skippylou on 2024-07-24
> **halogen2 said:**
> What happens if you try to run it in Terminal?
```
libreoffice --calc
```
If there is any terminal output when it fails, could you please post the output?

No go. Calc shows its busy in the side toolbar but will not appear.

---

### Post by dragonfly41 on 2024-07-25
I think that you have to broaden your search net ..

[https://ask.libreoffice.org/t/libre-office-calc-not-opening-in-ubuntu-20-04/53365/13](https://ask.libreoffice.org/t/libre-office-calc-not-opening-in-ubuntu-20-04/53365/13)

and rethink search title .. such as "LibreOffice Calc launcher spinning but not opening" (or similar). As when using AI assistants the prompts must be on target.

---

### Post by dragonfly41 on 2024-07-26
It would be nice for all to know if your issue is solved.

---

