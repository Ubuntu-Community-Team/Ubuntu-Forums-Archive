---
title: "usbmuxd crashing when iPhone unplugged?"
date: 2018-01-09
forum: General Help
---

### Post by mikkyx2 on 2018-01-09
Hi all,
Since upgrading to Ubuntu 17.10 a couple of weeks ago, I've noticed that my iPhone (5S, iOS 11) doesn't charge when connected to the front USB ports on my computer. I found something about running usbmuxd to resolve this, and if I run it from the command line like so:

[FONT=courier new]sudo usbmuxd -u -U usbmux[/FONT]

My phone lights up and begins to charge - until I have to unplug it to take a call or go out - then the next time I reconnect it, nothing again until I run the above command. 

This wasn't happening on any previous version (I started on 16.04 then upgraded to 17.04 prior to 17.10) - it's as if usbmuxd is crashing whenever I unplug my phone (doesn't show up under [FONT=courier new]ps[/FONT]). 

Is there a safe eject somewhere that's now required, or is there something else afoot? Thanks in advance for any advice :)

---

### Post by clapac on 2018-02-01
Hi!

           I've had the same issue. I solved it creating a new udev rule. I used the steps below, I hope it could help you too. 


1. Create a new udev rule file:


                **        cd /etc/udev/rules.d/**

       [B] sudo vim 100-iphone-usbmuxd.rules 

  [/B]( * the file name is formed by PRIORITY-whatever.rules, you can use 99-mynewrules.rules, for example) :)


2. Insert the following lines into the created rules file:


        [B]ENV{DEVTYPE}=="usb_device", ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="05ac", ATTR{idProduct}=="129[0-9abcef]", RUN+="/usr/sbin/usbmuxd -u -U usbmux"
        ENV{DEVTYPE}=="usb_device", ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="05ac", ATTR{idProduct}=="12a[0-9ab]", RUN+="/usr/sbin/usbmuxd -u -U usbmux"
        ENV{DEVTYPE}=="usb_device", ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0fca", ATTR{idProduct}=="8014", RUN+="/usr/sbin/usbmuxd -u -U usbmux"[/B]



3. Save the file.

4. Run the following command to reload the udev rules:


**        sudo udevadm control --reload-rules**
        


5. Test it, unplugging the iPhone and reconnecting it.

It should work. Maybe this isn't the best way to solve this issue, but it worked for me.


Best regards!

---

