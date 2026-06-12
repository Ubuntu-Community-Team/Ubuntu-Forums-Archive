---
title: "dot profile, and a command not working"
date: 2018-11-21
forum: General Help
---

### Post by aeronutt on 2018-11-21
So in gnome-shell, I have a veracrypt command in .profile to decrypt one of my disks. Has worked fine for years, and works fine in Ubuntu 18.10.

However, it doesn't work in KDE Plasma 18.10. (The command works when I copy/paste in a terminal.)

For what it's worth, here's the command:
veracrypt --text --non-interactive --mount /dev/sda1 --pim 1000 --password="$(kwalletcli -f veracrypt -e vcryptpartition)" /mnt/vcrypt

There is a difference, in that when I run this in gnome-shell, I use secret-tools, not kwalletcli.

Is there a better place to put such a command? I don't want it loaded at boot, but only for a particular user login.

---

