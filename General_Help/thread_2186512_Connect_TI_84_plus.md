---
title: "Connect TI 84 plus"
date: 2013-11-07
forum: General Help
---

### Post by r-ehl on 2013-11-07
Hey everyone,

who can I connect my TI 84 Plus with my Ubuntu 13.10 Laptop in order to copy some apps to my calculator?
I tried to use tilp, but every time on startup it shows:

> Msg: failed to open the USB device.
Cause: Check that the USB cable is plugged in and that the calculator is turned ON! Also, check libusb and usbfs for valid permissions.

No difference between root and normal user.

What can I do? Does anybody have experience concerning this?

Thanks in advance!

---

### Post by Old_Grey_Wolf on 2013-11-07
I found this on the [internet]("http://www.whitwellhigh.com/ubuntu.txt"). Hope it helps.

1) Install the tilp package and its dependencies like libticables2-2: sudo apt-get install tilp

2) Download the patch:
wget [https://launchpadlibrarian.net/79510370/new-devices-and-fixed-sysfs-warning.patch](https://launchpadlibrarian.net/79510370/new-devices-and-fixed-sysfs-warning.patch)

3) Apply the patch to the installed udev rules:
sudo patch /lib/udev/rules.d/45-libticables.rules < new-devices-and-fixed-sysfs-warning.patch 

4) Add yourself to the tilp group:
sudo usermod -a -G tilp $USER

5) Re-login to apply the group settings (Restart Computer)

6) The TI-84+ uses an USB-A - USB-B connector which is called DirectLink. This should be detected automatically. 
Connect the calculator now to the computer. If you've previously had connected it already, disconnect and reconnect it.

7) Now make known to tilp that you're using a TI-84+ calculator by running:
tilp --calc=ti84+ --cable=DirectLink

This will set the calc=TI84+ and cable_model=DirectLink in the ~/.tilp configuration file. After running the above command, it's sufficient to run just tilp in the future (using the application menu or by running the command directly).

---

