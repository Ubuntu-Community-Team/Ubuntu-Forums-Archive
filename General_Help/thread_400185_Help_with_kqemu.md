---
title: "Help with kqemu"
date: 2007-04-03
forum: General Help
---

### Post by neogenesis213 on 2007-04-03
I installed qemu and kqemu following the guide at
[URL="https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo"]https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo
[/URL] on feisty.

Everything worked correctly no errors. But when I run qemu this is what is says.

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Qemu runs really slowly. 
I've tried the other appz such as VMware and VirtualBox but i gave on them as networking was too complicated on them. 

[B][SIZE="3"]
Anywho does anyone know how to rectify this problem and make kqemu work.[/SIZE][/B]

---

### Post by Peter76 on 2007-04-05
There should be a better way, but the quick and dirty way is:

sudo chmod 666 /dev/kqemu

Now it should work fine.

Anybody knows how to set this up properly with an udev rule???

---

### Post by OrkanSpec on 2007-04-29
check: [http://ubuntuforums.org/showthread.php?t=348047](http://ubuntuforums.org/showthread.php?t=348047)

According to man pages, 
sudo update-rc.d kqemu.sh multiuser
is better in this case than 
sudo update-rc.d kqemu.sh defaults

kqemu solution has been verified on Kubuntu 7.04 amd64.

---

