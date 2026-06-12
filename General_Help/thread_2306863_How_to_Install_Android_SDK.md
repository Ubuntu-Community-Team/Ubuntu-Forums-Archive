---
title: "How to Install Android SDK"
date: 2015-12-19
forum: General Help
---

### Post by Darth4212 on 2015-12-19
I am currently running Ubuntu 15.10 and would like to install the  Android SDK how do I install it please list all of the commands and everything.

---

### Post by ian-weisser on 2015-12-19
Okay, here you are: [https://help.ubuntu.com/community/AndroidSDK]("https://help.ubuntu.com/community/AndroidSDK")

If we missed anything, please update the instructions.

---

### Post by grahammechanical on 2015-12-19
You might be interested in the Ubuntu Make project
> 
[h=3]Installing Ubuntu Make[/h] If you are on latest development Ubuntu version, first, add the Ubuntu Make ppa: 

 $ sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
 $ sudo apt-get updateThen, installing Ubuntu Make: 

 $ sudo apt-get install ubuntu-make 
[h=3]How to install android-studio[/h]  $ umake androidAnd  then, accept the installation path and Google license. _It will  download, install all requirements alongside Android Studio and latest  android SDK _itself, then configure and fit it into the system like by  adding an Unity launcher icon&#8230; 

And  that's it! Happy Android application hacking on Ubuntu. You will find  the familiar experience with the android emulator and sdk manager +  auto-updater to always be on the latest. 



[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

ubuntu-make is being developed as a means of installing development IDEs for various platforms & not just Android. It also aims to keep these IDEs & SDKs up to date for us.

Regards.

---

### Post by Darth4212 on 2015-12-22
Thanks everyone for the help this issue is now resolved!

---

