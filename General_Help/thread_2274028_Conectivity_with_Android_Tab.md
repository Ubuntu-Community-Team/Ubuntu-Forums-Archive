---
title: "Conectivity with Android Tab"
date: 2015-04-17
forum: General Help
---

### Post by 3dmatrix on 2015-04-17
I have two computers (say **A** and **B**)
Both of them run on Ubuntu 14.04
When I connect my android Tab to** A** it gets recognized for file transfer but when I connect it to **B** it does not gets recognized.
Whereas if I connect my friend's android tab to computer **B** it gets recognized.
Can any one tell me, how can I find out what is missing in the two installs because of which the two computers are behaving differently.

---

### Post by ajgreeny on 2015-04-17
STEP 1
```
sudo apt-get update
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
sudo apt-get dist-upgrade

```
STEP 2
```
sudo nano /etc/fuse.conf
```
Remove the # from the below line of code for user_allow_other, like so in /etc/fuse.conf...
```
#/etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)

#Set the maximum number of FUSE mounts allowed to non-root users.
#The default is 1000.
#mount_max = 1000

# Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```
STEP 3
With tablet attached by USB run```
lsusb
```
This should bring up an output similar to the following so look for the tablet line by maker or other known name.
```
Bus 002 Device 003: ID [COLOR=#ff0000]0fce[/COLOR]:[COLOR=#ff0000]01b1[/COLOR] Sony Ericsson Mobile Communications AB    #This is an android tablet; note text in red.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
etc
etc
```
STEP 4
```
sudo nano /lib/udev/rules.d/69-mtp.rules
```
Add the below lines of code with red text transferred from above
```
# Sony Xperia Z2 Tablet
ATTR{idVendor}=="[COLOR=#ff0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#ff0000]01b1[/COLOR]", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```
STEP 5
```
sudo nano /etc/udev/rules.d/51-android.rules
```
Add the following line of code
```
ATTR{idVendor}=="[COLOR=#ff0000]0fce[/COLOR]", ATTR{idProduct}=="[COLOR=#ff0000]01b1[/COLOR]", MODE=”0666"
```
STEP 6
```
sudo service udev restart
```
Reboot

You should now be able to plug your Android device in and drag/drop data to/from your Android device folders using MTP.

---

### Post by 3dmatrix on 2015-06-03
Thanks for the reply. It works with individual devices. But what I asked was slightly different.
The two OS in both the computers are exactly the same. Still the devices are not recognized in one of them.
What could be the reason ? If we can find the difference between the two computer's OS, then it seems the problem can be permanently solved.
Or can it be because of difference in the two computer's hardware ?

---

