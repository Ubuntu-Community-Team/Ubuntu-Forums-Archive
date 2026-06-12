---
title: "Detects other wifi-s but not my own and does not detect the external antenna"
date: 2013-12-16
forum: General Help
---

### Post by andjeladavidovic on 2013-12-16
Hello,

Here I am with an annoying Dell laptop. And a bunch of problems. I have Ubuntu 12.04 32bit.

Problem 1:
My internal wifi detects all other networks except my own. In the beginning it was detecting it, and then disturbing connections of all other computers near by. So for some time I kept turnning off wifi. Fially I am getting some days alone in the house and now when I turn on wifi it I have this new problem.

I checked rfkill list and these is nothing blocked. I tried updating driver to bcmwl-kernel-source_6.30.223.141.+bdcom-0ubuntu2_i386.deb and it did not help. 

Any ideas?

Problem 2:
Since internal wifi did not work, I tried using the usb antenna. And it worked perfectly last night!
 Today it does not detect it at all. And antenna works, since I am using it now from my othe computer -very old Toshiba with the same Ubuntu 12.04 32 bit.

I was googling a lot about these problems. So here are some data you might want to know:

lspci -nnk | grep -iA3 net   gives
Network controller: ... BCM4313 ... [14e4:4727]
Dell Device [1028:0015]

lsmod has amog other lines  wl 

Can anyone help? I am not very good with these things and I am wasting hell lot of time on trying to fix these annoying thigs.

---

### Post by varunendra on 2013-12-20
Welcome to the forums andjeladavidovic !

Please try this first -
```
sudo apt-get purge bcmwl-kernel-source
```
This will purge the proprietary "wl" driver that is currently in use, so that the native "brcmsmac" module can load instead since next boot. Reboot and see if you can use your wifi.

If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

