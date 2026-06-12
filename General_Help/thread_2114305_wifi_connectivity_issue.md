---
title: "wifi connectivity issue"
date: 2013-02-09
forum: General Help
---

### Post by hemandr on 2013-02-09
i am new to ubuntu.
present ver 12.10, installed from burned CD.

problem area Internet.

presently net working with usb dongle.
problem arises when i try to connect through my home wifi.

it shows connecting to wifi hotspot, but repeatedly keeps asking for paswd...and never connects.

sys config
lenove g480, dual boot win 7

any volunteers to help please...

---

### Post by wildmanne39 on 2013-02-09
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by hemandr on 2013-02-24
uploaded as desired

---

