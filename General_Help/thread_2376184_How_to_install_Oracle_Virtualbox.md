---
title: "How to install Oracle Virtualbox?"
date: 2017-10-31
forum: General Help
---

### Post by 1jarwolf on 2017-10-31
I am running a 32 bit Xubuntu. I did *cat /etc/issue*  and I get **Ubuntu 16.04.3 LTS**
How do I know whether this is Zesty, Stretch, Yakkety, Xenial, Jessie? I am unsure of which oracle virtualbox to download as I may pick the wrong version.

HAPPY HALLOWEEN!!!

---

### Post by RobGoss on 2017-10-31
Try running the following command, it should show you what version you have installed
```
 lsb_release -a
```

---

### Post by slickymaster on 2017-10-31
In a terminal window, add the following line to your **/etc/apt/sources.list**```
deb http://download.virtualbox.org/virtualbox/debian xenial contrib
```Download and add the Oracle public keys```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```Install it```
sudo apt-get update
sudo apt-get install virtualbox-5.2
```Install the **dkms** package to ensure that the VirtualBox host kernel modules are properly updated when the kernel version changes```
sudo apt-get install dkms
```

---

### Post by ajgreeny on 2017-10-31
Take a little care if you try the 5.2 version of VBox as there is a problem with the guest additions of the same version.
There is a work around shown on the VBox site [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) but I did not find that was successful with all my VMs so I have for now at least reverted to VBox-5.1, though I do use the Oracle repos as suggested by slickymaster.

You may find 5.2 works fine for your VMs as some of mine were OK, so give it a try; you can always uninstall 5.2 and install 5.1 in place of it if necessary.

---

### Post by 1jarwolf on 2017-10-31
Thank you guys! If I notice a problem whilst using virtualbox I will change t0 5.1.

---

