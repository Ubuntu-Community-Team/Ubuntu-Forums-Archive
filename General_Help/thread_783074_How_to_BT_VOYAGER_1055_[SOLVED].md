---
title: "How to BT VOYAGER 1055 [SOLVED]"
date: 2008-05-05
forum: General Help
---

### Post by ukripper on 2008-05-05
Finally after 2 years I have successfully made my BT voyager 1055 working under ubuntu Hardy. Right now i am typing using my new voyager 1055 in ubuntu

I would like to share with my fellow ubuntu mates how I have achieved this:-

Step 1 - Dowloaded and installed latest Bt voyager drivers from BT's website on my windows box. Once installed I went into program files/BT VOYAGER/ folder and copied all over to my ubuntu box.

Step 2 - Make sure your Voyager 1055 device is connected to your ubuntu box. Installed latest ndiswrapper-1.9 from hardy's repos.


Step -3 - In terminal – type following once you are in folder where you copied the BT voyager files to.
Code:
```
 sudo ndiswrapper -i bcmrndis.inf
```

don't worry if you get invalid error. just carry on!

Step -4 - Run
Code:
```

ndiswrapper -l
```

, it is 'ell' not one

Step -5 - copy files over
Code:```


sudo cp -v  usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/
```

Step -6 - Run again
Code:

```
ndiswrapper -l
```

and then
Code:
```

sudo modprobe ndiswrapper
```

Step -7 - create new file -
Code:

```
sudo gedit /etc/udev/rules.d/99-custom.rules
```

Step -8 - copy paste the following:
#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**


then save and exit



Unplug your adapter and plug it back. Everything works hopefully for you as well.

configure your wireless using network manager and then off you go.


I have never felt so much relieved resolving this, like a quest for me.

---

