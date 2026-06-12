---
title: "Ubuntu 20.04 Focal, python3-pyqt4 and libffi6 not available"
date: 2020-05-17
forum: General Help
---

### Post by LongH on 2020-05-17
Hello, I'm following the instructions here: [https://www.rtl-sdr.com/ksdr/](https://www.rtl-sdr.com/ksdr/) to get a Kerberos SDR set up on my PC running Ubuntu 20.04 LTS. However, I get the following error when I try to install all the packages. 

```
hunter@hunter-HP-ZBook:~$ sudo apt install python3-pip python3-pyqt4 build-essential gfortran libatlas3-base libatlas-base-dev python3-dev python3-setuptools libffi6 libffi-dev python3-tk pkg-config libfreetype6-dev php-cli wondershaper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python3-pyqt4
E: Unable to locate package libffi6
```

I searched on [https://packages.ubuntu.com/](https://packages.ubuntu.com/) and apparently the packages python3-pyqt4 and libffi6 aren't available for Ubuntu 20.04 LTS. The packages are available for Eoan, Bionic, Xenial, so I assume that they just haven't been updated for Ubuntu 20.04 Focal. Is there any workaround, like installing an older version of the packages? Or should I go back to Ubuntu 18 Bionic? 

Thanks, 
-Hunter

---

### Post by Perfect Storm on 2020-05-17
It's because qt have moved to 5. You'll end up in a big mess with your computer if you try to install qt4 and its dependencies. It will be a dependency hell as they call it. I'm not sure if the qt4 and qt5 can coexist.

---

### Post by LongH on 2020-05-18
Thanks for the info!

I might just try 

 sudo apt install python3-pyqt5  libffi7

and see if it works. I guess the new versions could be different enough that it breaks things, but maybe not. Other than that I guess I just need to wait for the Kerberos SDR software to get updated. 

Thanks, 
-Hunter

---

