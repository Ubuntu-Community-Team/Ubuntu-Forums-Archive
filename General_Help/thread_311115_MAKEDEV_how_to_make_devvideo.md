---
title: "MAKEDEV how to make /dev/video"
date: 2006-12-02
forum: General Help
---

### Post by cd-r80 on 2006-12-02
How to make /dev/video? And why I don't have it (Xubuntu 6.06 alt. install)?

---

### Post by reclusivemonkey on 2006-12-03
> **cd-r80 said:**
> How to make /dev/video? And why I don't have it (Xubuntu 6.06 alt. install)?

What device do you have that should be mapped to /dev/video? With udev now as I understand it, only devices that you actually have in your machine are created.

---

### Post by cd-r80 on 2006-12-03
I have quickcam messenger for what I need /dev/video. At boot it is connected. I made new /dev/videos with a script I found. Everything was working, but now after reboot there is no more /dev/video. Quickcam was working...

---

### Post by reclusivemonkey on 2006-12-03
> **cd-r80 said:**
> I have quickcam messenger for what I need /dev/video. At boot it is connected. I made new /dev/videos with a script I found. Everything was working, but now after reboot there is no more /dev/video. Quickcam was working...

udev should make this device for you when you boot. I suspect whatever script you use, it will be overwritten by udev at each boot. What did you do to get the quickcam messenger working?

---

### Post by cd-r80 on 2006-12-03
I run this script or something:
#!/bin/bash

function makedev () {
for dev in 0 1 2 3; do
echo "/dev/$1$dev: char 81 $[ $2 + $dev ]"
rm -f /dev/$1$dev
mknod /dev/$1$dev c 81 $[ $2 + $dev ]
chmod 666 /dev/$1$dev
done

# symlink for default device
rm -f /dev/$1
ln -s /dev/${1}0 /dev/$1
}

echo "*** new device names ***"
makedev video 0
makedev radio 64
makedev vtx 192
makedev vbi 224

Download and install from [http://home.mag.cx/messenger/:](http://home.mag.cx/messenger/:)
qc-usb-messenger-1.5.tar.gz

---

### Post by reclusivemonkey on 2006-12-03
> **cd-r80 said:**
> 
Download and install from [http://home.mag.cx/messenger/:](http://home.mag.cx/messenger/:)
qc-usb-messenger-1.5.tar.gz

Have you loaded the modules for your cam? Does the cam work after running that script? I have a Dexxa webcam, and it works just fine without the need to make any devices.

---

### Post by cd-r80 on 2006-12-03
I rerun the script, but it did not help . I run again quickcam.sh & it started to work. Or I have reboot and check again with AMSN. Quickcam modules were loaded at boot.

---

### Post by cd-r80 on 2006-12-03
No. It is not. I now see that makedev script is not helping or doing anything. It is quickcam.sh which helps load modules again correctly. I don't know why they do not work allthought after reboot I have:
lsmod:
usbcore               129668  4 quickcam
videodev                9856  1 quickcam

---

### Post by reclusivemonkey on 2006-12-03
> **cd-r80 said:**
> No. It is not. I now see that makedev script is not helping or doing anything. It is quickcam.sh which helps load modules again correctly. I don't know why they do not work allthought after reboot I have:
lsmod:
usbcore               129668  4 quickcam
videodev                9856  1 quickcam

The quickcam.sh tells you to edit certain files. You should add the items it tells you to rc.local (before exit 0) and they should load for you each boot.

---

### Post by cd-r80 on 2006-12-03
Well, I will try to find what. I have only quickcam in /etc/modules. Thankss..

---

### Post by Stemp on 2006-12-03
I created a /dev/webcam with udev for my Labtech Webcam Pro.

1° Find the ID of your webcam with lsusb :
Bus 001 Device 003: ID **046d**:**08a2** Logitech, Inc. Labtec WebCam Pro

2°  create a file /etc/udev/rules.d/99-perso.rules and add your rule :
KERNEL=="video*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="08a2", SYMLINK+="webcam"
of course change de idVendor or idProduct

[Edit] : I forgot to restart udev --> sudo /etc/init.d/udev restart

---

### Post by cd-r80 on 2006-12-03
I made:
KERNEL=="video*", SYSFS{Logitech, Inc.}=="046d", SYSFS{Quickcam Messenger}=="08f0", SYMLINK+="webcam"

But it does not help, no dev after restart udev. I found sysv... no udev at boot I try to reboot also

I have udev run at runlevels 5 0 6 S. No help.

---

### Post by Stemp on 2006-12-03
KERNEL=="video*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="08f0", SYMLINK+="webcam"

---

### Post by cd-r80 on 2006-12-03
Not working, yet.
Ok:
KERNEL=="video*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="08f0", SYMLINK+="webcam"

I cannot see typing errors.
lsusb
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

---

### Post by Stemp on 2006-12-03
No creation of a /dev/webcam ?

---

### Post by cd-r80 on 2006-12-03
No creation of /dev/webcam.

99-perso.rules
etc/init.d/udev restart
 * Loading additional hardware drivers... [ok]

ls /dev/
...vcsa -> zero.

I have blacklist:
blacklist snd_usb_lib
blacklist snd_usb_audio

I dont't want webcam take sound...

---

### Post by cd-r80 on 2006-12-04
I don't know udev does not make video devices. I have line:
KERNEL=="video*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="08f0", SYMLINK+="webcam"

Can I update udev or check it someway?
lsusb:
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

ls /sys/bus/usb/devices...:
KERNEL=="1-2"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="ff"
    SYSFS{bDeviceProtocol}=="ff"
    SYSFS{bDeviceSubClass}=="ff"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 3"
    SYSFS{bcdDevice}=="0100"
    SYSFS{bmAttributes}=="a0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="4"
    SYSFS{idProduct}=="08f0"
    SYSFS{idVendor}=="046d"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="Camera"
    SYSFS{speed}=="12"
    SYSFS{version}==" 2.00"

Is this Xubuntu problem? I used this cam before with Ubuntu Breezy.

---

### Post by Stemp on 2006-12-04
I don't think it's a Xubuntu or udev problem.
It seems that you webcam is not recognize.

---

### Post by cd-r80 on 2006-12-04
Who knows how that quickcam.sh can set up the modules and devices correctly? Because after that the /dev/video is made and webcam works...until reboot. I haven't much used awk,sed...
Or better when & where to put that mknod part so that works with reboot?

Part of:
VIDEODEV=`dmesg | awk '/quickcam: Registered device:/ { print $5 }' | head -n 1`
VIDEODEV_REAL="`$REALPATH $VIDEODEV`"
echo "I will be using $VIDEODEV, if there are more cameras I'll not test them."
askreturn
echo "Testing if $VIDEODEV is correct."
ls -la "$VIDEODEV"
if [ "$VIDEODEV" != "$VIDEODEV_REAL" ]; then
        ls -la "$VIDEODEV_REAL"
        echo "$VIDEODEV is a symbolic link to $VIDEODEV_REAL."
fi
if [ ! -r "$VIDEODEV_REAL" -o ! -w "$VIDEODEV_REAL" ]; then
        echo "[!] You don't have read/write access to $VIDEODEV."
        echo "On many distributions, you should add yourself into the"
        echo "\"video\" group by giving command"
        echo "  adduser `whoami` video"
        echo "and then log in again to be able to access the video."
        echo "A quick alternative is just to do"
        echo "  chmod a+rw $VIDEODEV_REAL"
        askreturnfail
fi
VIDEODEV_MAJ=`ls -la "$VIDEODEV_REAL" | awk '{print $5}' | tr -d ','`
VIDEODEV_MIN=`ls -la "$VIDEODEV_REAL" | awk '{print $6}'`
if [ "$VIDEODEV_MAJ" != "81" ]; then
        echo "[!] $VIDEODEV_REAL major number is $VIDEODEV_MAJ."
        echo "Usually it should be 81, so there are problems ahead."
        askreturnfail
fi
CAMERA_MIN=`echo $VIDEODEV | sed 's,.*/[^0-9]*\([0-9]*\),\1,g'`
if [ "$CAMERA_MIN" != "$VIDEODEV_MIN" ]; then
        echo "[!] Bad minor number $VIDEODEV_MIN in $VIDEODEV_REAL, should be $CAMERA_MIN."
        echo "To correct this problem, remove the bad file $VIDEODEV_REAL and"
        echo "recreate it with mknod-command (read man mknod). Example:"
        echo "  rm -f $VIDEODEV"
        echo "  mknod $VIDEODEV c 81 $CAMERA_MIN"
        echo "  chmod a+rw $VIDEODEV"
        askreturnfail
fi

---

### Post by cd-r80 on 2006-12-05
At last it works! What is the problem with modprobe! It was a change from modprobe to insmod. Using insmod instead of modprobe or just rmmod & reload quickcam things started to work with reboot.

Thanks to Faqs, Howtos:
[http://www.ubuntuforums.org/showthread.php?t=191770&page=6](http://www.ubuntuforums.org/showthread.php?t=191770&page=6)
benvdh

I don't even have those 99-personal.rules for udev.

AMSN & all allright!

---

