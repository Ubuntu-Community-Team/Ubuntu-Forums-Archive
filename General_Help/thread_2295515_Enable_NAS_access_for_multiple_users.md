---
title: "Enable NAS access for multiple users"
date: 2015-09-19
forum: General Help
---

### Post by lou6 on 2015-09-19
I'll be installing a NAS soon (wd my cloud) on a home network and want to make it available to all users via nfs

If I create an fstab entry to mount the NAS to a system folder and set the folder permissions to 666 (or 777) will each user be able to have a personal folder that symlinks to the system folder?

If so, does it matter who owns the system folder?

Please excuse me if these are elementary questions - although I have decades of computer experience I'm fairly new to Ubuntu.

TIA for your help.

---

### Post by uaebuntu on 2015-09-19
I have a QNAP 219 TS NAS attached to the network using nfs. The NAS is mounted at /media/NAS I have separate directories for each user, some common directories all have access to,  and a backup directory for each machine. (plus the standard QNAP directories)

Each user I have set up on the different machines with the "useradd" command has the same user ID as we have several machines in the house and this userID is recognised by the NAS.

The user then creates their own directory on the NAS and it gives each the access privileges they want. I have the NAS as a static IP on the network and have created a set of directories in the / directory on the NAS e.g. /Servers/  there are others which can be given different permissions for the back up, QNAP and public areas.

So far it has worked OK, and a Network folder called NAS shows in the file manager which corresponds to the NAS directory mounted. This is the line in /etc/fstab

192.168.1.150:/Servers  /media/NAS  nfs defaults 0 0

---

