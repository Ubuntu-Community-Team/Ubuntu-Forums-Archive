---
title: "Help making adb recognize a generic android tablet"
date: 2013-05-16
forum: General Help
---

### Post by hg088 on 2013-05-16
I'm trying to root a generic tablet (titan pc008) using ADB.

The thing is when i connect the tablet and run adb devices it doesn't get listed.

So i guess i need to install some sort of generic driver or something but i've very superficial knowledge about rooting and android tinkering in general.

I've already tried killing and restarting the adb server

The lsusb output for my device:
```
Bus 002 Device 004: ID 2207:0000
```

Added this line to the file "/etc/udev/rules.d/99-android.rules":
```
SUBSYSTEM=="usb", ATTR{idVendor}=="2207", ATTR{idProduct}=="0000", MODE="0666", OWNER="user"
```

---

### Post by mr_mop on 2013-05-16
I think it's just your filename is wrong.

Try renaming it 51-android.rules

Also make sure you've got to do a chmod a+r which means "add read permissions to all users" on that file

[http://developer.android.com/tools/device.html](http://developer.android.com/tools/device.html)

---

### Post by hg088 on 2013-05-17
Thanks mr_mop but that didn't do the trick. After reading that info I'm assuming that there's no need to install drivers, just set the udev rule correctly. Any other ideas in that regard?

---

### Post by lemonoid on 2013-05-17
as far as a generic android tablet what do you mean by generic? on google's android developer's site, look for using hardware devices and you will find  the list of all the supported device types (brands/OEMs) for adb. I'm sure if yours isn't listed, it can be found, but what you need to do is just copy and paste the ENTIRE list that Google has in /etc/udev/rules.d/51-android.rules (assuming that you have the SDK & platform-tools installed which contain adb). after that, in the terminal type the command:  sudo restart udev   then go to /etc/environment and add the path (with a text editor, ie terminal command: sudo gedit etc/environment)to the SDK's platform tools to your environment, at the end of what is already in your environment path you add the path to the SDK's platform-tools, (example) :/home/yourusername/android/android-sdk-linux/platform-tools and save the file. the colon is imperative, because it separates what is in your path from what you are adding to your path. after this, it would be wise to restart your computer, make sure Android Debugging is turned on in your tablet's application or development settings (it depends what version of Android you're running). then hook up your tablet, in the terminal type: adb devices    ..this should start the adb daemon and find your device. if it does not return a device ID, then it's still not finding your device. This means you've either done something wrong (so go back and check everything for errors), Google hasn't yet added the ID to the ADB rules for your device, or it could simply be the cable you are using. I develop for Android and I've set up adb on windows and ubuntu both many times, after a while you get the hang of it, it just becomes easy. But many times it is as simple as the cable as I said, I've used adb on HTC, Motorola, LG, Samsung, ASUS, some random tablet I don't even remember the brand (so they should have the device ID for yours), and several others, and many times, you need that device's specific cable to communicate through the Android Debugging Bridge, and sometimes, you need any cable besides the one that came with it lol. ADB is funny and can act up if everything isn't perfect. So if you're positive you've done everything right, try various cables. just make sure each time you try a different cable you kill adb before trying again ( command: adb kill-server). But your best bet is to just copy ALL of the device ID's that Google has from A to Z even if you plan on never using those devices, because its possible that one of those will work for yours, and it doesn't matter which, as long as one does. PM me if you need any help with setting anything Android up on Ubuntu......also if you do go back and edit your 51-android.rules file, make sure to obviously save it, but sudo chmod a+r it again, then restart udev again.

---

### Post by lemonoid on 2013-05-17
ok, I saw that you did put the type of your tablet, sorry, didn't see it on first read. I just remembered, the brand of generic tablet I rooted was a CVS tablet, which is def not supported by google So I'm sure if one of their device ID's worked on it ( a year and a half ago), then there is one in that long list that will work for yours, so just put the whole list in the rules file. i'll check back in the morning if i can and see if u got it going.

---

### Post by hg088 on 2013-05-17
Hi lemonoid thanks for answering.

I tried adding the google list to the udev file and also making it readable for everyone but that didn't work.

Luckily i found the answer here: [http://stackoverflow.com/questions/12111005/how-to-register-this-tablet-to-ubuntu-udev-list](http://stackoverflow.com/questions/12111005/how-to-register-this-tablet-to-ubuntu-udev-list) by Mateus Sousa Mello. That got my device recognized.

Thanks again btw.

---

