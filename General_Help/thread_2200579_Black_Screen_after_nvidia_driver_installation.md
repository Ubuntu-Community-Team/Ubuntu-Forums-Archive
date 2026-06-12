---
title: "Black Screen after nvidia driver installation"
date: 2014-01-20
forum: General Help
---

### Post by singularity2 on 2014-01-20
hi, i'm new with ubuntu, my system has been working well until i tried installing the nvidia driver

i'm using ubuntu 13.10, nvidia gtx570, core i5 2500k

i couldn't see the nvidia drivers under additional drivers in settings, so i always do it under terminal, i have tried both x-swat and xorg-edgers repositories, tried nvidia-current and nvidia-331...but whenever i restart, i would get the dark purple screen but the ubuntu logo wouldn't show anymore, i would only have a black screen then i'd hear the log on sound...

tried going into recovery mode and edit xorg.conf, but it's not there, after several tries, found out it would appear if i did

sudo nvidia-xconfig


so i edited xorg.conf and added a line

option "UseDisplayDevice" "DFP"


read it somewhere, couldn't remember, but it still didn't fix the problem...


also tried downloading the driver off nvidia's website, installed it using the .run file, but was getting errors


please
help

---

### Post by jeanjd63 on 2014-01-20
Hello
Can you give the returns of :
**dpkg  -l  |  grep -i nvidia **

---

### Post by singularity2 on 2014-01-20
i'll have to reinstall ubuntu again, i'll post it later

thanks

---

### Post by singularity2 on 2014-01-21
without reinstalling ubuntu, i went into recovery and chose drop to root shell and ran [B]dpkg -l | grep -i nvidia

this is what i got

[/B][IMG]http://i1101.photobucket.com/albums/g428/conflict10/IMAG0216_zps7e1a97c7.jpg[/IMG]

---

### Post by singularity2 on 2014-01-21
i'll reinstall ubuntu now and will run dpkg -l | grep -i nvidia again

thanks

---

### Post by jeanjd63 on 2014-01-21
If you reinstall all, first try to boot. If the bug is install nvidia drivers, don't install them.

---

### Post by singularity2 on 2014-01-21
if ireinstall and not instlal nvidia drivers, it's ok, but i want to install the nvidia drivers because it's better, the transition effects are smoother and faster

---

### Post by monkeybrain20122 on 2014-01-21
If you tried xorg-edgers then it may be the cause of your woes. For some inexplicable reasons when you install Nvidia 331 it installs bumblebee as a recommended package. Bumblebee is for optimus machines and it automatically blacklists the nvidia card. So if you don't have a second graphic card you are left with a black screen. I updated with xorg-edegers using synaptic, so I just unchecked bumble bee (and primus) before I clicked apply and I updated just fine (or in terminal sudo apt-get install nvidia-331 --no-recommends)


So you need to remove bumblebee and its configuration file from cli and reboot.
```
sudo apt-get purge bumblebee
sudo rm -fr /etc/modprobe.d/bumblebee.conf
sudo reboot
```

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1265570)

---

### Post by singularity2 on 2014-01-21
monkeybrain20122, thank you!!!  that did it

i reinstalled ubuntu, added the xorg-edgers repository and installed nvidia-311, right after the installation, i ran

sudo apt-get purge bumblebee
sudo rm -fr /etc/modprobe.d/bumblebee.conf
sudo reboot

it showed the dark purple screen, screens till went black but it returned, i just dont have the ubuntu loading logo anymore, not complaining, but is that normal, or is there something i can do?

and just for additional knowledge, i'm really new with ubuntu...i tried

sudo apt-get install nvidia-331 --no-recommends

did not work, is there really a command that doesn't include the recommended additonal software?

and if i install using synaptic, which one shoud i click?  let's say i want nvidia 331, i just click that?  nothing else?

thanks so much!!!

---

### Post by singularity2 on 2014-01-22
reinstalled ubuntu and installed nvidia using synaptics, unclicked bumblebee, yes, this was is much easier...i still get a black screen instead of the ubuntu loading logo, but everything is working now, thanks again!!!

---

