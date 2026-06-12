---
title: "micro SD card in Samsung Rugby Pro wont show up in Ubuntu"
date: 2013-08-21
forum: General Help
---

### Post by sir_robert007 on 2013-08-21
When i plug the phone in its 4GB internal memory will show up but not the 16GB micro SD card I have installed. I have the phone connected as a media device (MTP). I tried using programs such as gMTP and Qlix to no avail. lsusb gives me this output:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04d9:0702 Holtek Semiconductor, Inc. 
Bus 006 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 001 Device 003: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]



```

Ubuntu seems to be detecting it as can be seen from the output above

Anyone know how I can get this to work?

Computer Info:

Ubuntu 12.04 64-bit

Phone info: Android 4.1.2 Jelly Bean

---

### Post by SeijiSensei on 2013-08-22
Using Kubuntu 13.04 with my Galaxy S3 brings up separate Phone and Card entries in the device's directory root.  I don't know how you have configured 12.04 to use MTP, but MTP support was pretty dicey in Ubuntu until 13.04 was released.

I'm also running Android 4.1.2.

---

### Post by sir_robert007 on 2013-08-22
I havent changed any settings for MTP in Ubuntu as of yet. Is there any way i can configure it so it will work with my phone without having to upgrade my entire OS?

---

### Post by SeijiSensei on 2013-08-23
I couldn't figure out how to get it to work in Kubuntu 12.04, so I upgraded to 13.04.  Perhaps it's easier to get MTP working in vanilla Ubuntu 12.04.  I can't help there, I'm afraid.

---

### Post by sir_robert007 on 2013-08-26
Ok i figured it out. All i had to do was install go-mtpfs which can be done by adding this repository:

```

# sudo add-apt-repository ppa:webupd8team/unstable
# sudo apt-get update
# sudo apt-get install go-mtpfs

```

Website that i got this from:

[http://forum.xda-developers.com/showthread.php?t=2223401](http://forum.xda-developers.com/showthread.php?t=2223401)

---

