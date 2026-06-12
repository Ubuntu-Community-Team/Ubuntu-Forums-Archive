---
title: "force lirc to run specific hardware? USBUIRT"
date: 2008-06-24
forum: General Help
---

### Post by bond007taz on 2008-06-24
please be gentle, i am new to linux and especially to ubuntu. I am trying to create a HTPC on a GA-MA69 AMD (ati x1250 embedded vc) motherboard. I have a IR device connected to the machine, which is a USB-UIRT. I know the system sees the device when i connect it does see ttyUSB0 (i forget which command i used to get that info). Now I can do:
```
 sudo lircd -H usb_uirt_raw -d /dev/ttyUSB0 -n
```

and i will get:

```
lircd-0.8.3pre1[30745]: lircd(userspace) ready
```

i can bring up 'irw' in another window but of course i dont have the lircd.conf setup so nothing appears but at least it stays open. 

So i go to use irrecord and use this command:
```
sudo irrecord -H usb_uirt_raw -d /dev/ttyUSB0 blah.conf
```

i then go through the steps for irrecord and the USBUIRT device lights up when i press a button and I can complete irrecord and once it is done I have a .conf file

so the issue is... I dont know how to put this "-H usb_uirt_raw -d /dev/ttyUSB0" code into my hardware.conf file so it uses the USBUIRT when i start the service. I have tried different variations in the hardware.conf file and everytime i try to start the lirc service using

```
/etc/init.d/lirc restart
```

everything fails.

Does anyone have a hardware.conf that i could copy that would force it to use the commands that work above? maybe i am making this too hard?

NOTE: I did try the instructions at [https://help.ubuntu.com/community/Lirc_USB-UIRT](https://help.ubuntu.com/community/Lirc_USB-UIRT) , but i think this assumes that the drivers are loaded when the OS boots?

also, i ran across some posts that mention atiusb? I ran 
```
lsmod | grep ati
``` and i dont see anything related to atiusb... is this something?

```

cpufreq_conservative     8712  0 
atiixp                  5648  0 [permanent]
ide_core              113996  1 atiixp
ati_agp                 9996  0 
agpgart                34760  2 fglrx,ati_agp
pata_atiixp             8960  0 
libata                159344  4 pata_atiixp,ata_generic,pata_acpi,ahci

```

---

### Post by bond007taz on 2008-06-24
is there a way I can use: ```
sudo lircd -H usb_uirt_raw -d /dev/ttyUSB0 -n
``` to start everytime? would that work?

---

