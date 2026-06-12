---
title: "Ubuntu 12.04 and nvidia geforce 720m"
date: 2013-11-02
forum: General Help
---

### Post by erotavlas on 2013-11-02
Hi,

I have bought a laptop of asus f550c with i7-3537u and nvidia geforce gt720m. I have installed bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) to enable optimus technology. I have two question: I cannot find the nvidia setting menu on system tools->administrator->nvidia-setting to configure the video board. Further is not clear if the optimus technology work automatically or if it works only manually by using it with demanding application. I also tried to install latest nvidia driver as specified here [http://askubuntu.com/questions/325037/installing-nvidia-drivers-on-ubuntu-12-04](http://askubuntu.com/questions/325037/installing-nvidia-drivers-on-ubuntu-12-04).

Thank you

---

### Post by erotavlas on 2013-11-18
[FONT=times new roman][SIZE=3]Hi, 
I'm still trying to install properly the nvidia driver. At the moment I'm able to install the nvidia driver and nvidia setting with these commands
```

sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331 nvidia-settings-331
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
sudo apt-get dist-upgrade
```
But if I type nvidia-setting in the terminal, the nvidia setting manager starts and gives this message

```

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

```

In the applications->system tools->administration I cannot see the nvidia control panel.
I'm have also tried to type sudo nvidia-xconfig but the command does not work.
Can you help me? 
Thank
[/SIZE][/FONT]

---

