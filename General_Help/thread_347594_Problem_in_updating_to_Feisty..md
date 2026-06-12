---
title: "Problem in updating to Feisty."
date: 2007-01-27
forum: General Help
---

### Post by sanguinemoon on 2007-01-27
I wanted to test Feisty, aware that it isn't ready. But I seem to be getting PGP errors when I do. Here's my output.

raccoon@Atrocity:~$ sudo update-manager -d
Password:
warning: could not initiate dbus
extracting '/tmp/tmpYduzmv/feisty.tar.gz'
authenticate '/tmp/tmpYduzmv/feisty.tar.gz' against '/tmp/tmpYduzmv/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072

Does anyone know how I can fix this?

---

### Post by jpeddicord on 2007-01-27
Run a quick sudo apt-get update. Usually it refreshes the PGP keys needed correctly. If not, try again at a later time. Sometimes the update files don't go through correctly.

You can also try changing every instance of 'edgy' in /etc/apt/sources.list to 'feisty', and then running sudo apt-get dist-upgrade.

---

