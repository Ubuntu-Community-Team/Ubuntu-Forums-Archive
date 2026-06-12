---
title: "autofs auto.smb annoyance"
date: 2015-12-17
forum: General Help
---

### Post by Tim_Bower on 2015-12-17
Have used autofs for years to mount samba and nfs shares, but after installing 15.10, I actually tried using the delivered auto.smb script for the first time (used to just code my own configs, explicitly mounting the shares I wanted).   Very happy that I got auto.smb to work with very little trouble, but there's just one minor problem.  autofs doesn't seem to honor the --ghost option in auto.master when using auto.smb.

The line in my auto.master file looks like this:

[INDENT]/cifs    /etc/auto.smb  --timeout=300 --ghost[/INDENT]


All of the found shares mount just fine under /cifs/<machinename>/ , but the --ghost option apparently does nothing.  Is this because I'm specifying a script rather than just a simple configuration file?

Is there any way to get the --ghost option in auto.master to work with a script like auto.smb?

Any help is appreciated.

---

