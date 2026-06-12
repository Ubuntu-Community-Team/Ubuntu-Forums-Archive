---
title: "Removing installeed programs"
date: 2008-03-27
forum: General Help
---

### Post by dctalk37 on 2008-03-27
So I've been running around the net trying out new things and downloading apps. Now i have a few things i want to get rid of. And for the life of me haven't figured it out. I got Linux DC++ from a repository and have a few things on Wine. When ever i use uninstall on Wine. the uninstaller runs but never removes the app. And i have no clue how to remove Linux DC++. Help me Please

---

### Post by Athelstan101 on 2008-03-27
You could try the following:
```
$ sudo apt-get autoremove
sudo $ apt-get --purge remove <package>
```

---

### Post by cardinals_fan on 2008-03-27
Open up Synaptic (System -> Synaptic Package Manager) and search for Linux DC++.  When it comes up, click the check box and select Remove.  As for the WINE apps, all the installed files are in /home/your-user-name/.wine

---

### Post by dctalk37 on 2008-03-27
So i tryed the sudo thing and heres what happened.

neonnegro@neon-lap:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto python-zopeinterface python-twisted-names python-twisted-core
  python-twisted-web libwxgtk2.8-0 python-twisted-runner torcs-data-tracks
  python-pyogg torcs-data-cars python-twisted-mail python-editobj blt
  python-imaging billard-gl-data libwxbase2.8-0 python-twisted-lore
  python-twisted-conch libcrypto++6 freepats python-twisted-news
  python-twisted-words python-twisted libcal3d12 egoboo-data tcl8.4 tk8.4
  amule-common libode0debian1 python-twisted-bin
The following packages will be REMOVED:
  amule-common billard-gl-data blt egoboo-data freepats libcal3d12
  libcrypto++6 libode0debian1 libwxbase2.8-0 libwxgtk2.8-0 python-crypto
  python-editobj python-imaging python-pyogg python-twisted python-twisted-bin
  python-twisted-conch python-twisted-core python-twisted-lore
  python-twisted-mail python-twisted-names python-twisted-news
  python-twisted-runner python-twisted-web python-twisted-words
  python-zopeinterface tcl8.4 tk8.4 torcs-data-cars torcs-data-tracks
0 upgraded, 0 newly installed, 30 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 331MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118923 files and directories currently installed.)
Removing amule-common ...
Removing billard-gl-data ...
Removing blt ...
Removing egoboo-data ...
Removing freepats ...
Removing libcal3d12 ...
Removing libcrypto++6 ...
Removing libode0debian1 ...
Removing libwxgtk2.8-0 ...
Removing libwxbase2.8-0 ...
Removing python-twisted ...
Removing python-twisted-conch ...
Removing python-crypto ...
Removing python-editobj ...
Removing python-imaging ...
Removing python-pyogg ...
Removing python-twisted-words ...
Removing python-twisted-lore ...
Removing python-twisted-web ...
Removing python-twisted-runner ...
Removing python-twisted-news ...
Removing python-twisted-names ...
Removing python-twisted-mail ...
Removing python-twisted-core ...
Removing python-twisted-bin ...
Removing python-zopeinterface ...
Removing tk8.4 ...
Removing tcl8.4 ...
Removing torcs-data-cars ...
Removing torcs-data-tracks ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
neonnegro@neon-lap:~$ sudo $ apt-get --purge remove Linux DC++
sudo: $: command not found
neonnegro@neon-lap:~$ sudo $ apt-get --purge remove
sudo: $: command not found
neonnegro@neon-lap:~$

---

### Post by forrestcupp on 2008-03-27
You're putting a '$' in there and it shouldn't be there.  It should be
```
sudo apt-get --purge remove *packagename*
```
You need to know the actual package name, and it's not Linux DC++ because package names don't have spaces.

You could try opening up Synaptic and searching for **Linux DC++**.  You can completely remove it from Synaptic.

About the Wine apps.  The Wine uninstaller seems to not work well.  You can just delete the file or app's directory without any big consequences.  Just do what cardinal_fan said.  In Nautilus, go to your /home directory and go to the View menu and check the box to 'show hidden files.'  Then go to the .wine directory, to the drive_c directory, then to the Program Files directory, and you should find the directory for your wine app that you installed.  Just delete that directory and it is uninstalled.

---

### Post by dctalk37 on 2008-04-02
Well I have a problem then i didn't get LINUX DC++ from Synaptic. I got it from a website repository I've already stated this. So I guess then my question would be how do i find out the name of the package. I already know how to remove programs that i got from Synaptic that's easy. Plus not ones answered how to remove programs from wine. If i just remove the files form my HD that's fine but i still have icons on my wines tab that won't go away.

---

