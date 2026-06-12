---
title: "Disable wifi, bluethooth and Webcam"
date: 2018-05-23
forum: General Help
---

### Post by giobaxx on 2018-05-23
Could you help to undestand how i can  disable the following Peripherals, i read about adding some the used module in blacklist but i'm not sure that is the correct way

Integrated webcam
Integrated Bluethooth
Integrated Wireless Card

in reality i have to disable the integrated wifi card because at certain we'll need to plug an external wifi card via usb.

I tried to disable via BIOS but the option to disabled then does not exist so i have to do it through Ubuntu.

---

### Post by #&amp;thj^% on 2018-05-23
If your Wifi was installed during your initial install setup, then no need to blacklist anything for your particular case, just deactivate the driver, using the Additional Drivers utility. 
If not post back and we will help try to solve that.
That also I believe will also deactivate the Bluetooth. (I need to check that)
WebCam is a different matter.
EDIT: The Buletooth  will still try to load so we can use this to disable.
```

sudo -H gedit /etc/default/tlp
```
If you use something different than gedit replace that in the code i show

Find the section:
```
# Radio devices to disable on startup: bluetooth, wifi, wwan.
# Separate multiple devices with spaces.
#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wifi wwan"

```
Edit the line to read:

```
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth"
```

Example:

```
# Radio devices to disable on startup: bluetooth, wifi, wwan.
# Separate multiple devices with spaces.
DEVICES_TO_DISABLE_ON_STARTUP="bluetooth"

```
Save and close the file.
Also check your autostartup list and un check the Blueman Applet from loading at startup, as it will turn on Bluetooth when it loads. 
The next time you reboot Bluetooth "should" be disabled.

---

### Post by linuxlover18 on 2018-06-06
Thanks so much, this worked for me!!! I had tried other solutions like in the file /etc/bluetooth/main.conf adding the > AutoEnable=False; that simply doesn't work! Again... many thanks

---

### Post by #&amp;thj^% on 2018-06-06
That's Great :) and thanks for the reply. 
Enjoy and Kind Regards

---

