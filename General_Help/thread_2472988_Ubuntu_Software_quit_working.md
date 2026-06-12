---
title: "Ubuntu Software quit working"
date: 2022-03-19
forum: General Help
---

### Post by psychohermit on 2022-03-19
Greetings folks,  Running ubuntu 20.04.3.  Ubuntu software quit working.  I have been unable to locate where the menus are constructed so I don't have the actual name of the application to remove and reinstall it.  I haven't been able to guess the name of it either.  Web searches are less than helpful, they are how to add menus to ubuntu and helpful things like that.  Any assistance would be greatly appreciated.  Thanks in advance, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
Open a terminal & run:
```
gnome-software
```
Post back the result.

---

### Post by psychohermit on 2022-03-19
glenn@LinuxBox:~$ gnome-software  Command 'gnome-software' not found, but can be installed with:  sudo apt install gnome-software

---

### Post by #&amp;thj^% on 2022-03-19
I guess we do the same here as in the other thread.
Before you do this please check that snap store will open with:
```
snap-store
```
```
snap remove gnome-software
sudo apt install gnome-software
```

---

### Post by psychohermit on 2022-03-19
glenn@LinuxBox:~$ snap-store cannot change profile for the next exec call: No such file or directory snap-update-ns failed with code 1 glenn@LinuxBox:~$  glenn@LinuxBox:~$ snap remove gnome-software snap "gnome-software" is not installed  Thanks, --glenn  btw, why are formatting removed?  It all runs together in one line.  Really anoying.

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> glenn@LinuxBox:~$ btw, why are formatting removed?  It all runs together in one line.  Really anoying.

IJDK :( >> ```

``` Code Tags
Now to problem at hand, run:
1st: just for good practice back-up:
```
sudo cp -r ~/.local/share/gnome-software local/share/gnome-software.bk
```
now to see if we can get this thing in good working order run:
```
sudo apt autoremove gnome-software && sudo apt install gnome-software
```

---

### Post by psychohermit on 2022-03-19
glenn@LinuxBox:~$ sudo cp -r ~/.local/share/gnome-software ~/local/share/gnome-software.bk [sudo] password for glenn:  cp: cannot stat '/home/glenn/.local/share/gnome-software': No such file or directory glenn@LinuxBox:~$ sudo apt autoremove gnome-software && sudo apt install gnome-software Reading package lists... Done Building dependency tree        Reading state information... Done Package 'gnome-software' is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Reading package lists... Done Building dependency tree        Reading state information... Done The following additional packages will be installed:   gnome-software-common gnome-software-plugin-snap libappstream-glib8 Suggested packages:   gnome-software-plugin-flatpak The following NEW packages will be installed:   gnome-software gnome-software-common gnome-software-plugin-snap   libappstream-glib8 0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded. Need to get 6,659 kB of archives. After this operation, 13.6 MB of additional disk space will be used. Do you want to continue? [Y/n] y Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-common all 3.36.1-0ubuntu0.20.04.0 [5,559 kB] Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 libappstream-glib8 amd64 0.7.16-1ubuntu1 [135 kB] Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software amd64 3.36.1-0ubuntu0.20.04.0 [892 kB] Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-plugin-snap amd64 3.36.1-0ubuntu0.20.04.0 [72.9 kB] Fetched 6,659 kB in 2s (3,239 kB/s)                    Selecting previously unselected package gnome-software-common. (Reading database ... 188704 files and directories currently installed.) Preparing to unpack .../gnome-software-common_3.36.1-0ubuntu0.20.04.0_all.deb .. . Unpacking gnome-software-common (3.36.1-0ubuntu0.20.04.0) ... Selecting previously unselected package libappstream-glib8:amd64. Preparing to unpack .../libappstream-glib8_0.7.16-1ubuntu1_amd64.deb ... Unpacking libappstream-glib8:amd64 (0.7.16-1ubuntu1) ... Selecting previously unselected package gnome-software. Preparing to unpack .../gnome-software_3.36.1-0ubuntu0.20.04.0_amd64.deb ... Unpacking gnome-software (3.36.1-0ubuntu0.20.04.0) ... Selecting previously unselected package gnome-software-plugin-snap. Preparing to unpack .../gnome-software-plugin-snap_3.36.1-0ubuntu0.20.04.0_amd64 .deb ... Unpacking gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.0) ... Setting up libappstream-glib8:amd64 (0.7.16-1ubuntu1) ... Setting up gnome-software-common (3.36.1-0ubuntu0.20.04.0) ... Setting up gnome-software (3.36.1-0ubuntu0.20.04.0) ... Processing triggers for desktop-file-utils (0.24-1ubuntu3) ... Processing triggers for mime-support (3.64ubuntu1) ... Processing triggers for hicolor-icon-theme (0.17-2) ... Processing triggers for gnome-menus (3.36.0-1ubuntu1) ... Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.4) ... Processing triggers for libc-bin (2.31-0ubuntu9.7) ... Processing triggers for man-db (2.9.1-1) ... Setting up gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.0) ... glenn@LinuxBox:~$  gnome-software and ubuntu-software are two different critters  Thanks, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> glenn@LinuxBox:~```
$ sudo cp -r ~/.local/share/gnome-software ~/local/share/gnome-software.bk [sudo] password for glenn:  cp: cannot stat '/home/glenn/.local/share/gnome-software': No such file or directory glenn@LinuxBox:~$ sudo apt autoremove gnome-software && sudo apt install gnome-software Reading package lists... Done Building dependency tree        Reading state information... Done Package 'gnome-software' is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Reading package lists... Done Building dependency tree        Reading state information... Done The following additional packages will be installed:   gnome-software-common gnome-software-plugin-snap libappstream-glib8 Suggested packages:   gnome-software-plugin-flatpak The following NEW packages will be installed:   gnome-software gnome-software-common gnome-software-plugin-snap   libappstream-glib8 0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded. Need to get 6,659 kB of archives. After this operation, 13.6 MB of additional disk space will be used. Do you want to continue? [Y/n] y Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-common all 3.36.1-0ubuntu0.20.04.0 [5,559 kB] Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 libappstream-glib8 amd64 0.7.16-1ubuntu1 [135 kB] Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software amd64 3.36.1-0ubuntu0.20.04.0 [892 kB] Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-plugin-snap amd64 3.36.1-0ubuntu0.20.04.0 [72.9 kB] Fetched 6,659 kB in 2s (3,239 kB/s)                    Selecting previously unselected package gnome-software-common. (Reading database ... 188704 files and directories currently installed.) Preparing to unpack .../gnome-software-common_3.36.1-0ubuntu0.20.04.0_all.deb .. . Unpacking gnome-software-common (3.36.1-0ubuntu0.20.04.0) ... Selecting previously unselected package libappstream-glib8:amd64. Preparing to unpack .../libappstream-glib8_0.7.16-1ubuntu1_amd64.deb ... Unpacking libappstream-glib8:amd64 (0.7.16-1ubuntu1) ... Selecting previously unselected package gnome-software. Preparing to unpack .../gnome-software_3.36.1-0ubuntu0.20.04.0_amd64.deb ... Unpacking gnome-software (3.36.1-0ubuntu0.20.04.0) ... Selecting previously unselected package gnome-software-plugin-snap. Preparing to unpack .../gnome-software-plugin-snap_3.36.1-0ubuntu0.20.04.0_amd64 .deb ... Unpacking gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.0) ... Setting up libappstream-glib8:amd64 (0.7.16-1ubuntu1) ... Setting up gnome-software-common (3.36.1-0ubuntu0.20.04.0) ... Setting up gnome-software (3.36.1-0ubuntu0.20.04.0) ... Processing triggers for desktop-file-utils (0.24-1ubuntu3) ... Processing triggers for mime-support (3.64ubuntu1) ... Processing triggers for hicolor-icon-theme (0.17-2) ... Processing triggers for gnome-menus (3.36.0-1ubuntu1) ... Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.4) ... Processing triggers for libc-bin (2.31-0ubuntu9.7) ... Processing triggers for man-db (2.9.1-1) ... Setting up gnome-software-plugin-snap (3.36.1-0ubuntu0.20.04.0) ...
``` glenn@LinuxBox:~$  gnome-software and ubuntu-software are two different critters  Thanks, --glenn
I had to see if I could read this mess first.
Yep I knew there was a difference, 
Now dose it work?

---

### Post by psychohermit on 2022-03-19
ubuntu-software no  gnome-software yes  Thanks, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> ubuntu-software no  gnome-software yes  Thanks, --glenn

I was under the impression that from 16.04 to 20.04 ubuntu-software was replaced with gnome-software.
Are you fully updated?
```
sudo apt update
sudo apt full-upgrade
```

---

### Post by psychohermit on 2022-03-19
Yes, fully updated.  Thanks,--glenn  Why do my posts come out all on one line?

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> Yes, fully updated.  Thanks,--glenn  Why do my posts come out all on one line?

You have to place the terminal output in between code tags, see my signature;
if you are fully updated lets see what happens then with:
```
sudo apt install --reinstall software-center
```
Show any errors.

---

### Post by psychohermit on 2022-03-19
Yes, I knew that, but it all runs together in one line.  ```
 glenn@LinuxBox:~$ sudo apt install --reinstall software-center Reading package lists... Done Building dependency tree        Reading state information... Done Package software-center is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source  E: Package 'software-center' has no installation candidate 
```  Thanks, --glenn

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> Yes, I knew that, but it all runs together in one line.  Thanks, --glenn
I honestly have no answer for that, except Zombie Gremlins. ;) (Joke)
Are you all good now?

---

### Post by psychohermit on 2022-03-19
Thanks for your help.  Ubuntu Software is still broken but Gnome Software works.  --glenn

---

### Post by #&amp;thj^% on 2022-03-19
> **psychohermit said:**
> Thanks for your help.  Ubuntu Software is still broken but Gnome Software works.  --glenn

I found one of your older posts: [https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-software-is-not-working-ubuntu-20-04-3-a-4175703588/](https://www.linuxquestions.org/questions/ubuntu-63/ubuntu-software-is-not-working-ubuntu-20-04-3-a-4175703588/)
This been going on for a bit then, right?
try this for me:
```
sudo apt install --reinstall gnome-control-center
```

---

### Post by ajgreeny on 2022-03-19
> **psychohermit said:**
> Yes, fully updated.  Thanks,--glenn  Why do my posts come out all on one line?

This is a known bug on some hardware caused by your settings in the forum software.

Go to Settings (top right) and scroll down to General Settingx on the left hand pane.
Scroll down to Message Editor Interface and set it to Standard.  I suspect you have set it to Full WYSIWYG, which can cause this annoying wall of text.

---

### Post by #&amp;thj^% on 2022-03-19
> **ajgreeny said:**
> This is a known bug on some hardware caused by your settings in the forum software.

Go to Settings (top right) and scroll down to General Settingx on the left hand pane.
Scroll down to Message Editor Interface and set it to Standard.  I suspect you have set it to Full WYSIWYG, which can cause this annoying wall of text.

I took a sabbatical, so this is Great info to keep in my back pocket.
Thanks ajgreeny ;)

---

### Post by psychohermit on 2022-03-19
Reinstalled Gnome Control Center.

Still broken.

Yes it happen in the past and I ended up reinstalling ubuntu.

Thanks,
--glenn

Yay, the formatting works now.  WYSIWIG editor was selected.

Where are the menus generated from?  If I knew what to call it I would just reinstall it.

---

### Post by #&amp;thj^% on 2022-03-19
There are two different software apps in Ubuntu 20.04, Software Center  and Snap Store . The Snap Store and the Software app can be installed alongside each other without removing either app. If Ubuntu Software got removed in 20.04 it can be reinstalled by running sudo apt install gnome-software. If the snap-store is not currently installed it can be installed if by running:
```
sudo snap install snap-store
```
This is what I see from snap-store.(Screenshot)

---

### Post by psychohermit on 2022-03-19
I removed and reinstalled snap-store and ubuntu software is working again.

Thanks,
--glenn

---

