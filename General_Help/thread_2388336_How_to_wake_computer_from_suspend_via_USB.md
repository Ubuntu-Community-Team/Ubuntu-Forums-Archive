---
title: "How to wake computer from suspend via USB"
date: 2018-03-31
forum: General Help
---

### Post by Cavsfan on 2018-03-31
I have an older computer that came with ps/2 connections for the mouse and keyboard.

I recently got a USB mouse and keyboard that is controlled with one USB connection - it's called a USB receiver.

I had gotten use to the USB not working and just pressed the power button briefly and that would wake it up.

However, windows works and so too should Linux systems wake from suspend via USB as it is set to do so in the BIOS.

So, I found this link which worked nicely on Xubuntu Bionic Beaver 18.04 (developmental version) and even on Arch Linux.

I thought I would share this great find. [https://askubuntu.com/questions/848698/wake-up-from-suspend-using-wireless-usb-keyboard-or-mouse-for-any-linux-distro](https://askubuntu.com/questions/848698/wake-up-from-suspend-using-wireless-usb-keyboard-or-mouse-for-any-linux-distro)

The solution is naturally by the green checkmark. My system just has 5 USB ports but, the article uses an example of 8 ports. Just do it for each one you have and it will work.
Or if you want to be really specific, find out which ones you need enabled and just enable that one or two if you so choose.

---

### Post by Cavsfan on 2018-04-22
The previous post did not work for me after a new kernel was installed but, this method should work every time.

Look in this folder **/sys/bus/usb/devices/** and determine how many USB ports you have.

**ls -l /sys/bus/usb/devices/** shows I only shows I have 4.

You can not enter these commands with sudo. You have to become super-user.
i.e:
```
cavsfan@cavsfan-Xenial-Xerus:~$ sudo su
[sudo] password for cavsfan: 
root@cavsfan-Xenial-Xerus:/home/cavsfan# 
```

After entering **sudo su** first, I entered this:
```
echo enabled > /sys/bus/usb/devices/usb1/power/wakeup
echo enabled > /sys/bus/usb/devices/usb2/power/wakeup
echo enabled > /sys/bus/usb/devices/usb3/power/wakeup
echo enabled > /sys/bus/usb/devices/usb4/power/wakeup

```

I then suspended the computer and about 20 minutes later was able to unsuspend the PC with just the mouse or keyboard.

Although it did take roughly 5 minutes for the network to come back up, the network did resume.

Here is how to automagically do this at bootup; this way it *should* never fail.

Create a text file and name it what you want I called mine **usbwakeup**.
```
#!/bin/bash
# Make USB ports wake from suspend
echo enabled > /sys/bus/usb/devices/usb1/power/wakeup
echo enabled > /sys/bus/usb/devices/usb2/power/wakeup
echo enabled > /sys/bus/usb/devices/usb3/power/wakeup
echo enabled > /sys/bus/usb/devices/usb4/power/wakeup

exit 0
```

Then make it executable how ever you choose: **chmod +x usbwakeup**, **chmod 755 usbwakeup**, etc.
Then copy it to /etc/init.d/ like this: 
```
sudo cp usbwakeup /etc/init.d/usbwakeup
```

Then make a symlink:
```
sudo ln -s /etc/init.d/usbwakeup /etc/rc3.d/S01usbwakeup
```

Then you can restart and suspend like I did to test it.

it worked for me.

PS: I think this will work on other versions of Ubuntu. I added it to both 18.04 and 16.04 with success.

---

### Post by seansplayin on 2018-09-20
> **Cavsfan said:**
> The previous post did not work for me after a new kernel was installed but, this method should work every time.

Look in this folder **/sys/bus/usb/devices/** and determine how many USB ports you have.

**ls -l /sys/bus/usb/devices/** shows I only shows I have 4.

You can not enter these commands with sudo. You have to become super-user.
i.e:
```
cavsfan@cavsfan-Xenial-Xerus:~$ sudo su
[sudo] password for cavsfan: 
root@cavsfan-Xenial-Xerus:/home/cavsfan# 
```

After entering **sudo su** first, I entered this:
```
echo enabled > /sys/bus/usb/devices/usb1/power/wakeup
echo enabled > /sys/bus/usb/devices/usb2/power/wakeup
echo enabled > /sys/bus/usb/devices/usb3/power/wakeup
echo enabled > /sys/bus/usb/devices/usb4/power/wakeup

```

I then suspended the computer and about 20 minutes later was able to unsuspend the PC with just the mouse or keyboard.

Although it did take roughly 5 minutes for the network to come back up, the network did resume.

Here is how to automagically do this at bootup; this way it *should* never fail.

Create a text file and name it what you want I called mine **usbwakeup**.
```
#!/bin/bash
# Make USB ports wake from suspend
echo enabled > /sys/bus/usb/devices/usb1/power/wakeup
echo enabled > /sys/bus/usb/devices/usb2/power/wakeup
echo enabled > /sys/bus/usb/devices/usb3/power/wakeup
echo enabled > /sys/bus/usb/devices/usb4/power/wakeup

exit 0
```

Then make it executable how ever you choose: **chmod +x usbwakeup**, **chmod 755 usbwakeup**, etc.
Then copy it to /etc/init.d/ like this: 
```
sudo cp usbwakeup /etc/init.d/usbwakeup
```

Then make a symlink:
```
sudo ln -s /etc/init.d/usbwakeup /etc/rc3.d/S01usbwakeup
```

Then you can restart and suspend like I did to test it.

it worked for me.

PS: I think this will work on other versions of Ubuntu. I added it to both 18.04 and 16.04 with success.

I listed here all steps to wake from USB
[https://rog.asus.com/forum/showthread.php?104066-How-do-I-enable-wake-by-mouse-keyboard&p=735982#post735982](https://rog.asus.com/forum/showthread.php?104066-How-do-I-enable-wake-by-mouse-keyboard&p=735982#post735982)

---

