---
title: "Feisty Questions! Partitions and network manager"
date: 2007-04-20
forum: General Help
---

### Post by Arlanthir on 2007-04-20
Solution: I went with manual configuration for the Networking and edited fstab to my likings ;)
Not perfect, but close =)

----------------------------------------------------

[I]
I've installed Feisty Fawn after some months of Edgy. I must say I'm even more impressed!
However, there are some problems I'd like to solve, being:
[LIST]
[*]Network manager always asks for keyring password on login
[*]Partitions didn't get quite right during install
[/LIST]

I think the first is self-explanatory, network manager saves the password in the keyring, which is protected by password too, so.. No 'save you the work of inputting a password' here :S I'd like to have the network manager without manual configuration but with a reminded automatic password login.

The second one is a bit more tricky to explain, but here goes:

During install, feisty asked me about what partitions I'd like to have mounted and where.
I chose my ntfs windows partition to be mounted in /windows and my fat32 storage partition to be mounted in /box. However, when I start Ubuntu, it does not actually mount those partitions in the required mount points. It does however, mount them on /media/*disklabel* when I run GParted or click their label in Nautilus. I got a hold of my mad newbie skills and went berserk on fstab, only to find that there are NO references to said partitions. With that being said, where can I change them to automatically boot on startup for all users, and with the mountpoints that I specified?  I like the disk icon and the automatic shortcut that this way produces, though, but well..

Thank you very much, and congratulations on such a wonderful distro!
[/I]

---

### Post by viciouslime on 2007-04-20
Are you sure you downloaded the final release? Only the network manager thing was an issue in one of the test releases, but has now been fixed.... least it works for me. If not you should probably file a bug report as I don't think there is any easy fix.

---

### Post by strabes on 2007-04-20
For the network manager problem, run "kwalletmanager" and remove the password on the wallet that deals with knetworkmanager. I used to have a similar problem with knetworkmanager asking me for my username and password for the WPA2 enterprise security on my university's wireless network. An update of knetworkmanager fixed it automatically.

Why do you **not** want those partitions mounted in /media? That's where everything is automagically mounted. They appear on the desktop and everything.

---

### Post by Arlanthir on 2007-04-20
Yes I am sure =/
Well, an easy fix would be forcing manual configuration, but I like the manager, so.. I'll wait and see if someone has another idea :P

---

### Post by Arlanthir on 2007-04-20
Those partitions can be in media, that's ok for me, I'd just like them to be mounted automatically =/ And well, not for root only access. Besides, I'd like to change the name of the mountpoints, instead of having the labels of the partitions ;) Also, I'm not using KDE, it's not a problem with it's network manager, it's the Feisty Fawn's Network Manager (in Gnome) that has an issue of saving the WEP pass in the keyring which is protected by.. well.. another pass =/

---

### Post by Arlanthir on 2007-04-20
I managed to change the mount options of the volumes in their properties page, right clicking on them and etc.. Now I don't know how to mount them at boot.. =/
Network manager problem still persists!

Edit: Nope, still the same, still asks for password when mounting.. -_-

---

