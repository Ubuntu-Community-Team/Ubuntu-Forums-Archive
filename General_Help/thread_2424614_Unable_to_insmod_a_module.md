---
title: "Unable to insmod a module"
date: 2019-08-11
forum: General Help
---

### Post by distinct on 2019-08-11
Hi team,

I am currently working a NanoPi, a 3rd party variant of the Raspberry pi that is running "Ubuntu 16.04.5 LTS". I am currently working with an electronic test house to be able to do WiFi and Bluetooth EMI/RFI tests for the various power/modulation and technologies within WiFi. This will allow our product to be certified and sold. I think I am asking for help decrypting steps from a guide that the manufacture is not responding to.

Nonetheless, I have been in contact with the manufactuer of the WiFi module on our NanoPi and they have supplied an application that was cross compiled for our processor and a .bin file. In their instructions they tell me to initialise the application in 2 ways:
1. If Wi-Fi driver is built a kernel module(bcmdhd.ko):
insmod /system/lib/modules/bcmdhd.ko iface_name=wlan0 firmware_path=/etc/firmware/fw_bcmdhd_mfg.bin nvram_path=/etc/firmware/nvram.txt

2. If Wi-Fi driver is built in kernel
echo /system/etc/firmware/fw_bcmdhd_mfg.bin> /sys/module/bcmdhd/parameters/firmware_path

While they're vague on some of the details here, like does is the firmware path? /system/etc is not a standard path. So assuming option 1. I placed the files into my local home directory and attempted the following:
sudo insmod /sys/modules/bcmdhd.ko iface_name=wlan0 firmware_path=/etc/pi/fw_bcm43438a0_mfg.bin nvram_path=/etc/pi/nvram.txt

I ended up with an error:
insmod: ERROR: could not load module /sys/modules/bcmdhd.ko: No such file or directory

The bcmdhd.ko doesn't exist anywhere. Not knowing much about the insmod command, is it used to push the existing *.ko file into the kernel, or the *.ko file is the file that is created when it is pushed into the kernel?

I hope someone can help, this might be too specific of a question.

---

### Post by elqusy90 on 2019-09-05
could you please upload the file you have received from the manufactuer of the WiFi module

---

