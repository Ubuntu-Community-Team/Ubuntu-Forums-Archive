---
title: "No display"
date: 2022-12-24
forum: General Help
---

### Post by martymcc on 2022-12-24
I have Ubuntu, probably 20.04, on a laptop. I haven't used it in several months, and it was working normally when I last used it. Now when I turn it on, it flashes the BIOS text, then "ubuntu" in big letters at the bottom of the screen, then some lines of text scroll by rapidly, and then all I get is a black screen. When I access the system remotely using NoMachine on a Windows laptop or a Mac, NoMachine says "Cannot detect any display running. Do you want NoMachine to create a new display and proceed to connect to the desktop?" I click on the "Yes" button, NoMachine tells me I'm connecting to Ubuntu 20.04.4, and I get an Ubuntu display on the Windows or Apple machine,

What could be the reasons why I don't get a display on the Ubuntu machine, and what would I do to fix it?

---

### Post by UltimateCat on 2022-12-24
Not using your pc in several months may be the culprit.
When the os doesn't get the updates from the repo's that it needs things break.

You could try to restore your installation provided that you have a backup or the USB thumb drive or the CD/DVD disk that you installed Ubuntu with.
 OR> just perform a fresh installation.

[https://help.ubuntu.com/stable/ubuntu-help/backup-restore.html.en](https://help.ubuntu.com/stable/ubuntu-help/backup-restore.html.en)

TimeShift is a real gem!

[https://linuxconfig.org/ubuntu-22-04-system-backup-and-restore](https://linuxconfig.org/ubuntu-22-04-system-backup-and-restore)

---

### Post by martymcc on 2022-12-24
The machine was left running all this time, though I restarted it trying to get it to show a display. When I logged in remotely, Software Update told me that a few updates were ready to install. I authorized the updates, and now it reports that the software is all up to date, but there is an upgrade to 22.04. I authorized that, and nothing seems to be happening, but I think that much is normal. Let's see what happens tomorrow.

By the way, it's Christmas Eve, so Merry Christmas to all!

Maybe I will get a Christmas gift of an upgrade.

---

### Post by ajgreeny on 2022-12-25
Try logging into one of the tty command line sessions by using Ctrl+Alt+F1 at the login screen, enter your username then your password which will not echo on screen, and once logged in there run the command
***sudo apt update && sudo apt upgrade***
Tell us any error messages you get or even photograph those errors and add here as attachments.

---

### Post by martymcc on 2022-12-25
Thanks. Those keys don't work in remote access, but I opened Terminal in the GUI and was already logged in when it opened. I entered that command line and grabbed the latter part of what showed on the screen. One package was updated, gnome-software-common. I didn't "sudo apt autoremove" as suggested. Still no display on the laptop, and telling Software Update to upgrade (in the remote connection) still does nothing. Here's the text I grabbed:

1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libxmlb1
Use 'sudo apt autoremove' to remove it.
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages will be upgraded:
  gnome-software-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,559 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 gnome-software-common all 3.36.1-0ubuntu0.20.04.1 [5,559 kB]
Fetched 5,559 kB in 0s (13.5 MB/s)          
(Reading database ... 206621 files and directories currently installed.)
Preparing to unpack .../gnome-software-common_3.36.1-0ubuntu0.20.04.1_all.deb ..
.
Unpacking gnome-software-common (3.36.1-0ubuntu0.20.04.1) over (3.36.1-0ubuntu0.
20.04.0) ...
Setting up gnome-software-common (3.36.1-0ubuntu0.20.04.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
martin@Ubunton:~$

---

### Post by martymcc on 2022-12-25
Update: I found detailed instructions on updating to 22.04, ending with sudo do-release-upgrade. After several hours the Ubuntu machine rebooted into 22.04, and I have a display on the machine and can also log in remotely. So I guess UltimateCat was right: things broke, and a rebuild by means of a version upgrade fixed them. Solved!

---

### Post by UltimateCat on 2022-12-28
Glad things are working now:-

Happy New Year!

---

