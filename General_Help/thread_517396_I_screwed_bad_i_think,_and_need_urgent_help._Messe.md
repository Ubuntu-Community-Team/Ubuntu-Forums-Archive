---
title: "I screwed bad i think, and need urgent help. Messed up splash page"
date: 2007-08-04
forum: General Help
---

### Post by Masta Frankis on 2007-08-04
Hey everyone, heres my story.

I was messing around with the splash .png's (in /usr/share/pixmaps/splash) and what I did was, I downloaded a new picture. And i didn't research on how to install it correctly, so i just renamed the old splash.png to something like splashold.png, and then renamed the new picture to match the old one. I was thinkin when Ubuntu loads, it would still have the same settings, so when it looked up the picture, it would just bring up the new one since it had the old name. idk if that makes sense, but yea. 

So now my computer loads up fine, i get the ubuntu loading page. And after that, when the login page is supposed to come, the screen is all black, and I just see the mouse with the hourglass, as if its busy or working. but it doesnt get anywhere, just stays on that screen. 

My system specs are

Compaq Presario
Nvidia GeForce 6600 (drivers were installed correctly, I was running Beryl with it's desktop effects and a GTK 2.x theme with no problem)
1GB DDR2 RAM
Intel Pentium D(ual) 3.2Ghz Processors
160GB Hard Drive

Any assistance is greatly appreciated. Once I get my hands wrapped our linux a bit more, I'll be sure to contribute back. Thanks.

---

### Post by Masta Frankis on 2007-08-04
Also, I have Debian as a dual boot option available on that comp (which is what I'm running now). When I bring up the file browser, I see the ubuntu partition as another drive. So I tried to access it from Debian and fix the error, But it wont let me access it. It says 

> Unable to mount the seleceted volume.

libhal-storage.c 1401 : info: called libhal_free_dbus_error but dbuserror was not set.

process 5836: applications must not close shared connections - see dbus_connection_close() docs. this is a bug in the application.

error: device /dev/hdc3 is not removable

error: could not execute pmount 

Thanks again

---

### Post by eggdeng on 2007-08-04
Boot ubuntu in recovery mode. When you get to a prompt, type ```
cd /usr/share/pixmaps/splash 
```to change to the directory where the splash image files are located. Type ```
ls
``` to list the files in that directory. You should see both the new and the old image files. Change the name of your new image file ```
mv ./new_file.png ./some_name.png
``` and then rename the old image file back to its original name ```
mv ./old_file.png ./original_name.png
``` Reboot. Nothing wrong with what you did, probably just that the new image file was the wrong size or filetype?

---

### Post by Masta Frankis on 2007-08-04
Thanks. I tried it, and renamed the files to the original names. But I still can't get to log in screen. Now I have no clue what the problem could be. Like I get the ubuntu loading page. It shows the bar that loads it all the way. then just goes to a black screen with nothing but the mouse and the hourglass. :confused:

---

### Post by Masta Frankis on 2007-08-04
I really hate to bump, and I'm not sure if it's against the rules. It probably is. But I really need assistance. I really need the computer tonight, and Debian isn't gonna cut it for me. All my apps and settings are on Ubuntu, and well I'm basically computer-less. Please any tips are appreciated. Thanks alot

---

### Post by eggdeng on 2007-08-05
Sorry for taking so long to get back, we're in different time zones. If you still haven't managed to get it sorted, you may have to reinstall gnome. ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Masta Frankis on 2007-08-06
hey thanks for the reply. I tried it, but it still didn't solve my problem. Any ideas?

---

### Post by Masta Frankis on 2007-08-06
bump

---

### Post by tlacuache on 2007-08-07
If reinstalling ubuntu-desktop didn't fix your problem, if it were me I'd probably boot into recovery mode (or knoppix), back up my home directory to an external hard drive, and reinstall ubuntu from scratch.

But that's probably not what you want to hear.

---

### Post by Masta Frankis on 2007-08-07
Yea, i thought it would have to come to that. Ill go ahead and do it. But any ideas as to why that happened? Thanks

---

