---
title: "Reverting to 16.04"
date: 2018-11-26
forum: General Help
---

### Post by aneblanc on 2018-11-26
After an offer of an upgrade from 16.04 to 18.04 on a pop up window I have just upgraded to 18.04. I have tried it for a couple of days and I would like to go back to 16.04.
I am planning to do a fresh install of 16.04. 
Is it possible to do a fresh install from within Ubuntu or do I need to use a flash drive? 
I have saved all the contents of the desktop and the home folders.Is there anything else I need to save or do before I start the new installation?
Thank you

---

### Post by oldfred on 2018-11-26
You need to use flash drive.
Do you have separate /home?

Generally apps will update to a newer version's data & configuration files. Some may not like going back to older versions.

You may want to export list of installed apps, to make it easy to re-install all of them.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

---

### Post by aneblanc on 2018-11-26
I am not completely sure what you mean with separate /home. I suppose yes.
Thanks for the code to save the list of apps.

---

### Post by oldfred on 2018-11-26
Separate /home is having two ext4 partitions one for system and one for data(/home).
Makes backup slightly easier and new or total reinstall easier. As you include /home without formatting, but format / (root) and install to it. Then old /home partition is used in new install.

---

### Post by missmoondog on 2018-11-27
may i ask why you want to revert back to 16.04? did stuff happen during the upgrade that doesn't work right? that happens 99% of the time when doing an upgrade like that and i don't know why it's even allowed!

the differences in 18.04 and 16.04 aren't terribly big but after a foobarred in line upgrade, 18.04 will suck! i actually tried it on 2 machines, although i knew better, and it didn't take but 5 minutes to say screw that and did a clean install. much happier! :)

---

### Post by aneblanc on 2018-11-27
I am glad someone is asking!
The desktop is gone, I'd like to have it back.
The tray at the top used to have icons of applications loaded at start, they are not there, though they are loaded.
The touch pad areas are different. I cannot click anymore where I was used to click.
Alt Tab used to allow me to switch between several browser windows or PDF windows, not anymore with 18.04
I used to open the launcher in the corner, I can't do it anymore.
No more several time zone clocks in the calendar. It was a practical feature to call friends and family in different countries.
To switch off the computer I used to press the start button and nothing else.
Files doesn't work smoothly anymore.
And a few more minor annoyances...
Would you know how long Ubuntu will support 16.04? I heard of 5 or 10 years. 10 would be better.
I regret not inquiring about the differences between 16 and 18 before upgrading.

---

### Post by CatKiller on 2018-11-27
It sounds like it's Unity that you miss the most. It's been discontinued, but you may well still be able to install it. It is no longer the default, that's all.

16.04 is supported until April 2021.

[This page](https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux) was my first result for "Unity in 18.04."

---

### Post by oldfred on 2018-11-27
This is really for server installs as they want stability for longer term. Desktop users usually want newer applications which normally are not updated. 
 18.04  LTS support increased to 10 years 
[https://ubuntuforums.org/showthread.php?t=2406087](https://ubuntuforums.org/showthread.php?t=2406087)

When Ubuntu switched to Unity, I started to use flashback/fallback/gnome-panel, name has changed over time. But it is the old Ubuntu panel system, I believe similar to Mint which kept old panel system. It is not really mentioned unless you know it is available. While it has changed a bit, it is not much different than original Ubuntu before Unity. My monitor is the old 4:3 so having panels at top & bottom makes more sense for me. Having menus on side takes away too much width.

---

### Post by aneblanc on 2018-11-28
I installed unity with the commands "sudo apt update" and  "sudo apt install ubuntu-unity-desktop". 
I don't get the screen described on [https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux) right after this command and rebooting does not bring any change.

---

### Post by deadflowr on 2018-11-28
When you log in do you get this (ish) screen:
[ATTACH=CONFIG]281790[/ATTACH]
or a screen with similar look?

---

### Post by aneblanc on 2018-11-28
> **deadflowr said:**
> When you log in do you get this (ish) screen:
[ATTACH=CONFIG]281790[/ATTACH]
or a screen with similar look?

No I don't.

---

### Post by deadflowr on 2018-11-28
And it's not the login screen like the one from your link here:
[https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux#h6-2-switch-to-unity-desktop-environment]("https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux#h6-2-switch-to-unity-desktop-environment")
?

---

### Post by aneblanc on 2018-11-28
No, sorry to disappoint. This one was the one when I ran 16.04.

---

### Post by CatKiller on 2018-11-28
> **aneblanc said:**
> I installed unity with the commands "sudo apt update" and  "sudo apt install ubuntu-unity-desktop". 
I don't get the screen described on [https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux) right after this command and rebooting does not bring any change.

When you've installed a new desktop environment you should have a widget on the login screen next to your name to say which desktop you want to launch.

---

### Post by aneblanc on 2018-11-28
> **oldfred said:**
> You need to use flash drive.
Do you have separate /home?

Generally apps will update to a newer version's data & configuration files. Some may not like going back to older versions.

You may want to export list of installed apps, to make it easy to re-install all of them.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

Thank you for all the codes, I have done the deed and reverted to 16.04. Pleased to be back and not to have to spend more time learning new ropes. Apparently I am good until at least 2021.

---

