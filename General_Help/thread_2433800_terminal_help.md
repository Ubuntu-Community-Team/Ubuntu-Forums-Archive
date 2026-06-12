---
title: "terminal help"
date: 2019-12-25
forum: General Help
---

### Post by sviginak on 2019-12-25
I have used ubuntu for several years. A year ago I messed something up by trying something from ubuntu facebook and I couldn't boot. Someone suggested Lubuntu, so using terminal I installed Lubuntu and have booted with Lubuntu icon coming up, but I still go to Ubuntu 16.04 since. I upgraded  to 18.04.3 yesterday, hoping the Lubuntu issue would be resolved and of course it wasn't. At the sign in it recognizes my password but goes right back to user list/password. I can sign in if I choose Lubuntu or unity but not Ubuntu. Usinf terminal, I would like to get rid of Lubuntu and get back to booting to Ubuntu. Any suggestions. I have a Gazpro6 system 76 but haven't gotten any response there, but I hope to get some advice here. Thanks in advance

---

### Post by CelticWarrior on 2019-12-25
Backup & install fresh will definitely be faster than undoing that.

---

### Post by sviginak on 2019-12-25
So if I back up my home folder, make an install usb, and install that while deleting everything, should be golden? I did a backup through system settings already.

---

### Post by guiverc on 2019-12-25
I'm somewhat confused; it's probably terminology.

Lubuntu comes in ISO form, and is installed from thumb-drive.  From terminal you can only install the `lubuntu-desktop` (ie. the desktop used by Lubuntu which varies on your release; LXDE for 18.04).

You mention seeing the Lubuntu icon; I suspect here you mean you see the "Lubuntu" plymouth screen, which is a ~wallpaper that shows on booting the system (is not strictly part of the desktop; it'll be Lubuntu only because it was the last desktop you installed, unless you changed it). The plymouth screen isn't path of the desktop/GUI - just hides text boot messages (giving a graphic as many non-technical users find text boot messages 'scary' as warnings & errors of certain types are normal).

You mention signon; where I'm guessing you enter your username/password; login starts; then fails (no message) then you return to signon/greeter screen.  This is I gather your problem; you cannot access your GUI/desktop.

For GUI logins to proceed, you need some free space in $HOME (your user directory; /home/$USER); if insufficient space is detected, the work files required by GUI cannot be created & login is aborted (no message) & you are returned to login screen/greeter.  I wonder if this is what you are experiencing. 

If you switch to a text terminal (ctrl+alt+F4 for example), you should be able to login; and a `df -hl` (disk free; human-output & local drives only) will show how much space is available (look at /home partition; if you don't have a separate /home partition it'll use space in /). This is one possible problem, and can be fixed by moving files off your $HOME, or removing unwanted files.  I'd check how much space you have available

---

### Post by Impavidus on 2019-12-26
> **guiverc said:**
> 
For GUI logins to proceed, you need some free space in $HOME (your user directory; /home/$USER); if insufficient space is detected, the work files required by GUI cannot be created & login is aborted (no message) & you are returned to login screen/greeter.  I wonder if this is what you are experiencing.

If those file required by the GUI already exist, but you have no write permission on them, you can get the same effect. It was a common problem with files getting owned by root after sudo abuse, but it seems less common nowadays. In any case, make sure all files in your $HOME directory are owned by you.

---

### Post by ajgreeny on 2019-12-26
If you can eventually manage to boot into the Ubuntu GUI as you want, you can find which added packages were installed when you added the **lubuntu-desktop** package by using terminal command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will output a list in date order of anything you have recently installed.
From this you can fairly quickly find those additions at the same time as the **lubuntu-desktop** package and use ```
sudo apt purge "your package list"
``` using the full list from that command, of course.

---

### Post by sviginak on 2019-12-26
All, I am able to log into Unity desktop. Verified in system sttings I am running 18.04.3. I have backed up my personal data and as Celtic Warrior suggested just want to do a clean install. I am not able to download the Ubuntu 18.04.3 ISO. It should go to my download folder but it doesn't show up. Wondering if this is a unity issue? I can also log into Lubuntu, so I will try to download ISO to there. Using 16gb usb stick.

---

### Post by sviginak on 2019-12-26
Thanks to all for the suggestions, I finally took Celtic Warrior's advice. Backed up my personal data and formatted the hd and a clean installation.

---

### Post by ajgreeny on 2019-12-26
Great! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

