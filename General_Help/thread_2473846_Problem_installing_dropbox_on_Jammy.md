---
title: "Problem installing dropbox on Jammy"
date: 2022-04-15
forum: General Help
---

### Post by Tom_Carr on 2022-04-15
I just installed the daily build of Jammy.  I then went to the software store and installed dropbox.  It asked me for my email and password, then brought up the web site where I can see my files, but it did not sync the files with my computer.  I then decided to try uninstalling and reinstalling.  When I tried to uninstall, I got a message saying "Unable in remove Dropbox: no packages to remove".

What should I do?

---

### Post by ajgreeny on 2022-04-15
Was the dropbox version you installed a .deb package or a snap package? 

I have removed all snap infrastructure from my machines and have no idea what the dropbox version is for 22.04.

If it's a snap you will need to run command ```
snap list
``` to find the actual package name then ```
snap remove dropbox
``` using the real name of the package as shown in the list.

---

### Post by deadflowr on 2022-04-15
There is no dropbox snap.
>  I then decided to try uninstalling and reinstalling. When I tried to uninstall, I got a message saying "Unable in remove Dropbox: no packages to remove".
Which method did you attempt to do the uninstall/reinstall with, command line or the software store?
If using the command line the package is probably either caja-desktop or nautilus-dropbox.

---

### Post by Tom_Carr on 2022-04-15
It did not show up doing a "snap list".  This is what I got.

> tom@tom-OptiPlex-3040:~$ snap list
Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
chromium                   100.0.4896.127    1967   latest/stable    canonical&#10003;  -
core20                     20220318          1405   latest/stable    canonical&#10003;  base
firefox                    99.0-2            1188   latest/stable/…  mozilla&#10003;    -
gnome-3-38-2004            0+git.1f9014a     99     latest/stable/…  canonical&#10003;  -
gtk-common-themes          0.1-79-ga83e90c   1534   latest/stable/…  canonical&#10003;  -
snap-store                 41.3-59-gf884f48  575    latest/stable/…  canonical&#10003;  -
snapd                      2.54.4            15177  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               10     latest/stable/…  canonical&#10003;  -
tom@tom-OptiPlex-3040:

Keep in mind that when I tried to remove it I got the message "Unable to remove dropbox: no packages to remove".
But it still shows up as being installed

---

### Post by Tom_Carr on 2022-04-15
> [COLOR=#000000]Which method did you attempt to do the uninstall/reinstall with, command line or the software store?[/COLOR]

Software store

---

### Post by Tom_Carr on 2022-04-15
I did "find -name dropbox" and got this:

> tom@tom-OptiPlex-3040:~$ find -name dropbox
./.dropbox-dist/dropbox-lnx.x86_64-146.4.4836/dropbox


But I don't know what it means.  I am very much a novice using the terminal.  I had to look up the find command in google to learn how to use it.

---

### Post by #&amp;thj^% on 2022-04-15
> **Tom_Carr said:**
> I just installed the daily build of Jammy.  I then went to the software store and installed dropbox.  It asked me for my email and password, then brought up the web site where I can see my files, but it did not sync the files with my computer.  I then decided to try uninstalling and reinstalling.  When I tried to uninstall, I got a message saying "Unable in remove Dropbox: no packages to remove".

What should I do?

What DE are you using, I'll assume Gnome here, I pull this in a search "nautilus-dropbox/jammy 2019.02.14-1ubuntu1 amd64
  Dropbox integration for Nautilus
"
```
sudo apt install nautilus-dropbox
```
and should be good to go.
>  Installing this package will download the proprietary dropbox binary
 from dropbox.com.

---

### Post by Tom_Carr on 2022-04-15
I only know how to install software using the software store.  Could you point me to something that shows how to install from the terminal, or give me exact code.

---

### Post by #&amp;thj^% on 2022-04-15
> **Tom_Carr said:**
> I only know how to install software using the software store.  Could you point me to something that shows how to install from the terminal, or give me exact code.

I did you may have missed it.
```
sudo apt install nautilus-dropbox
```
EDIT: To help more, you will need to start dropbox to finish the install, it downloads dropbox binary
from dropbox.com.
One More Tip: i used this to search:
```
apt search dropbox
nautilus-dropbox/jammy,now 2019.02.14-1ubuntu1 amd64 [installed]
  Dropbox integration for Nautilus

```
Learn the terminal, it's your best friend, >>when used properly.

---

### Post by Tom_Carr on 2022-04-15
I did it, and this is what I got:

tom@tom-OptiPlex-3040:~$ sudo apt install nautilus-dropbox
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
nautilus-dropbox is already the newest version (2019.02.14-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 132 not upgraded.

---

### Post by #&amp;thj^% on 2022-04-15
I can see why>>>"and 132 not upgraded. "
Please run:
```
sudo apt update 
sudo apt upgrade
``` 
Reboot

---

### Post by Tom_Carr on 2022-04-15
Will do as you suggest and check back later.

---

### Post by #&amp;thj^% on 2022-04-15
Well that's up to you, but myself I prefer terminal installs.
Before you go try this now:
```
sudo apt remove --purge nautilus-dropbox
```
then reinstall using:
```
sudo apt install --reinstall nautilus-dropbox
```
watch the terminal for a "you need to Start Dropbox to complete the installation.
It then down loads from dropbox.com the binary's to install Dropbox.

---

### Post by Tom_Carr on 2022-04-15
I followed your instructions.  It still doesn't work.  This is what I got:

tom@tom-OptiPlex-3040:~$ sudo apt remove --purge nautilus-dropbox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gnomebluetooth-1.0 ltrace python3-gpg
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  nautilus-dropbox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 288 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 159875 files and directories currently installed.)
Removing nautilus-dropbox (2019.02.14-1ubuntu1) ...
Dropbox isn't running!
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
(Reading database ... 159847 files and directories currently installed.)
Purging configuration files for nautilus-dropbox (2019.02.14-1ubuntu1) ...
tom@tom-OptiPlex-3040:~$ sudo apt install --reinstall nautilus-dropbox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gnomebluetooth-1.0 ltrace
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  nautilus-dropbox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/66.7 kB of archives.
After this operation, 288 kB of additional disk space will be used.
Selecting previously unselected package nautilus-dropbox.
(Reading database ... 159847 files and directories currently installed.)
Preparing to unpack .../nautilus-dropbox_2019.02.14-1ubuntu1_amd64.deb ...
Unpacking nautilus-dropbox (2019.02.14-1ubuntu1) ...
Setting up nautilus-dropbox (2019.02.14-1ubuntu1) ...
Please restart all running instances of Nautilus, or you will experience problem
s. i.e. nautilus --quit
Dropbox installation successfully completed! You can start Dropbox from your app
lications menu.
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
tom@tom-OptiPlex-3040:~$ ^C

---

### Post by Tom_Carr on 2022-04-15
I have to turn off the computer for now.   I will try again tomorrow.  Thanks for all your help.  We haven't fixed it yet but I really appreciate your efforts.

---

### Post by #&amp;thj^% on 2022-04-15
I'll check back, but all looks good to me IE: Please restart all running instances of Nautilus, or you will experience problem
s. i.e. nautilus --quit
Dropbox installation successfully completed! You can start Dropbox from your app
lications menu.

---

### Post by Tom_Carr on 2022-04-17
It is working now.  I just needed to restart the computer.  Thanks for you help.  I'll leave this thread open for a few more days just in case I have additional problems.  Please do check back later if you have time, just to make sure I am OK.

---

