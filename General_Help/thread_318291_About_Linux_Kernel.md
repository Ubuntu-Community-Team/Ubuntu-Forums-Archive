---
title: "About Linux Kernel"
date: 2006-12-13
forum: General Help
---

### Post by tenghoward on 2006-12-13
[http://www.ubuntuforums.org/showthread.php?t=318005]("http://www.ubuntuforums.org/showthread.php?t=318005")

Regarding the latest update for Kernel. Can someone show me to download which .deb file for generic Kernel? It would be better if which .deb to install first. I don't want to update through Adept as my Internet instability might caused downloading hang and Dpkg locked. :-k

---

### Post by Cable on 2006-12-13
If you're running 6.10 (Edgy) you can simply update your computer to receive the update.  If you're running anything prior to 6.10, it looks like you'll have to wait a bit as those updates have not been released yet (from the post you linked to).

---

### Post by az on 2006-12-13
> **tenghoward said:**
> I don't want to update through Adept as my Internet instability might caused downloading hang and Dpkg locked. :-k

Not relevant.  If your bandwidth cuts out, dpog won't even be run.

If you want to do it "by hand" just run

sudo apt-get -d upgrade

and that will just download the debs for you and put them in /var/cache/apt/archives

then run it again without the -d and the packages will be installed.

---

### Post by tenghoward on 2006-12-13
> **azz said:**
> Not relevant.  If your bandwidth cuts out, dpog won't even be run.

If you want to do it "by hand" just run

sudo apt-get -d upgrade

and that will just download the debs for you and put them in /var/cache/apt/archives

then run it again without the -d and the packages will be installed.

Thank you! :KS

---

