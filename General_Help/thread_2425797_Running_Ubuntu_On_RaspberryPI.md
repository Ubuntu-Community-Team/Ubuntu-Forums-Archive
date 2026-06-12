---
title: "Running Ubuntu On RaspberryPI"
date: 2019-08-30
forum: General Help
---

### Post by felixklg on 2019-08-30
recently i have downloaded ubuntu on the microSD and when i put it in the slot it does not boot :(

---

### Post by TheFu on 2019-08-30
Assume we are clueless, old and perhaps a little senile.  
EXACTLY what steps did you take to get the correct file and put it onto the microSD?
Leave nothing out.

---

### Post by HermanAB on 2019-08-31
Here is a guide:
[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)

---

### Post by guiverc on 2019-08-31
The file has to be 'burnt' onto the SD card; myself as I use a \*nix environment I use `dd`  (data dump) to convert it from a file (if= or input-file) to a device (of= or output-file) like I saw in HermanAB's link.  My guess is you just copied the file onto a SD card as a un-bootable but readable file.  As TheFu said, for us to see what you did wrong, we must know what you did (and what OS you are wanting to use to write the file is helpful too, eg. `dd` may not exist in your environment, and it's somewhat dangerous as it doesn't stop stupid use of it.

---

### Post by dabian2 on 2019-08-31
Which version of the RaspberryPi are you using?

Which version of Ubuntu are you using?

What kind of hardware (monitor, keyboard, mouse, and etc.) have you connected to your RasberryPi?

---

