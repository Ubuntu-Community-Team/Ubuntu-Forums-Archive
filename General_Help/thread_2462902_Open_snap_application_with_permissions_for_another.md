---
title: "Open snap application with permissions for another drive"
date: 2021-05-29
forum: General Help
---

### Post by mumike on 2021-05-29
[COLOR=#242729][FONT=-apple-system]I'm attempting to run the bitcoin daemon and have it store the blockchain data onto a separate drive of mine. However, I keep encountering issues with permissions. I'm new to Linux, but I believe the problem is two-fold.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]First, is my file system even set up properly? I reformatted the target HDD to be compatible, but it is mounted at /media/server01/hdd-server01-con The other file system is in boot, with the main partition the filesystem root.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]Second, the snap issue. I cannot run bitcoin-core.qt as root as I get this error:[/FONT][/COLOR]
root@server01:/# sudo bitcoin-core.qt
mkdir: cannot create directory '/run/user/0': Permission denied
[COLOR=#242729][FONT=-apple-system]I'm not sure how that even makes sense as I'm running from root, unless there is a setting somewhere which expects me to be entering that command from a different folder. On the other hand, running it from the applications window does open the dialog, but after selecting the target folder (/media/server01/hdd-server01-con/btc) it immediately gives me this error at startup:[/FONT][/COLOR]
Error initializing settings: Failed saving settings file:
- Error: Unable to open settings file /media/server01/hdd-server01-con/btc/settings.json.tmp for writing.

---

### Post by Holger_Gehrke on 2021-05-29
snaps are constrained through AppArmour. Thanks to this they are unable to write anywhere but in the $HOME of the user running them. Additionally they can be allowed to access removable media mounted through udisk in /media/$USER/. This is done to minimize the damage buggy software or malware packaged as a snap can do to the system.

Holger

---

### Post by mumike on 2021-05-31
Thank you! I'll go ahead and install ubuntu on the HDD itself I wanted to use then.

---

### Post by grahammechanical on 2021-05-31
What information do you have that says that bitcoin-core snap should be run as root? That seems to go against the principles of packaging an application as a snap package.

Perhaps it would better if you asked this question of the developer.

[https://snapcraft.io/bitcoin-core](https://snapcraft.io/bitcoin-core)

You may also find this informative:

[https://ubuntu.com/blog/hey-snap-wheres-my-data](https://ubuntu.com/blog/hey-snap-wheres-my-data)

It seems that the developer needs to get special permission to code his app to access another drive. If he has not requested and gained that permission, then what you want to do is impossible. That blog post will help you find out where bitcoin-core is storing the data. Perhaps you can then regularly back it up to the other hard disk.

Regards

---

