---
title: "problem instaling HP printer drivers"
date: 2015-05-26
forum: General Help
---

### Post by thomas52 on 2015-05-26
hi friends,
i have just sucessfully installed ubuntu 14.04 LTS 32 bit on my pc.  but i am having problems installing drivers for my HP printer LaserJet P1007. can you  please help me ?
thanks.

---

### Post by Bucky Ball on 2015-05-26
Would help if you let us know what you have done to install it and where you are having issues. Have you installed HPLip from Software Centre? That is the first point of call ...

Install that. Plug in printer and go to 'Printers'> Add Printer. Go through the motions and when you get to the driver sections, choose HP then scroll through and see if the entry for your model is there ... but you may have done all this already.

---

### Post by thomas52 on 2015-05-26
> **Bucky Ball said:**
> Would help if you let us know what you have done to install it and where you are having issues. Have you installed HPLip from Software Centre? That is the first point of call ...

Install that. Plug in printer and go to 'Printers'> Add Printer. Go through the motions and when you get to the driver sections, choose HP then scroll through and see if the entry for your model is there ... but you may have done all this already.

sorry, i have just installed Ubuntu and i am very much in the learning process. i haven't had the chance to explore software center so far  but i will try to follow the instruction you have given. thanks a lot

---

### Post by Bucky Ball on 2015-05-26
Yep, [HPLip supports your printer]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1007.html"). Install from SCentre, reboot, Add Printer. You should find the driver on the list when you get to that part.

PS: Understood. Enjoy the learning curve. ;)

---

### Post by thomas52 on 2015-05-26
sir can you please give me a step wise explanation for this installation procedure , i have only installed HPLIP tool box and i want to know what else i should do after that. help me please. thanks a lot

---

### Post by dino99 on 2015-05-26
open a terminal, and run: >  sudo apt-get install hplip hplip-gui

---

### Post by thomas52 on 2015-05-26
yes i have done this. please refer the attachment and guide me further 


```


siddhesh@siddhesh-H61M-DS2:~$ sudo -s
[sudo] password for siddhesh: 
root@siddhesh-H61M-DS2:~# sudo apt-get install hplip hplip-gui 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
hplip-gui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 552 not upgraded.






```

---

### Post by thomas52 on 2015-05-26
> **Bucky Ball said:**
> Yep, [HPLip supports your printer]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1007.html"). Install from SCentre, reboot, Add Printer. You should find the driver on the list when you get to that part.

PS: Understood. Enjoy the learning curve. ;)



sir i have installed HPLIP
 and successfully installed my HP laserJet P1007 printer as you told me to do so but when I'm printing a test page or any other page the printer it does not print and keeps on adding the printer to the job. the printer state is idle since installed.

please tell me what should i do for this issue. please refer the attachment for the idea

thanks for the help

---

### Post by Bucky Ball on 2015-05-26
Okay, not sure what you've done wrong here, but I will say a couple of things. Your machine is way out of date. When is the last time you did an update??? Also, it is not a good idea to drop to root everytime you want to run a simple command that requires admin permissions. Just use sudo!

Open a terminal and run these commands one after the other hitting enter after each (do not become root permanently for this, just copy/paste the commands that I show here).

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This will get your machine up to date then we have a better idea of where we are going with this. At the moment, you have 550+ updates/upgrades waiting. None of the above commands will  upgrade your installed OS release to a newer one, only upgrade the software you have installed in your current OS.

---

