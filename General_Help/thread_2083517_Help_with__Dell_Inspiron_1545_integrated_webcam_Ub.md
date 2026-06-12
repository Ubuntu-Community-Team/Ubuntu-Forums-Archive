---
title: "Help with  Dell Inspiron 1545 integrated webcam Ubuntu 12.10"
date: 2012-11-12
forum: General Help
---

### Post by volkstech on 2012-11-12
Hi I installed Ubuntu 12.10 last week and myintegraded webcam doesn't work. I have tried to install Cheese to see if that would work but it didn't. Just wondering if anyone has ran into this and if or how they were able to fix the issue. 

Thanks!

---

### Post by ercherramon on 2012-11-12
hi. first test with the command: 

```
lsusb
```This is to verify that the system you are identifying the webcam.

later, install this packs:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```And see if cheese recognizes the webcam. if you do not recognize it, then you have to compile the driver.

---

### Post by volkstech on 2012-11-12
Hi ercherramon, 

I tried what you suggested but still no cam. I opened up preferences in Cheese and it looks as though it recognizes the the cam but the screen is black. 

[IMG]http://i47.tinypic.com/e8snir.png[/IMG]

---

### Post by ercherramon on 2012-11-13
I see. Well, it's better to compile the driver. install, please, these packages:

```
sudo aptitude install kernel-package linux-headers build-essential ctags libv4l cogito git-core git-doc
```

then download the source code and compile the driver MICRODIA, which is based on webcam the Inspiron 1545:

```
git clone http://repo.or.cz/r/microdia.git

cd microdia

make

sudo insmod ./sn9c20x.ko
```

and finally the system loads the driver:

```
sudo strip -g sn9c20x.ko
sudo mkdir -p /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo cp sn9c20x.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
sudo depmod -a
```

tell me. if it works webcam after this, please.

---

### Post by volkstech on 2012-11-13
Thank you for the help but when I try to install the packages I get an error: 

sudo: aptitude: command not found 

Thank you for your help!

---

### Post by ercherramon on 2012-11-13
sorry, i remember. the command aptitude don't install in ubuntu 12.10.

it was:

```
sudo apt-get install kernel-package linux-headers build-essential ctags libv4l cogito git-core git-doc
```

---

### Post by volkstech on 2012-11-16
> **ercherramon said:**
> sorry, i remember. the command aptitude don't install in ubuntu 12.10.

it was:

```
sudo apt-get install kernel-package linux-headers build-essential ctags libv4l cogito git-core git-doc
```

Hi, ercherramon. I still get errors. Here is the screenshot of terminal. 

[IMG]http://i50.tinypic.com/35iupfk.png[/IMG]

---

