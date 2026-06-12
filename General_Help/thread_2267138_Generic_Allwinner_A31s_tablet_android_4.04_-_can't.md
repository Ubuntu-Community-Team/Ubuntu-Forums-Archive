---
title: "Generic Allwinner A31s tablet android 4.04 - can't get usb debugging (adb)"
date: 2015-02-27
forum: General Help
---

### Post by aspidistra on 2015-02-27
[COLOR=#000000]lsusb gives me :[/COLOR]

[COLOR=#000000]Bus 002 Device 003: ID 1f3a:1000 [/COLOR]

[COLOR=#000000]so I update /etc/udev/rules.d/51-android.rules to be[/COLOR]

[COLOR=#000000]why or what is that file specifically "51-android-rules" - some sites say '99-android-rules'[/COLOR]

[COLOR=#000000]SUBSYSTEM=="usb", ATTR{idVendor}=="1f3a", ATTR{idProduct}=="1000", MODE="0600", OWNER="dan"[/COLOR]



[COLOR=#000000]then I update[/COLOR]

[COLOR=#000000].android/adb_usb.ini[/COLOR]


[COLOR=#000000]to contain[/COLOR]
[COLOR=#000000]0x1f3a[/COLOR]

[COLOR=#000000]as instructed[/COLOR]

[COLOR=#000000]adb devices (command)[/COLOR]
[COLOR=#000000]List of devices attached [/COLOR]

[COLOR=#000000]blank - nothing[/COLOR]

[COLOR=#000000]could there be other requirements apart from adb[/COLOR]

---

### Post by aspidistra on 2015-02-27
further -- got an idea that 

it needs "allwinner usb" driver

[border]
[COLOR=#000000][FONT=Arial]To get the tools, go to the git repository at [https://github.com/linux-sunxi/sunxi-tools/](https://github.com/linux-sunxi/sunxi-tools/) and download the ZIP file (called sunxi-tools-master.zip). Extract this, and place the folder on the Desktop of your Linux machine. Open a terminal, cd to the folder, then run[/FONT][/COLOR]sudo apt-get install libusb-1.0-0-dev[COLOR=#000000][FONT=Arial](this installs libusb, which is required for compilation). Then type **make** which should compile the files. This creates two programs (actually it creates a lot more, but these are the only two we're interested in) called **bin2fex** and**fex2bin**.[/FONT][/COLOR][/border]

about to try to get the module "awusb.ko" (I think that produces)

which can be inserted into the kernel  

[COLOR=#000000][FONT=sans-serif]Now, as root, install the module in your module tree, and load it:[/FONT][/COLOR]
cp awusb.ko /lib/modules/`uname -r`/extra/
depmod -a
modprobe awusb.ko


as (I think) - "allwinner" boards need this software in order for linux to address usb

---

### Post by aspidistra on 2015-02-27
awusb.ko is installed as driver

lsmod | grep usb
awusb                  12958  0 
usb_storage            62209  0 

android has the vendor

~/.android$ cat *.ini
0x1f3a

android rules - should that be root or the user

cat 51-android.rules
SUBSYSTEM=="usb", ATTR{idVendor}=="1f3a", ATTR{idProduct}=="1000", MODE="0600", OWNER="root"



adb devices
nothing there

---

### Post by aspidistra on 2015-02-27
this - supposed to enable the awusb kernel module

[h=3]Fedora[/h][COLOR=#000000][FONT=sans-serif]Before you can build this module, you first could need to install *dkms* and *libusbx* (maybe you need also *nas-libs*)[/FONT][/COLOR]
yum install dkms libusbx nas-libs[COLOR=#000000][FONT=sans-serif]Now descend into the *awusb* directory and run[/FONT][/COLOR]
make[COLOR=#000000][FONT=sans-serif]Now, as root, install the module in your module tree, and load it:[/FONT][/COLOR]
cp awusb.ko /lib/modules/`uname -r`/extra/
depmod -a
modprobe awusb.ko[COLOR=#000000][FONT=sans-serif]Add the following *50-awusb.rules* file to */etc/udev/rules.d*, to be able to access the device as a normal user:[/FONT][/COLOR]
SUBSYSTEM!="usb_device",ACTION!="add",GOTO="objdev_rules_end"
#USBasp
ATTRS{idVendor}=="1f3a",ATTRS{idProduct}=="efe8",GROUP="yuorgrupid",MODE="0666"
LABEL="objdev_rules_end"[COLOR=#000000][FONT=sans-serif]where "yuorgrupid" have to be substituted by the group id of your user.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Now reload udev rules to make the change active[/FONT][/COLOR]
udevadm control --reload-rules

---

### Post by aspidistra on 2015-02-27
the allwinner is the most generic android device in the UK the one which is cheapest on ebay - most widely sold

---

### Post by aspidistra on 2015-02-27
did this, effectively - lsusb now shows "allwinner a31"

but ..

"[COLOR=#000000][FONT=verdana]his is what i did[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]1, added the correct USB Ids to /var/lib/usbutils/usb.ids[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]2207 RocketChip[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]0006 MK908[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]now lsusb should show the device properly[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2, add udev rule in /etc/udev/rules.d/51-android.rules[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]SUBSYSTEM=="usb", ATTR{idVendor}=="2207", MODE="0666", GROUP="plugdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]restart udev service[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]3, added vendor id in ~/.android/adb_usb.ini[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]0x2207[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]restart adb server[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]connect MK908, enable usb "connect pc" and usb debugging.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]now adb devices shows the device. [I had to do connect PC couple of times.. :-) ]"

the allwinner usb module is present

list devices shows nothing

=========================================================

[/FONT][/COLOR]dan@f2:~$ lsusb
Bus 002 Device 003: ID 1f3a:1000 allwinner a31s
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dan@f2:~$ adb devices
List of devices attached

---

