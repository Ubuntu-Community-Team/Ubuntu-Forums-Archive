---
title: "Can't write on Ubuntu File System"
date: 2007-07-29
forum: General Help
---

### Post by nucleusfermi on 2007-07-29
**[COLOR="DarkRed"][SIZE="2"]I had heard about problems of reading and writing on the other parts of hard disk, that are assigned for Windows OS; but here I have different kind of problem, I am unable to write in Ubuntu Linuxes' own file system. I came to know about this when I was trying to make a subdirectory in "/lib/firmware" (I'm using "udev"), Actually I want to use my "Huewai MT882 USB Remote Network Device(SmartAX MT882) for connecting to internet(ADSL via WAN PPPoE) (i.e establishing internet connection). Though I had installation disk, and Linux supported documentations in which there are some "inc, src subfolders with same CDCEther file in them as well as one "makefile" named file and a patch notepad kinda file named USB CDCEther Readme File." But since I'm absolutely novice to this OS, I don't know how to use them. I searched whole forum very intensively and got some instructions via "UeagleAtm" website, by downloading a file named "ueagle-data-1.1.tar.gz", I followed all instructions and when it came to create subfolder in "/lib/firmware" and copy untarred files (in order to install "firmware") in that, I got failed, and permission was denied. In graphical mode too "create folder" icon was disabled (greyed). Now after so much searching I decided to post this question here, may I be able to attain answer. Thanks a lot for reading this long query. [/SIZE][/COLOR]**:(

---

### Post by tbroderick on 2007-07-29
Since you archive is going to be extracted in /lib you have use sudo. Generally, you use sudo for anything outside of /home. 

```

sudo mkdir /lib/firmware
sudo tar xvf ueagle-data-1.1.tar.gz

```

You can run nautilus or othere GUIs as root too. Use the gksu command.
```
gksu nautilus
gksu gedit

```

---

### Post by nucleusfermi on 2007-07-30
Thanks a lot tbroderick , that solved my problem but now I have one more trouble in the way, when I try to start the 'bridge' between the ATM modem and Ubuntu  by typing in terminal "sudo modprobe 2684", I get message "module 2684 not found". Can you help me?

---

