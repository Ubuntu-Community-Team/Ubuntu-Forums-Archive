---
title: "run program when ubuntu awakens from sleep?"
date: 2014-04-09
forum: General Help
---

### Post by sdowney717 on 2014-04-09
I would like to run xgps when the pc wakes up.

---

### Post by monkeybrain20122 on 2014-04-09
Is xgps set to autostar? If yes perhaps you can modify the solution I got from Toz [http://ubuntuforums.org/showthread.php?t=2213306](http://ubuntuforums.org/showthread.php?t=2213306)

---

### Post by Toz on 2014-04-09
The proper place to startup processes after sleep/hibernate is via scripts in /etc/pm/sleep.d. However, those scripts are executed as root and do not have access to any X environments. If xgps is an X program, you'll need to export the DISPLAY and XAUTHORITY variables before trying to run the script as a user. An example of doing this can be found in [this]("http://ubuntuforums.org/showthread.php?t=2213306") thread.

EDIT: ninja'd :)

---

### Post by sdowney717 on 2014-04-10
Thanks, that actually helped make it work.
[http://ubuntuforums.org/showthread.php?t=2215968&page=3&p=12983608#post12983608](http://ubuntuforums.org/showthread.php?t=2215968&page=3&p=12983608#post12983608)

Can you look at my post 26 and 27 and 28?

I managed to get my usb gps to work without hotplugging after awake from sleep. :)

But my solution kills the wired LAN network leaving it unconfigured.

All I did was delete /lib/udev/rules.d/40-gpsd.rules

Put in my custom rules file '70-persistent-usb-gps.rules' in its place

I dont think your script to run a program kills the LAN, something in my rules file?

```
# 
# Author: Fulup Ar Foll
# Date:   26-jun-09
# Object: make sure GPS dev (ex: /dev/gps-usb) dont change name on sleep/wakeup
# -----------------------------------------------------------------------------
#
# 1) place this file in /etc/udev/rules.d
# 2) use default config or update with your own vendor:product ID (use "lsusb" to find them)
# 3) reload udev with "/etc/init.d/udev reload"
#
# Device alias can be:
#  (default) - by path  ==> SYMLINK="serial-$env(ID_PATH)"   /dev/gps-pci-0000:00:1d.1-usb-0:1:1.0
#            - static   ==> SYMLINK="gps-usb"                /dev/gps-usb
#            - custom   ==> RUN+="/usr/local/bin/myscript"   /dev/any-thingk-you-want
#
# DEFAULT CONFIG: you can use this file "as it is", you should then see a /dev/gps-pci* 
# that will be created for any of the serial/usb you hot-plug. The name is fixe but
# depend on the USB port you use. As a result the name is fix until you keep the same socket.
#
# -----------------------------------------------------------------------
# check "man 7 udev" for forther syntax. (search for %n)
# -----------------------------------------------------------------------

# Examples
# -----------------------------------------------------------------------
# Your own script:     SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", RUN+="/usr/local/bin/myscript"
# Static device name:  SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", SYMLINK="gps-usb"
# Path dependent name: SUBSYSTEM=="tty", ATTRS{idVendor}=="xxxx", ATTRS{idProduct}=="yyyy", SYMLINK="gps-$env{ID_PATH}"
# In first case you do what ever you want, script receive the information about context in environement variables
# In second case you name is fixe (ex: /dev/gps-usb) this is working if your usb/serial ID(vendor:product) is unique
# In third case your device name depend on the port it is plugged in.


# ========================================================================================
#                          update YOUR CONFIG here after
# ========================================================================================

# Default rules is applied for any unspecified vendor:product devices
# -----------------------------------------------------------------------------------------
#SUBSYSTEM=="tty", ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK="gps-$env{ID_PATH}"

# Well known device may get a static device name 
# -----------------------------------------------------------------------
SUBSYSTEM=="tty", ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK="ttyGPS-usb"
SUBSYSTEM=="tty", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", SYMLINK="ttyGPS-rt650"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="5740", SYMLINK="ttyGPS-ait2000"
SUBSYSTEM=="tty", ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK="ttyGPS-lt20"

# ************************************************************************************
# WARNING: on Ubuntu version version 13 and more. Standard user does not have acces
#          to dialout group. In order to enable opencpn to access usb devices you
#          should enter following command in a terminal:
#       
#          sudo usermod -a -G dialout $LOGNAME 
#
# ***************************************************************************************
```

this was there 40-gpsd.rules

```
# udev rules for gpsd
#
# This file is Copyright (c) 2010 by the GPSD project
# BSD terms apply: see the file COPYING in the distribution root for details.
#
# GPSes don't have their own USB device class.  They're serial-over-USB
# devices, so what you see is actually the ID of the serial-over-USB chip.
# Fortunately, just two of these account for over 80% of consumer-grade
# GPS sensors.  The gpsd.hotplug wrapper script will tell a running gpsd
# that it should look at the device that just went active, because it
# might be a GPS.
#
# The following setup works on Debian and Ubuntu - something similar
# will apply on other distributions:
# 
#   /lib/udev/rules.d/25-gpsd.rules
#   /lib/udev/gpsd.hotplug
# 
# Setting the link in /lib/udev/rules.d activates the rule and determines
# when to run it on boot (similar to init.d processing).

SUBSYSTEM!="tty", GOTO="gpsd_rules_end"

# Prolific Technology, Inc. PL2303 Serial Port [linux module: pl2303]
ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# ATEN International Co., Ltd UC-232A Serial Port [linux module: pl2303]
ATTRS{idVendor}=="0557", ATTRS{idProduct}=="2008", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# PS-360 OEM (GPS sold with MS Street and Trips 2005) [linux module: pl2303]
ATTRS{idVendor}=="067b", ATTRS{idProduct}=="aaa0", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# FTDI 8U232AM / FT232 [linux module: ftdi_sio]
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cypress M8/CY7C64013 (Delorme uses these) [linux module: cypress_m8]
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0100", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cypress M8/CY7C64013 (DeLorme LT-40)
ATTRS{idVendor}=="1163", ATTRS{idProduct}=="0200", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug" 
# Garmin International GPSmap, various models (tested with Garmin GPS 18 USB)  [linux module: garmin_gps]
ATTRS{idVendor}=="091e", ATTRS{idProduct}=="0003", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cygnal Integrated Products, Inc. CP210x Composite Device (Used by Holux m241 and Wintec grays2 wbt-201) [linux module: cp210x]
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", SYMLINK+="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# Cygnal Integrated Products, Inc. [linux module: cp210x]
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea71", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# u-blox AG, u-blox 5 (tested with Navilock NL-402U) [linux module: cdc_acm]
ATTRS{idVendor}=="1546", ATTRS{idProduct}=="01a5", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# u-blox AG, u-blox 6 (tested with GNSS Evaluation Kit TCXO) [linux module: cdc_acm]
ATTRS{idVendor}=="1546", ATTRS{idProduct}=="01a6", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"
# MediaTek (tested with HOLUX M-1200E) [linux module: cdc_acm]
ATTRS{idVendor}=="0e8d", ATTRS{idProduct}=="3329", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug"

ACTION=="remove", RUN+="/lib/udev/gpsd.hotplug"

LABEL="gpsd_rules_end"
```

---

### Post by sdowney717 on 2014-04-10
can this be put into the script file?

sudo service network-manager restart

I have to test and see what it will do.

---

