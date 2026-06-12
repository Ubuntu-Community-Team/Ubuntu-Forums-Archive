---
title: "About install .apk file"
date: 2017-09-22
forum: General Help
---

### Post by satimis on 2017-09-22
Hi all,

About installing .apk file on SD card I found following link;

[https://stackoverflow.com/questions/7076240/install-an-apk-file-from-command-prompt](https://stackoverflow.com/questions/7076240/install-an-apk-file-from-command-prompt)

My understanding is the .apk file on the SD card

Steps to be performed:

1) 
$ sudo apt install adb

2) Insert SD card on USB port

3) 
$ lsblk```

NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 953.9G  0 disk 
&#9500;&#9472;sda1                  8:1    0   922G  0 part /
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9492;&#9472;sda5                  8:5    0  31.9G  0 part [SWAP]
sdb                     8:16   0 119.2G  0 disk 
&#9500;&#9472;sdb1                  8:17   0   487M  0 part /media/satimis/newlabel
&#9500;&#9472;sdb2                  8:18   0     1K  0 part 
&#9492;&#9472;sdb5                  8:21   0 118.8G  0 part 
  &#9500;&#9472;ubuntu--vg-root   252:0    0  86.9G  0 lvm  
  &#9492;&#9472;ubuntu--vg-swap_1 252:1    0  31.9G  0 lvm  
sdc                     8:32   0   1.4T  0 disk /media/satimis/datapartition
sdd                     8:48   1  59.5G  0 disk 
&#9492;&#9472;sdd1                  8:49   1  59.5G  0 part /media/satimis/D722-6ACB

```

SD card is automatically mounted.  sdd is SD card.

4)
$ sudo adb install /media/satimis/D722-6ACB/.apk

Please advise.  Thanks

This is my first time to install .apk file

Regards
satimis

---

### Post by TheFu on 2017-09-23
Copy the file to your Android device. Use the Android package manager to install it.

APK files don't work on desktop linux.

If you intend to install a file into android using the android debugger, then perhaps if you specify the exact name of the file (which isn't .apk), then it will work?

Might be easier to make a connection to the android device with adb first, then use the install command separately?

Also, I don't think you need/should use sudo with adb.

---

### Post by satimis on 2017-09-23
> **TheFu said:**
> Copy the file to your Android device. Use the Android package manager to install it.

APK files don't work on desktop linux.

If you intend to install a file into android using the android debugger, then perhaps if you specify the exact name of the file (which isn't .apk), then it will work?

Might be easier to make a connection to the android device with adb first, then use the install command separately?

Also, I don't think you need/should use sudo with adb.
Hi,

Thanks for your advice.

I'm testing Viewtouch
[http://viewtouch.com/](http://viewtouch.com/)

The apk file ViewTouch-1.11.40.apk is download here;
[http://viewtouch.com/download.html](http://viewtouch.com/download.html)

If I'm understand your advice correctly I must build a Rasberrry Pi running either Android or Chrome for installing the apk file?


I'm prepared download Flint OS here for running it on Raspberry Pi
Flint OS for RPi
[https://flintos.io/download/](https://flintos.io/download/)

Flint is a Chromium OS
Raspberry Pi Flint OS: Powered By Chromium OS
[https://pimylifeup.com/raspberry-pi-flint-os/](https://pimylifeup.com/raspberry-pi-flint-os/)


On googling I found following interesting threads;
1)
How to run Android emulator on Ubuntu or Debian
[http://xmodulo.com/how-to-run-android-emulator-on-ubuntu-or-debian.html](http://xmodulo.com/how-to-run-android-emulator-on-ubuntu-or-debian.html)

2)
How to Install Android Apps on Ubuntu using ARChon (Updated)
[http://www.omgubuntu.co.uk/2014/09/install-android-apps-ubuntu-archon](http://www.omgubuntu.co.uk/2014/09/install-android-apps-ubuntu-archon)


A further question can I install and run Chromium OS on VM of Oralce VirtualBox?

I tested Android on VM before.  I can install it on VM of VirtualBox but it didn't run well there.  I have asked VirtualBox Forum for assistance.  The moderator replied me that VirtualBox doesn't support Android.

Thanks

Regards
satimis

---

### Post by TheFu on 2017-09-24
I've never tried virtualbox with Android and haven't used virtualbox in about 5 yrs.

APK files are packages for Android.  I don't think they "install" on any other OS.
Some APK files will have binary libraries and programs, not java.  That means they are tied to the specific CPU, which for almost all Android devices is some level of ARM CPU, not Intel.  This is common with games, so trying to run a high-graphic Android game under an Intel CPU emulator just doesn't work. Wrong CPU.

Where I live, a cheap Android device is $30.

Really this isn't the best place to ask Android questions. Android isn't Ubuntu. There are lots and lots of android developer forums.

---

### Post by satimis on 2017-09-24
> **TheFu said:**
> I've never tried virtualbox with Android and haven't used virtualbox in about 5 yrs.

APK files are packages for Android.  I don't think they "install" on any other OS.
Some APK files will have binary libraries and programs, not java.  That means they are tied to the specific CPU, which for almost all Android devices is some level of ARM CPU, not Intel.  This is common with games, so trying to run a high-graphic Android game under an Intel CPU emulator just doesn't work. Wrong CPU.

Where I live, a cheap Android device is $30.

Really this isn't the best place to ask Android questions. Android isn't Ubuntu. There are lots and lots of android developer forums.
Hi,

Thanks for your advice.

Flint OS has packages for:
1) Flint OS for RPi v0.3
2) Flint OS for PC v1.0
3) Flint OS for TKB v1.0 (I suppose TKB board is Android device)
4) Flint OS VM for VMWare v0.1
[https://flintos.io/download/](https://flintos.io/download/)

I have Raspberry Pi3 B here for testing Flint5 OS and Android.  Just for curiosity to check whether it runs on VM of Virtualbox.

I have download all of them.  I don't have VMWare here.  I'll check whether it will run on VirturalBox.

Also I found FlintOS forum;
FlintOS Forum
[https://www.reddit.com/r/FlintOS/](https://www.reddit.com/r/FlintOS/)

Thanks

Regards
satimis

---

### Post by nicholasbrown on 2018-03-07
Actually, there are easier ways aside from this. And upon searching, I came across an article discussing [how to install apk on Android easily]("https://airmore.com/install-apk-files-on-android.html"). I followed the guide and works pretty well for me. :) You can try it for yourself.

---

### Post by TheFu on 2018-03-08
> **nicholasbrown said:**
> Actually, there are easier ways aside from this. And upon searching, I came across an article discussing [how to install apk on Android easily]("https://airmore.com/install-apk-files-on-android.html"). I followed the guide and works pretty well for me. :) You can try it for yourself.

I assumed that the OP wanted to install APKs into Ubuntu.

Yes, installing an APK into Android is trivial.  Just allow side-loading in the security options and open the APK. That will install it on Android. 

On Ubuntu ... well, that is a very different thing entirely. A chromeOS-like environment is needed.  There seem to be a few different methods:
* Shashlik
* Anbox
* Converting an APK into a Chrome-browser addon - [https://www.addictivetips.com/ubuntu-linux-tips/run-android-apps-on-linux/](https://www.addictivetips.com/ubuntu-linux-tips/run-android-apps-on-linux/)

I've not tried any, though I did run Android-x86 in a virtual machine a few years ago.  It was painfully slow.  Things are looking better these days. I installed Anbox.... it embeds deep into the host OS - kernel module needed.  It uses snaps too. And it crashed when I tried to launch it.  The install also broke X11 select/paste operations.  Boooo.

---

### Post by satimis on 2018-03-08
Hi all,

The SD card contains the OS for running Raspberry pi.  Installing new software should be vi a computer.  I expect to install a .apk package on the SD

Thanks

Regards
satimis

---

