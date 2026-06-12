---
title: "xserver error"
date: 2008-02-15
forum: General Help
---

### Post by zins184 on 2008-02-15
I have a Dell XPS 1330 and I tried sudo dpkg-reconfigure xserver-xorg didn't work. Fatal server error I get is no screens found. Other info it states is that no display devices found.. screens found, but none have a usable configuration.
specs:
T7500 2.2GHz
chipset (965PM/GM)
4 GB memory
250 HDD
NVIDIA GeForce Go 8400M GS / 128MB 
LCD 13.3 WXGA
WIRELESS MINICARD 4965

---

### Post by rucadulu on 2008-02-15
Try booting into recover mode then type in apt-get install nvidia-glx
then reboot into recover mode again run dpkg-reconfigure xserver-xorg and select the nvidia for your video card driver do not select nv that driver will not work with some of the newer nvidia cards. Hope this helps.

---

### Post by stevejesus on 2008-02-15
racadulu, how much is your power bill?  lol

---

### Post by rucadulu on 2008-02-15
About $90.00 a month.

---

### Post by zins184 on 2008-02-15
tried that and got back two error messages.
"could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
unable to lock the administration directory (/var/lib/dpkg/), are you root?"


ok I'm guessing your surpose to use sudo in front of it. lol anyway I type sudo in front and got this error
"package nvidia-glx has no installation candidate"

---

### Post by zins184 on 2008-02-16
dump anyone else....

---

### Post by PmDematagoda on 2008-02-16
Do:-
```
sudo rm /var/lib/dpkg/lock
```
then install the driver using:-
```
sudo apt-get install nvidia-glx-new
```
after that is finished enable the driver using:-
```
sudo nvidia-settings --config enable
```

---

### Post by zins184 on 2008-02-16
with sudo apt-get install nvidia-glx-new i get the same error "package nvidia-glx has no installation candidate"

---

### Post by rucadulu on 2008-02-16
Ok, lets try setting your driver to vesa and see if we can get the system to boot into the GUI. Boot into recovery mode again and run dpkg-reconfigure xserver-xorg when it asks for the video driver select VESA then finish answering the questions then reboot if this works you will boot into the GUI. Once there go to system>administration>software sources and enable all available channels under each tap. Then under system>administration select synaptic package manager. Once this opens go to settings repositories and make sure that the changes took. Then use synaptic to search for nvidia and then select the nvidia-glx, if you want the stable drivers or nvidia-glx-new, if you want the beta drivers. Install them and then reboot the system. when the system comes up the restricted driver module should come up. If it does not open a terminal and run dpkg-reconfigure xserver-xorg again and then select the nvidia drivers. Once this is done you will need to restart the xserver this can be done pressing ctrl, alt, and backspace at the same time or you can just reboot the computer.  Hope this helps.

---

### Post by zins184 on 2008-02-16
ok I'm in the gui did what you said and nvidia-glx isn't listed.

---

### Post by PmDematagoda on 2008-02-16
Open Software Sources in System>Administration>Software Sources and enable all the choices except for the CD-ROM in the Ubuntu Software tab. After that is done, close the window, you will be asked to reload the sources list, do that, after that is done go to the Restricted Drivers Manager in System>Administration>Restricted Drivers Manager and install the driver for the Nvidia card.

---

### Post by zins184 on 2008-02-18
do I need the computer hooked up to the internet? Because I still don't see driver and the Restricted Drivers Manager tells me there is no restricted driver to be installed.

---

