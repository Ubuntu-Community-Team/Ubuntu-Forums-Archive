---
title: "Mounting Android phone in 16.04.6 LTS"
date: 2019-08-31
forum: General Help
---

### Post by oygle on 2019-08-31
I had been following this tutorial at [https://ubuntuforums.org/showthread.php?t=2226702](https://ubuntuforums.org/showthread.php?t=2226702) (now closed) and got to step 4 ..

```
sudo nano /lib/udev/rules.d/69-mtp.rules
```

but that file is blank.Results from lsusb

```
lsusb
```

> Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0c45:670b Microdia 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 041: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Have also done the following from [https://askubuntu.com/questions/854332/how-to-connect-android-7-1-to-ubuntu-linux-with-usb](https://askubuntu.com/questions/854332/how-to-connect-android-7-1-to-ubuntu-linux-with-usb)

> 

Here's what I found works:

    First, ignore all the web comments you've seen about /etc/udev/rules.d/51-android.rules. That file isn't needed.

    Second, skip mtp-tools. They aren't documented, and jmtpfs is far easier anyway.

    Install the jmtpfs package: sudo apt-get install jmtpfs
    Make a directory, any directory: sudo mkdir /media/myphone
    Connect the USB cable
    Unlock the android phone.
    Swipe down from the top of the phone screen
    You should see a notification "USB ..."
    Tap that notification.

    You should see a menu titled "Use USB to...", select "Transfer files".

    On the linux computer issue:

sudo jmtpfs /media/myphone

ls /media/myphone

fusermount -u /media/myphone

It is a Galaxy S4, Model GT-I9506, Android version 5.0.1

Any ideas please ?

---

### Post by mörgæs on 2019-09-01
[Libmtp]("https://launchpad.net/ubuntu/+source/libmtp"), which was in version 1.10 in Buntu 16.04, has now reached 1.16. 

I would try how it works in a clean install of 19.04.

---

### Post by oygle on 2019-09-01
> **mörgæs said:**
> [Libmtp]("https://launchpad.net/ubuntu/+source/libmtp"), which was in version 1.10 in Buntu 16.04, has now reached 1.16. 

I would try how it works in a clean install of 19.04.

Thanks for your reply. The version of libmtp I have is 1.1.10-2ubuntu1 , so I guess it would need a Kubuntu upgrade to get the latest. Have been wanting to upgrade for a while, thanks.

---

### Post by oygle on 2019-09-06
Tried this on 18.04 and still problems. It kept coming up with the " asking to allow data access ". I select "allow" and a few seconds later, the message appears again.

---

### Post by SeijiSensei on 2019-09-07
Are you still trying to use jmtpfs to mount the phone, or are you just letting Kubuntu do it natively?  Connecting the phone and computer with a USB cable on my Kubuntu 19.04 machine brings up the Device Notifier dialog offering to select between camera and file manager.  I think it did that in 18.04, too, but it's been a while since I last used it. For some reason the File Manager item appears twice, and only one of them works.

It also shows up in the Devices section of Dolphin.

Of course, you have to have set the phone to use MTP mode.  It looks like you've done that already though.

---

### Post by Autodave on 2019-09-07
Some phones have (in Settings) a place that allows it to be mounted.  Make sure that that is enabled.

---

### Post by oygle on 2019-09-07
> **SeijiSensei said:**
> Are you still trying to use jmtpfs to mount the phone, or are you just letting Kubuntu do it natively?

As the install of jmtpfs worked but the other commands didn't, I removed jmtpfs. then searched for 'mtp' in synaptic

> go-mtpfs
libmtp-*
libmtp9
mtp-tools

and why I list those is because there may be conflicts ?? 

> **SeijiSensei said:**
> Connecting the phone and computer with a USB cable on my Kubuntu 19.04 machine brings up the Device Notifier dialog offering to select between camera and file manager.  I think it did that in 18.04, too, but it's been a while since I last used it. For some reason the File Manager item appears twice, and only one of them works.

Yes, the dialogue comes up, there are 3 options. One is for a camera and the other 2 for mtp. I have tested selecting both of them, and it is like it is stuck in a loop. That is, I select from the dialogue, then the phone asks this 'deny/allow" access message. I always say 'allow', and then it comes up with another dialogue in Kubuntu with those 3 options.

> **SeijiSensei said:**
> It also shows up in the Devices section of Dolphin.

Yes it does, sometimes, but if I try to select that in Dolphin, back it goes to that dialogue loop again.

> **SeijiSensei said:**
> Of course, you have to have set the phone to use MTP mode.  It looks like you've done that already though.

Yes it is definitely in MTP mode. But even if I get MTP going, what I **_really_** want to do is mount it, so that I can then use a file compare tool to copy/compare a lot of files that need restoring. A file manager just isn't the same, but , MTP is not going.

> **Autodave said:**
> Some phones have (in Settings) a place that allows it to be mounted.  Make sure that that is enabled.

Yes, I had an S2 and it was so easy to mount. Just select the option on the phone, connect cable and worked perfectly.

Btw, I have tried other cables, as some people suggest, and used a cable that worked as a usb/mount with that S2. Here is some info ..

$ **mtp-detect**

> libmtp version: 1.1.13

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 2, dev 10
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Error 1: Get Storage information failed.
USB low-level info:                                                                                                                                                                
   bcdUSB: 528                                                                                                                                                                     
   bDeviceClass: 0                                                                                                                                                                 
   bDeviceSubClass: 0                                                                                                                                                              
   bDeviceProtocol: 0                                                                                                                                                              
   idVendor: 04e8                                                                                                                                                                  
   idProduct: 6860                                                                                                                                                                 
   IN endpoint maxpacket: 512 bytes                                                                                                                                                
   OUT endpoint maxpacket: 512 bytes                                                                                                                                               
   Raw device info:                                                                                                                                                                
      Bus location: 2                                                                                                                                                              
      Device number: 10                                                                                                                                                            
      Device entry info:                                                                                                                                                           
         Vendor: Samsung                                                                                                                                                           
         Vendor id: 0x04e8                                                                                                                                                         
         Product: Galaxy models (MTP)                                                                                                                                              
         Vendor id: 0x6860                                                                                                                                                         
         Device flags: 0x48000202                                                                                                                                                  
Configuration 0, interface 0, altsetting 0:                                                                                                                                        
   Interface description contains the string "MTP"                                                                                                                                 
   Device recognized as MTP, no further probing.                                                                                                                                   
Device info:                                                                                                                                                                       
   Manufacturer: Samsung Electronics Co., Ltd.                                                                                                                                     
   Model: SM-G900I                                                                                                                                                                 
   Device version: G900IDVU1CQD11&d44a9a68                                                                                                                                         
   Serial number: R58F50YA4JZ                                                                                                                                                      
   Vendor extension ID: 0x00000006                                                                                                                                                 
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMPPD: 11.0; microsoft.com/WMPPD: 10.0;samsung.com/kies:3.0;samsung.com/devicestatus:1;samsung.com/sidesync3.1; 
   Detected object size: 64 bits                                                                                                                                                   
   Extensions:                                                                                                                                                                     
        microsoft.com: 1.0                                                                                                                                                         
        microsoft.com/WMPPD: 11.0                                                                                                                                                  
        microsoft.com/WMPPD: 10.0
        samsung.com/kies: 3.0
        samsung.com/devicestatus: 1.0
Supported operations:
   1001: Get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100b: Delete object
   100c: Send object info
   100d: Send object
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   101b: Get partial object
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9201: Report Added/Deleted Items
   9202: Report Acquired Items
   100a: Get thumbnail
   1011: Self test device
   1012: Set object protection
   1017: Reset device property value
   1019: Move object
   101a: Copy object
   9807: Get interdependent property description
   9808: Send object property list
   9501: Unknown PTP_OC
   9502: Unknown PTP_OC
   9503: Unknown PTP_OC
   9504: Unknown PTP_OC
Events supported:
   0x4002 ((null))
   0x4003 ((null))
   0x4004 ((null))
   0x4005 ((null))
   0x400c ((null))
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd404: Unknown property
   0xd407: Perceived Device Type
   0xd405: Device Icon


and there were pages of extra info after that. Other info, whilst the phone is connected ..

$ **lsusb**

> Bus 002 Device 005: ID 148f:2000 Ralink Technology, Corp. 
Bus 002 Device 004: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
Bus 002 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 002 Device 013: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It was so easy to mount with the old S2 (sigh), but a week ago I collected an egg and put it in a pocket with the S2. Which was fine, but then forgot about it, sat down and reached to take off shoes and then heard a 'crack' noise. ..lol  Was at least able to get all the files off the S2 but it is not stable at the usb cable connect point. Talk about egg on my face ..lol  :D

---

### Post by oygle on 2019-09-07
As the MTP side of things had issues, I decided to give jmtpfs another try. Before that, used the following

sudo **go-mtpfs** */media/myphone 

> 2019/09/08 12:58:09 fatal error LIBUSB_ERROR_IO; closing connection. 
2019/09/08 12:58:09 selectStorages failed: EOF

but still errors. I used the following 3 articles as a combination to try and get the mount going with **jmtpfs** ....

[https://askubuntu.com/questions/854332/how-to-connect-android-7-1-to-ubuntu-linux-with-usb](https://askubuntu.com/questions/854332/how-to-connect-android-7-1-to-ubuntu-linux-with-usb)
[https://askubuntu.com/questions/1000772/how-to-connect-android-samsung-7-0-on-linux-ubuntu-17-10](https://askubuntu.com/questions/1000772/how-to-connect-android-samsung-7-0-on-linux-ubuntu-17-10)
[https://unix.stackexchange.com/questions/389952/how-to-get-the-samsung-galaxy-s5-to-work-with-mtp-on-debian-9](https://unix.stackexchange.com/questions/389952/how-to-get-the-samsung-galaxy-s5-to-work-with-mtp-on-debian-9)

1.  ```
sudo apt install jmtpfs
```

2. Uncomment the "user_allow_other" line

```
SUDO_EDITOR=kate sudoedit /etc/fuse.conf 
```

```
cat */etc/fuse.conf
```

> # /etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE) 

# Set the maximum number of FUSE mounts allowed to non-root users. 
# The default is 1000. 
#mount_max = 1000 

# Allow non-root users to specify the allow_other or allow_root mount options. 
user_allow_other 

3. Get the vendor and product ID's of the phone

```
lsusb
```

> Bus 002 Device 005: ID 148f:2000 Ralink Technology, Corp. *
Bus 002 Device 004: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam 
Bus 002 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse 
Bus 002 Device 013: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In this case, the vendor is 04e8 and the product is 6860

4. If the rules file is empty, copy this one

```
sudo cp /lib/udev/rules.d/69-libmtp.rules /etc/udev/rules.d/69-libmtp.rules
```

5. Then modify (didn't need sudo for some reason)

```
kate /etc/udev/rules.d/69-libmtp.rules 
```

and add in this line ..

> ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", SYMLINK+="libmtp-%k", MODE="660", GROUP="disk", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"

6. Reset

```
sudo udevadm control --reload
```

7. Run** jmtpfs**

```
sudo jmtpfs /media/myphone
```

> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP). 
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface 
LIBMTP libusb: Attempt to reset device

8. Now see if it is mounted  (displaying last entry only)

```
mount
```

> 
jmtpfs on /media/myphone type fuse.jmtpfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0)

Hmm, so it is actually mounted, but now I can't see /media/myphone in Dolphin. No doubt because the user/group on that path is root.

At least that is a start.   :)

---

### Post by oygle on 2019-09-10
Now see if it is mounted (displaying last entry only)

```
mount
```

> jmtpfs on /media/myphone type fuse.jmtpfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0)

So it is actually mounted, but now I can't see /media/myphone in Dolphin. No doubt because the user/group on that path is root.

How do I fix that ?

---

### Post by oygle on 2019-09-12
I can get it to mount with jmtpfs but it seems some sort of permissions problem..

```
jmtpfs /media/myphone
```

> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
LIBMTP ERROR: couldnt parse extension samsung.com/devicestatus:1

```
$ jmtpfs  -l
```
> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
Available devices (busLocation, devNum, productId, vendorId, product, vendor):
1, 13, 0x6860, 0x04e8, Galaxy models (MTP), Samsung

```
$ mount
```

> jmtpfs on /media/myphone type fuse.jmtpfs (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

```
ls -al /media
```
> ls: cannot access '/media/myphone': Input/output error
total 12
drwxr-xr-x   4 root  root  4096 Sep  1 12:06 .
drwxr-xr-x  26 root  root  4096 Sep  4 11:35 ..
lrwxrwxrwx   1 root  root    45 Jun 25  2016 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx   1 root  root    42 Jun 25  2016 .hidden -> /etc/kubuntu-default-settings/hidden-media
d??????????  ? ?     ?        ?            ? myphone
drwxr-xr-x+  2 oygle oygle 4096 Sep  1 12:07 oygle


#unmount
```
fusermount -u  /media/myphone
```  

```
mount
```

No entry found for jmtpfs

```
ls -al /media
```
> total 16
drwxr-xr-x   4 root  root  4096 Sep  1 12:06 .
drwxr-xr-x  26 root  root  4096 Sep  4 11:35 ..
lrwxrwxrwx   1 root  root    45 Jun 25  2016 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx   1 root  root    42 Jun 25  2016 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-xr-x   2 oygle oygle 4096 Sep  1 12:06 myphone
drwxr-xr-x+  2 oygle oygle 4096 Sep  1 12:07 oygle

I don't know what causes the error > LIBMTP ERROR: couldnt parse extension samsung.com/devicestatus:1  , and the path where the phone is being mounted has question marks in it ??

---

### Post by oygle on 2019-09-12
The following works okay, but would prefer _NOT_ to use **sudo**

```
sudo mkdir  /media/myphone
sudo jmtpfs /media/myphone
jmtpfs  -l	#shows device
sudo ls -al /media
mount		#check if mounted
sudo  dolphin	#can access files ok
sudo  bcompare	#can copy/compare files ok
```

---

### Post by oygle on 2019-09-13
This works perfectly for me ..

1. Make some path under HOME. (I had _many_ permissions problems when trying to do this under /media )

```
mkdir ~/myphone
```

2.  Connect the device to the USB cable

3.  Ignore any messages on Ubuntu, but take the "allow" option on the Phone, if it appears

4. Use jmtpfs to mount the mtp device

```
jmtpfs ~/myphone
```

> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
LIBMTP ERROR: couldnt parse extension samsung.com/devicestatus:0

5. Although it gives an error, the device is available

```
jmtpfs -l
```

> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
Available devices (busLocation, devNum, productId, vendorId, product, vendor):
1, 9, 0x6860, 0x04e8, Galaxy models (MTP), Samsung

6. Check with the mount command ...

```
mount
```

> jmtpfs on /home/oygle/myphone type fuse.jmtpfs (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


7. Also the **ls** command

```
ls -al  ~/myphone
```

> total 4
drwxr-xr-x  3 oygle oygle    0 Jan  1  1970 .
drwxr-xr-x 47 oygle oygle 4096 Sep 14 08:50 ..
drwxr-xr-x 15 oygle oygle    0 Apr  4  4460147 Phone


8. It can be accessed via Dolphin,etc

9. Unmount before disconnecting the cable

```
fusermount -u  ~/myphone
```

10. Disconnect the micro usb cable

11. I have no idea if all the various commands to modify files, shown in the tutorial at [https://ubuntuforums.org/showthread.php?t=2226702](https://ubuntuforums.org/showthread.php?t=2226702) was necessary or were used by jmtpfs. Certainly in the early stages of attempting this, those modifications were done, but IMO the tutorial was for "connecting", not mounting.

---

### Post by alphasoup on 2019-12-30
To avoid permission issues under /media this was previously suggested in other posts:
$ YourPhone=LG_H830s
$ sudo mkdir -p /media/$LOGNAME/$YourPhone
$ sudo chown -R $LOGNAME:$LOGNAME /media/$LOGNAME/$YourPhone

Once this is setup, use your mount directory /media/$LOGNAME/$YourPhone
and you do not need to sudo, e.g.
$ jmtpfs -o allow_other /media/$LOGNAME/$YourPhone

Alternative?

$ sudo apt-get install gvfs-fuse

$ sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9

However if the device is properly present (or added) in /lib/udev/rules.d
file: 69-libmtp.rules
;; Example line:
# LG Electronics Inc. Android phone (ID2)
ATTR{idVendor}=="1004", ATTR{idProduct}=="61f9", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"

Then jmtpfs should not be needed and the device mount automatically when connected to usb:
$ mount | tail -1
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

---

### Post by oygle on 2020-04-05
Thanks for your reply. As I have just jumped to 19.10, I tried the methods I used in the previous post, however ran into problems. So I have used your suggestions ..

> **alphasoup said:**
> To avoid permission issues under /media this was previously suggested in other posts:
$ YourPhone=LG_H830s
$ sudo mkdir -p /media/$LOGNAME/$YourPhone
$ sudo chown -R $LOGNAME:$LOGNAME /media/$LOGNAME/$YourPhone

Once this is setup, use your mount directory /media/$LOGNAME/$YourPhone
and you do not need to sudo, e.g.
$ jmtpfs -o allow_other /media/$LOGNAME/$YourPhone

I can now do an **ls** , but the **mount** failed. Here is what I used ..

> 
sudo mkdir -p /media/oygle/myphone 

sudo chown -R oygle:oygle /media/oygle/myphone

jmtpfs -o allow_other /media/oygle/myphone
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
fusermount: option allow_other only allowed if 'user_allow_other' is set in /etc/fuse.conf

 jmtpfs -l
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
Available devices (busLocation, devNum, productId, vendorId, product, vendor):
2, 3, 0x6860, 0x04e8, Galaxy models (MTP), Samsung

---

### Post by oygle on 2020-04-05
So, this fixed it ..

```
jmtpfs  /media/oygle/myphone
```

check ...

```
mount
```

> jmtpfs on /media/oygle/myphone type fuse.jmtpfs (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

So, in full, this is what I needed

```
sudo mkdir -p /media/oygle/myphone
sudo chown -R oygle:oygle /media/oygle/myphone
jmtpfs  /media/oygle/myphone
```

---

### Post by oygle on 2020-04-10
This was working, tried to use **jmtpfs** today and got this message

> Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
error returned by libusb_claim_interface() = -6LIBMTP PANIC: Unable to initialize device
terminate called after throwing an instance of 'MtpErrorCantOpenDevice'
  what():  Can't open device
Aborted (core dumped)

---

