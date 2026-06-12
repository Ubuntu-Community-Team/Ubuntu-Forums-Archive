---
title: "Scrambled graphics after changing screen type - can't undo"
date: 2007-12-07
forum: General Help
---

### Post by Nytron on 2007-12-07
I changed my screen type from Generic to the specific screen I am using (which is a SyncMaster 192N). I received a prompt that told me I have to log out for the change to take effect, so I logged out. When I went to log back in, the screen was completely scrambled, making it impossible to navigate back to the menu to change the screen type back to generic to undo all of this.

I'm guessing there's a way to fix this in the console and it starts with sudo.

Help.

---

### Post by taurus on 2007-12-07
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X again with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to your GUI login screen with <Alt>F7 and restart X server again with <Ctrl><Alt>Backspace.

---

### Post by Nytron on 2007-12-07
> **taurus said:**
> Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X again with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to your GUI login screen with <Alt>F7 and restart X server again with <Ctrl><Alt>Backspace.good lord

brb pen :lol:

---

### Post by Nytron on 2007-12-07
> **taurus said:**
> Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X again with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, get back to your GUI login screen with <Alt>F7 and restart X server again with <Ctrl><Alt>Backspace.the file copy didnt work, so i skipped that and did the sudo dpkg-reconfigure line and it worked.

Thanks

---

### Post by heatpumpcontrol on 2007-12-07
After boot up, don't log in. Hit CTL+ALT+F1, enter your credentials and then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

follow the commands by answering the questions and make sure you select "vesa" as your video driver and generic screen with auto detect. Don't select advanced.

This should get you back to a viewable screen. After that, once you log in, go to 
Places, Computer and navigate to /etc/X11/ folder. There you'll see a file 'xorg.conf'. Now, if you see other files named similarly with a date or a .bak or .old extension then you should open one of those (or it), and compare it to your ative 'xorg.conf' file. Read carefully. This may be you original 'xorg.conf' file before the change. Check its properties to confirm the date and time it was last accessed or created. If it is what you believe to be your original 'xorg.conf' file then you can restore your current 'xorg.conf' file to the old settings from that old file.

back up current xorg.conf by:
```
sudo cp /etc/X11/xorg.conf /etc/X11/Xorg.conf.mybakup
``` <-- this makes a backup of your current xorg.conf file

now to copy your the file you believe is your old 'xorg.conf' file to the current 'xorg.conf' file:
```
sudo cp /etc/X11/xorg.conf.(enter here the full name of the file you found) (1 space)/etc/X11/xorg.conf
```

now restart X:
```
sudo /etc/init.d/gdm restart
```

after that you should be back to original configuration.

---

### Post by SneakyBooBoo on 2008-02-09
erm ran into the same kinda problem myself. i thought i could get better performance if i changed my driver and ended up killing it. when i try to boot x windows i crashes and says something about not being able to use the video resolution specified. can i use this method from the command prompt to restore my graphics config?

---

### Post by SneakyBooBoo on 2008-02-10
nevermind, i tried those commands and it worked. thx anyways. :)

---

