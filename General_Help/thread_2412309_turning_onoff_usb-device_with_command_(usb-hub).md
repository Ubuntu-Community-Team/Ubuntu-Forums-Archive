---
title: "turning on/off usb-device with command (usb-hub)"
date: 2019-02-11
forum: General Help
---

### Post by rosika on 2019-02-11
Hi,


I know this topic has been dealt with before but my "problem" is a bit different.


I want to enable/disable specific usb-ports. The theory is clear as it is well described on [https://stackoverflow.com/questions/18765725/turning-off-a-single-usb-device-again](https://stackoverflow.com/questions/18765725/turning-off-a-single-usb-device-again) . Example:
```
Turn off device ID 2-1:


echo '2-1' |sudo tee /sys/bus/usb/drivers/usb/unbind



```In my case it´s the following I want to do:


disabling the usb-port my wlan-stick is attached to.
That´s because I don´t need it when I use my umts-stick for internet-connection.


BUT: The wlan-stick isn´t attached directly to a usb-port on the computer but to a usb-hub which itself is connected to another
usb-hub (hama 78483) with its own power-supply.


So when using the recommended command, in my case:


```
echo '1-1.2.1' |sudo tee /sys/bus/usb/drivers/usb/unbind



```whould that have any effect at all? Because the hama hub with its own power-supply delivers power all the time, right?
Is there possibly another way of disabling a certain usb-device that suits my needs?


Many thanks in advance


Greetings
Rosika  :confused:


P.S.:
My system: Linux/Lubuntu 16.04.5 LTS, 64 bit

---

