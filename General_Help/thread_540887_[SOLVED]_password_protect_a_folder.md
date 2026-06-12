---
title: "[SOLVED] password protect a folder"
date: 2007-09-02
forum: General Help
---

### Post by gobbles414 on 2007-09-02
Hi all,

First, I know that this issue has been discussed before in the forums. But a satisfactory answer for my needs is nowhere to be found.:-(  I need three things: One, I need nautilus not to display the contents of a folder without first prompting for a password. Two, I need the files inside the folder to be hidden from apps such as Firefox and OpenOffice until I enter a password. Three, I still need to be able to save files to said folder using Firefox and OpenOffice (with or without a password). Is this possible?

---

### Post by southernman on 2007-09-02
It sounds as if you have more than yourself able to login to the machine using just one username... no? If so... shame! ;)

Again, if so... don't! Not even for your wife or kids. Just setup seperate users and keep eveyones /home/username directory chmod at 700.

---

### Post by cawill on 2007-09-02
You can use encrypted folders to achieve this:

[http://ubuntuforums.org/showthread.php?t=148600]("http://ubuntuforums.org/showthread.php?t=148600")

You can also use this program to manage them:

[http://www.getdeb.net/app.php?name=Cryptkeeper]("http://www.getdeb.net/app.php?name=Cryptkeeper")

Hope this helps.

---

### Post by gobbles414 on 2007-09-12
Hi all,

Sorry to have taken so long responding to your replies. I will experiment with your suggestions and report back.

---

### Post by gobbles414 on 2007-09-17
cawill and everyone,

Cryptkeeper is now working perfectly! It installed with only a few minor problems (mostly errors on my part). Here are some instructions that should work for all Feisty users starting in the terminal:

* sudo apt-get install encfs fuse-utils
* sudo modprobe fuse
* sudo gedit /etc/modules **--> A Text editor will open. Type *fuse* on a new line and then save.**
* sudo adduser *username* fuse
* reboot
* download and install the getdeb version of [Cryptkeeper]("http://www.getdeb.net/app.php?name=Cryptkeeper") (0.90 is currently the latest version)
* reboot (may not be necessary)
* System Tools --> Cryptkeeper (the icon will appear in the system tray)
* right click on the icon in the system tray and select *preferences*. Change the *file browser* option to *nautilus* (may not be necessary)
* **To use Cryptkeeper, left click on the icon in the system tray.**

Many thanks cawill! I hope that this is helpful to others!


PS to southernman:

The problem with your suggestion of separate accounts for different users is that Linux applications and plugins are often associated with a user's home directory (i.e. not installed systemwide). It is tedious to re-setup programs for each user.

---

