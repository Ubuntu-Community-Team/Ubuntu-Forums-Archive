---
title: "need a little help"
date: 2007-08-30
forum: General Help
---

### Post by kennster on 2007-08-30
ok so for one i made the switch from vista to ubuntu "glad i did" first time user of any liunx type OS
whell i got a problem i have ENVY to so i can ajust my rez from 1024/768 to 1600/1200 for some reasion it wont save ... it ses some thing about my x file wont alow it... and second i have xscreensavers whell i disabled gnome screen savers and whell now none of them work and 3 and final probelm every time I quit CS:S running in wine thats counter strike source BTW some times it gose to a all black screen and i can do any thang but for ctrl alt backspace and relog in and yes i am useing berly but most the time i dont ahve it running :confused: any help would be nice ty

---

### Post by banditti on 2007-08-30
What video chipset and driver are you using?

---

### Post by kennster on 2007-08-30
i have a nvidia GF7600gt and the drivers im not to shure on cuz it auto dled them for me threw Evny if u can tell me how to find out what driver it is i will like i sed ima little new to this OS i dont compleatly know my way around it but all i know it ses is some nvidia acel graphic drivers under RDM

---

### Post by kennster on 2007-09-01
ok i use nvidia settings to beable to set my desk top to 1600/1200 and it wont save it for when i restart i haft to keep doing it and the problem is it ses "unable to remove old X config backup file '/etc/x11/xorg.conf.backup'  i found the file and it ses i dont have permison to do any thang to it what should i do? to beale to save the info:confused:

---

### Post by Steve1961 on 2007-09-01
To edit xorg.conf type the following:

sudo gedit /etc/X11/xorg.conf

---

### Post by petit.padavoine on 2007-09-01
> **Steve1961 said:**
> To edit xorg.conf type the following:

sudo gedit /etc/X11/xorg.conf

He's using the nvidia-xconfig script.

You need super user (root) privileges to edit xorg.conf because it's a system file.
So instead of running nvidia-xconfig, run sudo nvidia-xconfig (sudo maens SuperuserDo). It will prompt you for your user password and then run the script with super user privileges, thus being able to edit xorg.conf.

---

### Post by kennster on 2007-09-01
TY for the help that worked um is tahre any web site or any thang that can teach me how to use thremal? like what domands do what exct? but that worked thank you

---

### Post by Amazona aestiva on 2007-09-01
Start nvidia-settings with sudo.

---

### Post by petit.padavoine on 2007-09-01
> **kennster said:**
> TY for the help that worked um is tahre any web site or any thang that can teach me how to use thremal? like what domands do what exct? but that worked thank you

[http://google.com](http://google.com) might do just that.

You should find a tutorial that you think is good and adapted to your level of computing.

To get you started:

man <nameofcommand> gives you info about a command.

---

### Post by kennster on 2007-09-03
ok im haveing trubel getting my drivers to work i tryed useing envy. but it wont  work for some reason every time ill restart it just goses crazy saying i dont have this and i need to install that and then freezes and i had to reinstall ubuntu 2 times in a row to figuer it out all i want it is to be able to have 1600/1200 rez and play my STEAM games in wine wiht no video card problems

---

### Post by Pumalite on 2007-09-03
Download from here and follow instructions: [http://www.nvidia.com/object/unix.htm](http://www.nvidia.com/object/unix.htm)
Post back if you have any problems.

---

### Post by kennster on 2007-09-03
> **Pumalite said:**
> Download from here and follow instructions: [http://www.nvidia.com/object/unix.htm](http://www.nvidia.com/object/unix.htm)
Post back if you have any problems.

Ty ima try that now ill let ya know how it turns out thank you

---

### Post by kennster on 2007-09-03
ok i got a problem i typed ```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run
``` and it sed cant open it ....?

---

### Post by Pumalite on 2007-09-03
At the command line: sudo chmod 777 /path/to/driver/NVIDIA blah, blah blah
Then sudo sh blah, blah, blah
Make sure you have build-essential:
sudo apt-get install build-essential
Good luck.

---

### Post by kennster on 2007-09-03
so install sudo apt-get install build-essential?

---

### Post by logos34 on 2007-09-03
> **kennster said:**
> so install sudo apt-get install build-essential?

You might want to use this guide for the newest nvidia driver:
[http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2)

---

### Post by Pumalite on 2007-09-03
Thank you for the link (bookmarked) logos34.

---

