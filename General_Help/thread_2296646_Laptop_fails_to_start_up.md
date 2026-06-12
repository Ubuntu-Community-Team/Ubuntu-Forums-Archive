---
title: "Laptop fails to start up"
date: 2015-09-27
forum: General Help
---

### Post by tommyss4l on 2015-09-27
I got an acer aspire e11 recently and after a while I got things working, until last night. It's always had a problem shutting down correctly, but once the boot splash came up I just forced it down and when I'd turn it on again, it would be fine. This morning I turn it on and it brings me to a how would you like to start up today page. My options are normally, advanced options, and recovery mode. I tried normally but that didn't work so I tried recovery. After a whole bunch of code flashed across the screen it brings me to a pink screen with some options. The first of which is continue normally, followed by clean, dpkg, failsafe, and a few others. I ran the dpkg and the grub options. The grub update seemed to be fine but the dpkg check was aborted due to Internet issues. I'm not sure if the wifi is on yet at this stage so that might explain that, but then why would the grub update not fail in the same way? 
So after running those two I selected start normally and it brought me to the login screen (Yay!). I logged in and it showed my desktop but the unity bar was missing as well as the top bar. I went through this 3-5 times with no success, each time ending in the same result. Even letting it sit there open has resulted in no change. 

Please if anyone has any ideas I'd love to hear them. I've tried a few different fixes and nothing has worked as yet. 

Thanks

---

### Post by tgalati4 on 2015-09-27
Run the *fsck* in the Advanced-->Recovery menu.  Keep a notepad handy.  Write down what actions that are taking place.  Hook up your ethernet cable in case you need to install any packages.

---

### Post by grahammechanical on 2015-09-27
Just a couple of points.

The reason that the Grub option did not have the same problem as the dpkg option is that the Grub option does not need to access the internet. The script that runs when we select the Grub option in turn runs 2 Grub utilities that get information from what is on the hard disk.

Whereas, the dpgk option does need to access the the Ubuntu servers/repositories. That recovery menu option will run a few commands such as apt-get update; apt-get install -f & apt-get dist-upgrade.

Now as to your problem which seems to be that you can get past the login screen and to a desktop but without the Unity launcher & top panel. Try right clicking the wallpaper and selecting Change Desktop Background. That will open System Settings at the Appearance page. But from their you can get to the System settings main window and from there you can open Software & Updates. In the Additional drivers tab you will get a choice of video drivers if you are connected to the internet and allow time for the utility to find drivers suitable for your machine. Experiment.

For those who are interested. It is possible to have a Wifi connection in recovery mode. If we have previously set up a wireless connection then the Network option of the recovery menu will make the WiFi connection to the router. 

Regards.

---

### Post by tommyss4l on 2015-09-27
Thank you both for all your help, sorry for the delay, I was working. 

Tgalati4: I ran the fsck and the only error that came up read "error getting authority: error initializing authority: could not connect: no such file or directory (g-io-error-quark, 1)

Ghrammechanical: I was able to get to the settings as you said. The only option there was switching to" using processor microcode firmware for Intel CPU's from Intel-microcode (proprietary). 

I have done the above and the only changes are I skip the first step I took where I can get to recovery mode in the first place. 

Thank you for your continued help

---

### Post by Bucky Ball on 2015-09-28
I'd open a terminal and do a complete update/upgrade if for no other reason than to know you're completely up to date and some redundant piece of software is not causing the issue:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Post any and all errors. This will not upgrade your currently installed OS to a newer version. :)

---

### Post by tommyss4l on 2015-09-28
Ran those four lines, no errors and no change

---

### Post by tgalati4 on 2015-09-28
Boot into Recovery Root terminal and post the output of:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

You might have a failing disk.

---

### Post by mörgæs on 2015-09-29
Are you able to start up and shut down normally using 15.10 (beta) in a live boot?

---

### Post by tommyss4l on 2015-09-29
"smartctl open device: dev/sda failed: no such device"

---

### Post by tommyss4l on 2015-09-29
Ok, so new update. I solved the no unity bar and top bar issue. I believe it was a profile issue because I've created a new profile and everything works. Unfortunately the laptop still will not shut down properly. I am currently working on getting 15.04 working through unetbootin so I can attempt morgaes' solution.

---

### Post by tgalati4 on 2015-09-29
Did you type the command correctly?  The disk drive is called /dev/sda not dev/sda.

---

### Post by tommyss4l on 2015-09-29
That is how I put it in, I ran it again just to make sure and no good. 

Also my version of unetbootin must not be working, I've tried to install 3 different downloads of 15.04 with no avail.

---

### Post by mörgæs on 2015-09-30
If you are considering a reinstall I would suggest 15.10 for comparison.

---

### Post by tommyss4l on 2015-09-30
I'm thinking that is my only discourse. Could you recommend another iso installer other than unetbootin?

---

### Post by mörgæs on 2015-09-30
There is a long discussion here:
[http://ubuntuforums.org/showthread.php?t=2289225](http://ubuntuforums.org/showthread.php?t=2289225)

If it has a CD/DVD drive you could also use this for installing.

---

