---
title: "I have a problem in login with the message &quot; /dev/name01p8 clean ~~ files ~~ blocks&quot;"
date: 2019-02-05
forum: General Help
---

### Post by dreamcacao on 2019-02-05
Hi,

I've used dual boot system in my laptop (samsung, ssd) (Ubuntu 16.04 and Window 10).
I've used Ubuntu well, but I got login problem today.


I tried to remote control to Ubuntu from Window, so I followed some instructions in google.
Then when I booted in Ubuntu, I could not login. When I enter password, screen shows "/dev/name0n1p clean  ~~ files ~~ blocks" in a flash and returns to login page.


I tried some advices in google but cannot fix it. FYI I use Intel internal graphic card and there is no problem in Window 10.


Anybody can help me?




Below is terminal commands I used.


    ```
$ sudo apt-get install ssh
$ /etc/init.d/ssh restart
$ ifconfig
$ reboot
$ sudo apt install xrdp
$ sudo systemctl enable xrdp
$ sudo apt update
$ sudo apt install tightvncserver
$ sudo tightvncserver
```




Below are commands after getting problem by 'ctrl + alt + f1'.


    ```
$ sudo apt-get purge nvidia*
$ sudo fsck -f /dev/nvme0n1p8
$ sudo systemctl stop gdm.service
$ sudo apt purge *390*
$ sudo apt autoremove
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt install nvidia-driver-396
$ sudo apt-get install xserver-xorg-video-intel
$ sudo blkid
```

---

