---
title: "Unable to see Samsung Ace 2 18160"
date: 2015-07-25
forum: General Help
---

### Post by Robbyx on 2015-07-25
My installation of a alternative ROM on the phone  has failed due to a bug. I need to put another zip file onto the ext micro  SD HC drive  in the phone but the android system will no longer load. I have tried a to reinstall my backup but it says there is a md5sum error, and fails. 

lsub shows
Bus 002 Device 009: ID 04e8:685d Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (Download mode)

The android phone  is not showing in nautilus or PCmanfm even though via lsub it is recognised.

I have tried sudo dmesg | grep -i “SCSI device”
grep: device”: No such file or directory

The idea was  to see where it might be found for mounting purposes. 

Is there a way to mount it manually? I am using 14.04, AMD 64.

I have put the sd card into a card reader and it was not recognised at all, this makes me assume the card reader is faulty, because a few hours ago the card worked ok in the phone. 

Any ideas? At the moment I can only get into recovery mode in the phone (but I have nothing to use for the recovery)

---

### Post by mystics on 2015-07-25
Do you already have adb installed? That can help you copy the file onto your phone.

If you don't already have it, then you can get it by running:

```

sudo add-apt-repository ppa:phablet-team/tools
sudo apt-get update
sudo apt-get install android-tools-adb

```

After that, boot your phone into recovery mode and run from your computer:

```

adb push */path/to/local/file* */path/on/phone* 

```

Hope this helps.

---

### Post by Robbyx on 2015-07-25
Thank you. I hope it will help a lot. At the moment, I can not see the android device in the file manager. I have  added the device details into

/etc/udev/rules.d/51-android.rules (as the root user) as per lsub quoted above. 

I  have also added in /home/robins/.android/adb_usb.ini and added the vendor Id as per instructions found. 

So my problem is how to discover the path to the phone.

---

### Post by mystics on 2015-07-25
Sorry if this is not related to what you're trying to do, but adb will  automatically send it to the connected device so long as it appears when  you type in:

```

adb devices

```

It also has to be the only connected device for it to automatically send it to that one.

You can also navigate the file system to see where you want to send the zip file using

```

adb shell

```

That should allow you to navigate the device from the terminal. Alternatively, you might be able to navigate it all from recovery mode.

---

### Post by Robbyx on 2015-07-25
Sorry to ask further. I appreciate your help so far. Do you have an answer for the "??? and no permissions shown" below?

robins@robins-desktop:~$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ sudo adb devices
[sudo] password for robins: 
List of devices attached 
????????????	no permissions

I have found some solutions that do not work for me: [http://askubuntu.com/questions/213874/how-to-configure-adb-access-for-android-devices](http://askubuntu.com/questions/213874/how-to-configure-adb-access-for-android-devices)

I have tried everything from "*I tried adding the udev rules for my phone, but it didn't help so I thought maybe I wasn't clear about my problem.* "

"> robins@robins-desktop:~$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ sudo adb devices
[sudo] password for robins: 
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ adb devices
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ sudo udevadm control --reload
robins@robins-desktop:~$ adb devices
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ sudo adb devices
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ adb kill-server
robins@robins-desktop:~$ adb start-server
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
robins@robins-desktop:~$ sudo adb devices
List of devices attached 
????????????	no permissions

robins@robins-desktop:~$ sudo tools/android update sdk --no-ui
sudo: tools/android: command not found
robins@robins-desktop:~$ 


The last surprised me and I am wondering if I have put the correct device description as from the lsusb quoted above  into adb_usb.ini

 ~/.android/adb_usb.ini
# ANDROID 3RD PARTY USB VENDOR ID LIST -- DO NOT EDIT.
# USE 'android update adb' TO GENERATE.
# 1 USB VENDOR ID PER LINE.
# ie 0x2207
0x<04e8>

---

### Post by Robbyx on 2015-07-25
I have made some changes to file names. In some places people quoted the rules files with - instead of dots.

Now it is not showing an error message but also showing no devices instead a blank line as below:

> robins@robins-desktop:~$ adb devices
List of devices attached 

robins@robins-desktop:~$ sudo tools/android update sdk --no-ui
sudo: tools/android: command not found
robins@robins-desktop:~$ 


I have rebooted both machines.

---

### Post by mystics on 2015-07-25
Glad you were able to get around permissions issue. I was going to advise starting the server as sudo (which is different than running sudo devices after the server has already been started), but I guess that won't be necessary now.

But as for devices not showing, when you run the command, where are you? You said you were only able to get into recovery. Are you in recovery when you run the command or are you at the bootloader? adb doesn't work while at the bootloader, so you'll need to be in recovery for any of the commands to work.

---

### Post by Robbyx on 2015-07-26
I have made great progress and  now the device is being found. I misunderstood some of the id labels that should have been put into 51.rules for example instead of entering  ATTR{ID_MODEL_ID}=="685d" I thought the id model was the number and so left off a second id.  

Thank you very much for the time and effort you put into helping me. I am now going to the next stage of pushing out the corrected zip file.

---

### Post by Robbyx on 2015-07-26
For others following on with similar problems, such as unable to access an android phone  connected by usb, you may also wish to refer to [http://ubuntuforums.org/showthread.php?t=1918512](http://ubuntuforums.org/showthread.php?t=1918512). Although detailed I have found it to be very helpful.

---

