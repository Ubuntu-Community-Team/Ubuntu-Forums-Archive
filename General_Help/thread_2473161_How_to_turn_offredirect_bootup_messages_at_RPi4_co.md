---
title: "How to turn off/redirect bootup messages at RPi4 console port"
date: 2022-03-25
forum: General Help
---

### Post by tc2020 on 2022-03-25
I am using Ubuntu server 20.04 LTS 64-bit on RPi4 with its console serial port brought out as RS-232. 
I would like to know how to disable/stop bootup/system messages from being sent out to this port during bootup and user session. 
If this is not possible, redirect these messages to somewhere else (like a file or /dev/null) is also workable.
Any hint/help would be very much appreciated. Thank you.

---

### Post by TheFu on 2022-03-26
Google found this: [http://pi.bek.no/hideBootMessages/](http://pi.bek.no/hideBootMessages/)  Don't know if it works.
$ sudoedit /boot/cmdline.txt
Make these changes to the file:[LIST]
[*]    Replace “console=tty1” with “console=tty3” to redirect boot messages to the third console?
[*]    Add “logo.nologo” to hide Raspberry logo
[*]    Add “quiet splash” for a non-text load screen.
[/LIST]

I don't have a Pi v4, so don't know if this applies or not.  
[https://ampron.eu/article/tutorial-simplest-way-to-remove-boot-text-on-the-raspberry-pi-based-kiosk-or-digital-signage-display/](https://ampron.eu/article/tutorial-simplest-way-to-remove-boot-text-on-the-raspberry-pi-based-kiosk-or-digital-signage-display/) is another solution. Again, don't know if it works or not.

What else have you tried?

---

### Post by tc2020 on 2022-03-28
I searched the net prior to posting this and found many discussions on this topic. They mainly talk about grub/grub2 which my unit does not have. Regardless, the main idea was to change some parameters dealing with cmdline. People have tried different settings but in the end, nothing really conclusive from what I have read.

With respect to the links you provided, none works. The file may be at /boot/cmdline.txt on a freshly created SD card but it's actually at /boot/firmware/cmdline.txt in the unit.

I experimented with quiet and loglevel parameters and did not really see any help. I have also looked into various parameters for kernel boot loader but not many that I can think of for this case. The link for this document is at [https://www.kernel.org/doc/html/v4.14/admin-guide/kernel-parameters.html#](https://www.kernel.org/doc/html/v4.14/admin-guide/kernel-parameters.html#). 

One would think by simply redirecting console messages to /dev/null or something similar would solve this issue. An optional redirect parameter would be nice but I have not found anything like this on the net.

I do not know if there are options that can be used if I want to go through rebuilding the kernel to solve this too.

---

### Post by him610 on 2022-03-29
@tc2020
> The file may be at /boot/cmdline.txt on a freshly created SD card but it's actually at /boot/firmware/cmdline.txt in the unit.
Those instructions TheFu pointed you to were written for RaspberryPI OS. On both of my RPi devices, /boot/cmdline.txt is where it should be.
Since you seem to be using ARm *buntu, you will need to reconfigure as necessary.

I go into my RPi devices using ssh, never seeing the boot messages, but then, I prefer to see boot messages as they scoll down the screen.

---

### Post by him610 on 2022-03-29
FWIW, RaspberryPI OS has a configuration tool, raspi-config that has this configurable line in it...
```
 I6 Serial Port   Enable/disable shell messages on the serial connection  
```
It is possible the *buntu Arm distro has a similar configuration tool, then again, maybe not.
Maybe, you should reconsider the distro you chose for your RPi device.

My installed version of RaspberryPi OS....
```
Linux rpi3B 5.10.92-v8+ #1514 SMP PREEMPT Mon Jan 17 17:39:38 GMT 2022 aarch64 GNU/Linux
No LSB modules are available.
Distributor ID:	Debian
Description:	Debian GNU/Linux 11 (bullseye)
Release:	11
Codename:	bullseye

```

---

### Post by tc2020 on 2022-03-29
It would be great to have that configuration tool for this Ubuntu. I will look for it.

We are at the point of no return, so not reconsidering the OS at this time.

Our ssh session is also very clean. It makes sense because once you are able to connect via ssh, it's already past bootup messages and therefore you should not see any. It is the serial console port that we prefer not to have all these messages.

We used a different OS before and we simply redirected the messages to have a clean console connectivity.
Our users can remotely connect to this console port (via IP/serial connectivity) to work with the device as well 
as to work with other systems connected to it. For this reason, a clean connection is preferred.

---

