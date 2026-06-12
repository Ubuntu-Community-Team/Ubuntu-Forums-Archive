---
title: "Upgrading, keeping everything"
date: 2008-06-17
forum: General Help
---

### Post by AmpersUK on 2008-06-17
PREAMBLE Occasionally I have a feeling that my Ubuntu is broken and I backup my home/data files and re-install, then recovering my data files. However this then loses all the extra programs I have downloaded and I have to start all over again. I feel sure the brains behind Ubuntu must have worked out a better way.  QUESTION Is there a command line where I can get the operating system upgraded with the same version (8.04) which doesn't destroy my data files and doesn't lose all the extra programs I have downloaded and set up?  Ampers.

---

### Post by change_mode on 2008-06-17
You can keep your data by setting up a seperate /home partition. There's also some program settings in there, but this will not let you keep the actual programs, but only the data files and the program settings.

Can't tell you more, because I'm pretty new to Ubuntu and never had to reinstall. Good luck.

---

### Post by argail1980 on 2008-06-17
install additional software in /opt and backup /etc and /opt along with /home

---

### Post by TransitMan on 2008-06-17
Depending on how often you back up your /home partition will often dictate what and how much you will lose.

Also, if you are restoring "ANY" OS because it is "broken" or not functioning the way you feel, some programs you have installed may need to be installed again.

This is based on my experience in both Linux and Windows NT systems.

---

### Post by paul.matthijsse on 2008-06-17
AmpersUK, what you want to do is, I suppose, reinstall your current 8.04 system. As far as I know there's no commandline option (or gui option) to do this, apart from plain reinstalling. Be aware that the extra programs you installed can very well be the source of what you call "my Ubuntu is perhaps broken". So keeping them is probably not a good idea. 

I suggest to change your Ubuntu setup. 
1. Make a root partition (~20GB) where you install Ubuntu. 
2. Make a /home partition (rest of disk) where you install your data.
3. Make a little bash script that installs all the programs you normally want to have. 

In case of problems/instability, you can reinstall Ubuntu by formatting the root partition, conflicting stuff there will be eliminated. All your data are still on /home (certainly do not format this partition!). Then run the script to reinstall your programs. My script is called 'ubuntu-postinstall.sh" and looks so: 

#!/bin/bash
sudo apt-get install joe amarok digikam verbiste liferea gkrellm kdegames spamassassin gdesklets stardict thunderbird geany rkhunter chkrootkit build-essential htop mplayer openssh-server ssh snort pwgen
exit

This way I can do a (semi) fresh install of Ubuntu, keep all my data and keep all the program settings (shortcuts, bookmarks, etc.) of the programs that are reinstalled via the script.

---

### Post by AmpersUK on 2008-06-17
> **change_mode said:**
> You can keep your data by setting up a seperate /home partition. There's also some program settings in there, but this will not let you keep the actual programs, but only the data files and the program settings.

Can't tell you more, because I'm pretty new to Ubuntu and never had to reinstall. Good luck.

 

Can anyone tell me how I may do this as it sounds like a definite part of my requirement. 

Ampers

---

### Post by change_mode on 2008-06-17
First you have to partition your hard drive. You need:

1 partition for / (the main system files)
1 swap partition (virtual memory)
1 partition for your data (/home)

You can do this with the program gparted. 20gb should be good for the system partition, swap depends on your memory size (you should already have a swap partition though) and the rest you can use for the /home partition.

Then when you install Ubuntu and it asks you where to install you select "manually edit partition table".
Set the mount point of the 20gb partition to / and the mount point of the data partition to /home. I think that's it :)

---

### Post by Pjotr123 on 2008-06-17
However, getting rid of possibly defective/wrong configuration files in the /home, may be useful. That's why this is a better way, I think:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

A clean start.  :-)

---

### Post by manfer on 2008-06-17
I don't think it would be possible for any operating system to repair itself for every breakdown that could happen on it.

Separating the user data files in other partition is the solution in all operating systems to prevent to have to backup and restore user files when you have to reinstall operating system. In ubuntu you do it making a partition for /home filesystem when you install it.

To prevent the programs lost is much more difficult. If the system is breakdown, how could the operating system determine what is wrong an what is not? It would be a lot of possibilities to care about for the system to repair itself.

Some operating systems does a backup of it to permit you go back to a previous state, like system restore on Windows XP, Time Machine on Mac OS X Leopard, and I suppose Windows Vista must have something better that Windows XP system restore (I'm not familiarized with Vista, maybe the shadow copy feature).

With the program Time Vault you can have that functionality on ubuntu.

This programs makes a restore to a previous state and don't need reinstall. The bad news of this kind of programs is the hard drive space they need, though todays systems have enough space on their hard drives to achieve this or you can use a separate drive for this purpose.

A fresh reinstall can always imply many things to do. Reinstall the soft you like (the script someone suggest is a good solution). And some software would need reconfiguration (some programs would have their config files on the users /home filesystem but, what about those which configuration is on /etc filesystem?)

---

### Post by paul.matthijsse on 2008-06-17
> **change_mode said:**
> You can do this with the program gparted. [...] Then when you install Ubuntu and it asks you where to install you select "manually edit partition table".No need for gparted, partitioning can be done directly during installation.

---

### Post by tim_wright on 2008-06-17
Try installing the following program:

sudo apt-get install aptoncd

It allows you to backup all your installed packages to a CD so getting your system up and running is a lot faster as you don't have to redownload all your apps.

---

### Post by AmpersUK on 2008-06-17
> **Pjotr123 said:**
> A clean start.  :-)

 Thanks, I have printed this out.  Ampers

---

