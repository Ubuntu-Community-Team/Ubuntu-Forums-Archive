---
title: "Arduino works only as root"
date: 2013-02-22
forum: General Help
---

### Post by sokopok on 2013-02-22
Hi, I'm having a big problem with arduino. 
Following the advice on the arduino forum, I removed the ubuntu version of arduino from my computer:
```
sudo apt-get purge arduino arduino-core
```Now I can only upload sketches to any board while being root.
I tried (for several days now) to find a solution, but nothing seems to work. Anybody can help me with this???

tomas@tomas:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise

tomas@tomas:~$ tail /var/log/kern.log
Feb 22 07:21:24 tomas kernel: [ 2316.604129] usb 2-1: new full-speed USB device number 15 using uhci_hcd
Feb 22 07:21:24 tomas kernel: [ 2316.793267] cdc_acm 2-1:1.0: ttyACM2: USB ACM device
Feb 22 07:21:31 tomas kernel: [ 2322.928074] usb 2-2: new full-speed USB device number 16 using uhci_hcd
Feb 22 07:21:31 tomas kernel: [ 2323.130337] cdc_acm 2-2:1.0: ttyACM3: USB ACM device
Feb 22 07:21:32 tomas kernel: [ 2324.488127] usb 2-1: USB disconnect, device number 15
Feb 22 07:21:32 tomas kernel: [ 2324.732085] usb 2-1: new full-speed USB device number 17 using uhci_hcd
Feb 22 07:21:32 tomas kernel: [ 2324.913293] cdc_acm 2-1:1.0: This device cannot do calls on its own. It is not a modem.
Feb 22 07:21:32 tomas kernel: [ 2324.913360] cdc_acm 2-1:1.0: ttyACM2: USB ACM device
Feb 22 07:21:33 tomas kernel: [ 2324.924480] input: Arduino LLC Arduino Leonardo as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.2/input/input16
Feb 22 07:21:33 tomas kernel: [ 2324.928604] generic-usb 0003:2341:8036.0006: input,hidraw0: USB HID v1.01 Mouse [Arduino LLC Arduino Leonardo] on usb-0000:00:1d.0-1/input2

crw-rw-rw- 1 root dialout 166, 0 Feb 22 07:05 /dev/ttyACM0
crw-rw-rw- 1 root dialout 166, 1 Feb 22 06:53 /dev/ttyACM1
crw-rw---- 1 root dialout 166, 2 Feb 22 07:21 /dev/ttyACM2
crw-rw-rw- 1 root dialout 166, 3 Feb 22 07:21 /dev/ttyACM3

tomas@tomas:~$ groups tomas
tomas : tomas adm tty uucp dialout cdrom sudo dip plugdev lpadmin sambashare

---

### Post by fdrake on 2013-02-22
do you need to be root or you can use sudo ?
if sudo wont work then post this
```

sudo less /etc/sudoers

```

---

### Post by sokopok on 2013-02-22
No problems with sudoers -> sudo ~/arduino-1.0.3/arduino works just fine. But I don't want to run arduino as root.

---

### Post by fdrake on 2013-02-22
> **sokopok said:**
> No problems with sudoers -> sudo ~/arduino-1.0.3/arduino works just fine. But I don't want to run arduino as root.

I don't know what arduino is . What exactly it does. Is it using some restricted forlder or devices?

> 
Description: Code, examples, and libraries for the Arduino platform
 Arduino is an open hardware microcontroller platform.  This package contains the minimal set of tools to allow one to program an Arduino.  It also contains
 examples and libraries. For a CLI, see the 'arduino-mk' package. 
 
 This package does not include the Java based Integrated Development Environment, which can be found in the 'arduino' package.
Homepage: [http://www.arduino.cc](http://www.arduino.cc)



is this some kind of IDE to create/run programs for microprocessors?

---

### Post by sokopok on 2013-02-22
One thing I forgot to mention:
The exact sequence of command I used, when removing the ubuntu version of arduino:

```
sudo apt-get purge arduino arduino-core
sudo apt-get update
sudo apt-get upgrade

```

Afterwards things were screwed up.

---

### Post by sokopok on 2013-02-22
Arduino is a microcontroller platform: they have all sorts of MCs, and an IDE to compile/upload programs to the controller.

Currently their site is down: [http://www.arduino.cc](http://www.arduino.cc)

---

### Post by fdrake on 2013-02-22
> **sokopok said:**
> No problems with sudoers -> sudo ~/arduino-1.0.3/arduino works just fine. But I don't want to run arduino as root.

why is it on your home dir? did you compiled from source or with the pack manager? what is the output for 
```

 ls -al ~/arduino-1.0.3/arduino

```

---

### Post by fdrake on 2013-02-22
> **sokopok said:**
> Arduino is a microcontroller platform: they have all sorts of MCs, and an IDE to compile/upload programs to the controller.

Currently their site is down: [http://www.arduino.cc](http://www.arduino.cc)

looks pretty cool! :D

---

### Post by sokopok on 2013-02-22
The version of the IDE shipped with ubuntu is quite old, I have a microcontroller that requires a newer version of the IDE. They only provide a .tgz with distribution-independent files.

```
tomas@tomas:~$ ls -la arduino-1.0.3/
total 92
drwxr-xr-x  8 tomas tomas  4096 Feb 22 06:17 .
drwxr-xr-x 64 tomas tomas 12288 Feb 22 07:01 ..
-rwxr-xr-x  1 tomas tomas   377 Feb 22 06:17 arduino
drwxr-xr-x 13 tomas tomas  4096 Dec 10 13:03 examples
drwxr-xr-x  4 tomas tomas  4096 Dec 10 13:03 hardware
drwxr-xr-x  3 tomas tomas  4096 Dec 10 13:03 lib
drwxr-xr-x 14 tomas tomas  4096 Dec 10 13:03 libraries
drwxr-xr-x  3 tomas tomas 16384 Dec 10 13:03 reference
-rw-r--r--  1 tomas tomas 36683 Dec 10 13:03 revisions.txt
drwxr-xr-x  3 tomas tomas  4096 Dec 10 13:03 tools

```


There is a permission problem somewhere. But I don't have the knowledge/skills to resolve this myself. I think (correct me if I'm wrong) it has something to do with 166 in:
```
crw-rw-rw- 1 root dialout 166, 0 Feb 22 07:05 /dev/ttyACM0
```

When searching google the common resolution is to add yourself to the dialout group, but I've been a member for years, so...

```
tomas@tomas:~$ groups tomas
tomas : tomas adm tty uucp dialout cdrom sudo dip plugdev lpadmin sambashare
```



[]("http://ubuntuforums.org/editpost.php?do=editpost&p=12523493")

---

### Post by fdrake on 2013-02-22
is /dev/ttyACM0 used by  arduino ? a character (unbuffered) device file . 
why don'e you try to make it executable and is if it works?
```

sudo chmod a+x /dev/ttyACM0

```

---

### Post by sokopok on 2013-02-22
>          is /dev/ttyACM0 used by  arduino ?Yes, this is the port use to talk to the arduino board. I think this is created by udev.

> why don'e you try to make it executable and is if it works?I don't really want to make it anything. When unplug the board (USB connection), or reboot all changes will be lost (I think, udev is not my speciality).
```

tomas@tomas:~$ sudo chmod a+x /dev/ttyACM*
[sudo] password for tomas: 
```no changes

---

### Post by fdrake on 2013-02-22
what kinds of errors do you get while sunning as regular user ?
 try to run aruino via terminal , and try to access the board. Does the termianl outputs anything?

also this might help too
> 
less /var/log/syslog | grep -i -e ttyACM -e error


---

### Post by sokopok on 2013-02-22
as me:
```
tomas@tomas:~/arduino-1.0.3$ ./arduino 
Experimental:  JNI_OnLoad called.
Stable Library
=========================================
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
Binary sketch size: 1,084 bytes (of a 32,256 byte maximum)
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
processing.app.SerialException: Error opening serial port '/dev/ttyACM2'.
        at processing.app.Serial.<init>(Serial.java:178)
        at processing.app.Serial.<init>(Serial.java:77)
        at processing.app.debug.Uploader.flushSerialBuffer(Uploader.java:77)
        at processing.app.debug.AvrdudeUploader.uploadViaBootloader(AvrdudeUploader.java:174)
        at processing.app.debug.AvrdudeUploader.uploadUsingPreferences(AvrdudeUploader.java:67)
        at processing.app.Sketch.upload(Sketch.java:1671)
        at processing.app.Sketch.exportApplet(Sketch.java:1627)
        at processing.app.Sketch.exportApplet(Sketch.java:1599)
        at processing.app.Editor$DefaultExportHandler.run(Editor.java:2380)
        at java.lang.Thread.run(Thread.java:679)
Caused by: gnu.io.UnsupportedCommOperationException: Invalid Parameter
        at gnu.io.RXTXPort.setSerialPortParams(RXTXPort.java:171)
        at processing.app.Serial.<init>(Serial.java:163)
        ... 9 more
processing.app.debug.RunnerException: Error opening serial port '/dev/ttyACM2'.
        at processing.app.debug.Uploader.flushSerialBuffer(Uploader.java:101)
        at processing.app.debug.AvrdudeUploader.uploadViaBootloader(AvrdudeUploader.java:174)
        at processing.app.debug.AvrdudeUploader.uploadUsingPreferences(AvrdudeUploader.java:67)
        at processing.app.Sketch.upload(Sketch.java:1671)
        at processing.app.Sketch.exportApplet(Sketch.java:1627)
        at processing.app.Sketch.exportApplet(Sketch.java:1599)
        at processing.app.Editor$DefaultExportHandler.run(Editor.java:2380)
        at java.lang.Thread.run(Thread.java:679)

```

as root:
```
tomas@tomas:~/arduino-1.0.3$ sudo ./arduino 
[sudo] password for tomas: 
Experimental:  JNI_OnLoad called.
Stable Library
=========================================
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7
RXTX Warning:  Removing stale lock file. /var/lock/LCK..ttyACM2
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists
Binary sketch size: 1,084 bytes (of a 32,256 byte maximum)
RXTX fhs_lock() Error: creating lock file: /var/lock/LCK..ttyACM0: File exists

```

---

### Post by fdrake on 2013-02-22
> 
processing.app.SerialException: Error opening serial port '/dev/ttyACM2

it looks like they differ from the others acms
> crw-rw---- 1 root dialout 166, 2 Feb 22 07:21 /dev/ttyACM2
athe other acms have also wr permission of users outside the group. 
i don't understand you are in the group, you are not outside.

---

### Post by sokopok on 2013-02-22
>  i don't understand you are in the group, you are not outside.That's why I posted this message...

I screwed around with the permissions a bit, so they probably aren't clean anymore... I'll do a reboot and try again...

---

### Post by cdaringe on 2013-02-22
arduino in ubuntu.  oh the many problems I've had.  not that this particularly helps, but i did have a similiar issue to that which you are describing.  mine was resolved by adding myself to a particular user group.  it may have not been the dialout group.  are you using <v23 or post 1.0?  I had to stick w/ v22 i recall.  havent tried in a while.  using the installer from the std repo didn't fly either--i had to install from the arduino site.  many others ran into this too.

---

### Post by fdrake on 2013-02-22
> **sokopok said:**
> That's why I posted this message...

i found another hint /var/lock/LCK..ttyACM2.
i think this is the reason why you can't run it .

root is able to removes lock files
> 
RXTX Warning:  Removing stale lock file. /var/lock/LCK..ttyACM2

and open so serial port '/dev/ttyACM2';

where insetad a reg user cant and it gets the msg:
```
processing.app.debug.RunnerException: Error opening serial port '/dev/ttyACM2'.
``` try removing the lock file in the "ttyACM2" /var/lock/.. folders

---------------------------------------------------------------------------------------------------

for more info on locks see [http://linux.about.com/od/lsa_guide/a/gdelsa20.htm](http://linux.about.com/od/lsa_guide/a/gdelsa20.htm)

---

### Post by sokopok on 2013-02-22
> **cdaringe said:**
> arduino in ubuntu.  oh the many problems I've had.  not that this particularly helps, but i did have a similiar issue to that which you are describing.  mine was resolved by adding myself to a particular user group.  it may have not been the dialout group.  are you using <v23 or post 1.0?  I had to stick w/ v22 i recall.  havent tried in a while.  using the installer from the std repo didn't fly either--i had to install from the arduino site.  many others ran into this too.
Yes I know! The thing is: it (kind of) used to work (a couple of days ago), but since I removed the ubuntu repo version of arduino: AAAARGHH

---

### Post by fdrake on 2013-02-22
any luck with removing the lock file?

---

### Post by sokopok on 2013-02-22
That's not the problem. I just rebooted, and no go:

before plugging in the arduino:

```
tomas@tomas:~$ ls -la /dev/ttyACM*
ls: cannot access /dev/ttyACM*: No such file or directory

tomas@tomas:~$ ls -la /var/lock/
total 3
drwxrwxrwt  3 root     root   80 Feb 22 09:21 .
drwxr-xr-x 24 root     root  840 Feb 22 09:14 ..
drwxr-xr-x  2 www-data root   40 Feb 22 09:14 apache2
tomas@tomas:~$ 

```
so there is no lock file.

after plugging in:

```
tomas@tomas:~$ ls -la /dev/ttyACM*
crw-rw-rw- 1 root dialout 166, 0 Feb 22 09:16 /dev/ttyACM0

```

---

### Post by sokopok on 2013-02-22
sorry forgot this:

tomas@tomas:~$ ls -la /var/lock/
total 4
drwxrwxrwt  3 root     root   80 Feb 22 09:21 .
drwxr-xr-x 24 root     root  840 Feb 22 09:14 ..
drwxr-xr-x  2 www-data root   40 Feb 22 09:14 apache2
-r--r--r--  1 tomas    tomas  11 Feb 22 09:21 LCK..ttyACM0


the lock file i owned by me


tomas@tomas:~$ rm /var/lock/LCK..ttyACM0 
rm: remove write-protected regular file `/var/lock/LCK..ttyACM0'? y

no sudo used

---

### Post by fdrake on 2013-02-22
[IMG]http://barbkampbell.com/wp-content/uploads/2010/10/wve-white-flag-260.jpg[/IMG]

---

### Post by sokopok on 2013-02-22
You bas***! I guess I'll give up myself. This project needed to be finished already!
I think I might start using Win*** again...

---

### Post by fdrake on 2013-02-22
> **sokopok said:**
> You bas***! I guess I'll give up myself. This project needed to be finished already!
I think I might start using Win*** again...
we must be missing something not important. Hopefully the ubunut repo will upgrade the version soon.

---

### Post by sokopok on 2013-02-22
That would be great, but it won't help me. The repo version gives me the same results now =(

---

