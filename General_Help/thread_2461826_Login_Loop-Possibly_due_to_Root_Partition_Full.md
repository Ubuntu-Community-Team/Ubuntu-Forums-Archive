---
title: "Login Loop-Possibly due to Root Partition Full"
date: 2021-05-08
forum: General Help
---

### Post by dcapone on 2021-05-08
I am a new Ubuntu user and I am struggling with what I've discovered to be the widespread "login loop" issue, in which logging in immediately pops up a black screen and then returns to the login. I've tried numerous of the proposed approaches including using the terminal to clean and autoclean, but with no success. I'm nearly certain the reason this is happening is due to my root partition being full, however I don't know how to address this without access to my desktop environment. I also am uncertain why my root partition fille dup so quickly in the first place as I was getting warning messages about "low disk space on file system root" for a while despite many sources suggesting creating a root partition size of only 15-20 GB. 

Please let me know if you have any suggestions

---

### Post by HermanAB on 2021-05-08
Boot with install media, then look at the disks to see what is going on.  You can delete everything in /var/log recursively to make space to maneuver - important log files will be recreated automatically.

---

### Post by guiverc on 2021-05-08
You haven't said what release or type of Ubuntu system you have installed, however please note that Ubuntu Desktop has recommended 25GB as the minimum size since before Ubuntu 17.10 (ie. all GNOME Shell releases; or since 2017-October-03).

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> 25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)

so your 15-20 GB were unofficial or you're using a release of Ubuntu that is now EOL/[I]end-of-life.

[/I]An inability to login with a GUI because of space issues isn't related to / generally, but space is need in $HOME or /home/$USER (ie. your user directory).  If you don't have a separate /home partition, then that space does need to be in /

You'll be able to login using a text terminal even if you're out of space, lack of space stops GUI logins only.

FYI:  *the amount of space you need varies on what you'll use the system for. If you don't add software to your system, maintain it well (& upgrade packages very regularly not letting them pile up etc) you can get away with less space. Myself I tend to bloat my systems with loads of software, so I need 32GB for my /.  Some package types need more space (eg. snaps), and many bloggers don't allow for upgrade time (suggesting fresh install instead of in-place upgrades meaning you don't need release-upgrade space available)*

---

### Post by vanadium on 2021-05-08
The reason for a full / could also be temporary files: check also /tmp and /var/tmp. On the terminal, also do a "sudo apt clean" to remove cached installation debs. That may allow you to recover, but then you will need to manage your limited root space to prevent that from occurring again: make sure to store your own files on other partitions, remove old kernels if they are still installed, redirect /tmp/ and /var/tmp to another partition, etc.

15-20 GB for root can work, but you should then have /home on a separate partition. Especially 15 is quite tight. You need to take your precautions if you choose to have a root that small.

---

### Post by ajgreeny on 2021-05-08
Interestingly, since I started using Ubuntu 16 years ago (now Xubuntu) I have never had a root partition larger than 20G and never use more than about 12G of that.

I have separate /home partition and i am not a gamer so there are no huge game folders in root which I believe can use a lot of disk space, but 20G has always been plenty for me.

---

