---
title: "How to disable screensaver/blank screen in 12.10"
date: 2013-01-31
forum: General Help
---

### Post by Balthier1979 on 2013-01-31
Hello guys, I am running an application in fullscreen. The application is  signageplayer from digitalsignage. Its an application that shows ads, news and such.
 
But the problem is that my screen keeps blanking every 5-10 minutes. I have turned off the settings for this in Brightness and Lock, but to no avail. I've also tried to run the following command
 
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
 
but still no go. Is there a way to prevent the screen going blank in 12.10?
 
In windows, you can actually make a batch file, then convert it to an executable file, and then change the extension from .exe to .scr and have the batch file run as the screensaver. You can set the batch file to do whatever you like, such as for example not do anything at all.
 
Is this possible in Ubuntu/Linux)? Because then I could run a batch file as the screen saver, and instead of it going blank, it would do nothing at all, which would solve the problem.

---

### Post by BlinkinCat on 2013-01-31
Hi,

This thread may be of assistance -

[http://ubuntuforums.org/showthread.php?t=2059551](http://ubuntuforums.org/showthread.php?t=2059551)

Cheers - :)

---

### Post by Balthier1979 on 2013-01-31
Thanks. I've tried to install Caffeine on my test computer. The first time I managed to run Caffeine preferences and set it to start automatically at logon, but it does not seem to start, and when I try to access it from Dash, nothing happens.
 
On my production computer, the strange thing is that the screen only goes blank when I am running that application. If I leave the screen on desktop, with or without a terminal window started, it does not go blank.

---

### Post by BlinkinCat on 2013-01-31
> **Balthier1979 said:**
> Thanks. I've tried to install Caffeine on my test computer. The first time I managed to run Caffeine preferences and set it to start automatically at logon, but it does not seem to start, and when I try to access it from Dash, nothing happens.
 
On my production computer, the strange thing is that the screen only goes blank when I am running that application. If I leave the screen on desktop, with or without a terminal window started, it does not go blank.

Hi,

Have read the guides ? You could search for them in Googlubuntu (link on my signature) I only briefly ran Caffeine (no longer do, but I know others swear by it) From what I remember you have to add the apps that you do not wish to start in the GUI. One of those was gnome-screensaver from memory. I have xubuntu now and no longer need Caffeine.

Hope that helps,

Cheers - :)

---

### Post by 3246251196 on 2013-01-31
> **BlinkinCat said:**
> Hi,

Have read the guides ? You could search for them in Googlubuntu (link on my signature) I only briefly ran Caffeine (no longer do, but I know others swear by it) From what I remember you have to add the apps that you do not wish to start in the GUI. One of those was gnome-screensaver from memory. I have xubuntu now and no longer need Caffeine.

Hope that helps,

Cheers - :)

```

$ gnome-screensaver-command --help
Usage:
  gnome-screensaver-command [OPTION...]

Help Options:
  -h, --help           Show help options

Application Options:
  --exit               Causes the screensaver to exit gracefully
  -q, --query          Query the state of the screensaver
  -t, --time           Query the length of time the screensaver has been active
  -l, --lock           Tells the running screensaver process to lock the screen immediately
  -a, --activate       Turn the screensaver on (blank the screen)
  -d, --deactivate     If the screensaver is active then deactivate it (un-blank the screen)
  -V, --version        Version of this application

$ ps -e | grep screen
 1503 ?        00:00:00 gnome-screensav

```

I wonder if killing the process would help ?

---

### Post by Balthier1979 on 2013-01-31
I'm afraid to install Caffeine on my production computer, as installing it on my test computer did not give the desired results.
 
Is the screensaver just a file, like it is in Windows? Is there a way I can just rename that file perhaps, then the OS would not have any screensaver to run?
 
I've read around a little, and found a few interesting tips, such as this thread
 
[http://ubuntuforums.org/showthread.php?t=2062608&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=2062608&highlight=screensaver)
 
but I am not quite able to comprehend what I am supposed to do, as I am quite new to Ubuntu. So I tried to run the following commands
 
xset dpms 0 0 0
xset s noblank
xset -dpms
 
Then logged off and logged and, but still the same problem. So I tried to restart the computer, and now I only get a blank screen at log on. I am able to open a terminal session with ctrl+alt+F1, but when I run xset q, I get the following error message
 
"unable to open display"
 
Help :)

---

### Post by Balthier1979 on 2013-01-31
Bah, it was just my USB hub that was causing the problem. I removed it, and Ubuntu started just fine.
 
How about this solution
 
*This is a pretty common issue with all versions of Ubuntu. First by default the gnome screensaver is installed and will blank the screen in about 10 minutes. So one of the fist things that I do after a new install is to remove it and replace it with xscreensaver which you can access and choose a screensaver or none at all. *
 
*From Terminal, run the following:*
 
[I]sudo apt-get purge gnome-screensaver
sudo apt-get install -y xscreensaver xscreensaver-gl-extra xscreensaver-data-extra[/I]
 
*Once installed, restart and then look for xscreensaver in the Dash, run it and then configure what you want.*
 
what if I just *sudo apt-get purge gnome-screensaver *to remove the screensaver. Will not the problem be out of the world then? I don't need a screensaver, as the computer and the screen is supposed to be on 24x7. Hibernation/sleep has been turned off.
 
Sorry for two consectuive posts.

---

### Post by Balthier1979 on 2013-01-31
I think I have found the solution to the problem. Just removing the gnome-screensaver did not help. But installting the xscreensaver kind of does. But the thing is that if I set the screensaver to be disabled in xscreensaver, it will stay disabled, until the computer is restarted, then I have to start the xscreensaver preferences panel again, click ok on a message box, to get Ubuntu to disable the screensaver again.
 
This is the dpms state at startup (even if screensaver has been disabled in xscreensaver)
 
[http://s4.postimage.org/yhgw5w8ct/dpms1.png](http://s4.postimage.org/yhgw5w8ct/dpms1.png)
 
The reason for this is following

[http://s14.postimage.org/e6ffmyc2p/dpms2.png](http://s14.postimage.org/e6ffmyc2p/dpms2.png)

If I click ok on the dialogbox, the settings are set correctly once again
 
[http://s14.postimage.org/6dpa1vzj5/dpms3.png](http://s14.postimage.org/6dpa1vzj5/dpms3.png)
 
So what I want to achieve is that the xscreensaver daemon is launched automatically on display:"0" (the only display the computer is connected to) at startup. Perhaps I can achieve this by making a startup script?
 
All help would be appreciated :)

---

### Post by Balthier1979 on 2013-02-07
Any help would be appreciated :)
 
I think I know how I can achieve this. I need to create a xscreensaver.desktop file in the /etc/xdg/autostart folder, and then have it run both xscreensaver and xscreensaver-demo at startup . But how do I do that, I can have it run, one or the other, but not both.

[Desktop Entry]
Exec=xscreensaver
Name=XScreenSaver
Type=Application
X-KDE-StartupNotify=false

Btw, what does x-kde-startupnotify do?

---

### Post by Balthier1979 on 2013-02-07
Ok, I've managed to solve it. I made two files, xscreensaver.desktop and xscreensaverdemo.desktop, and put both in the /etc/xdg/autostart folder. Then I made both executable.
 
xscreensaver.desktop
 
[Desktop Entry]
Exec=xscreensaver
Name=XScreenSaver
Type=Application
X-KDE-StartupNotify=false
 
xscreensaverdemo.desktop
 
[Desktop Entry]
Exec=xscreensaver-demo
Name=XScreenSaverDemo
Type=Application
X-KDE-StartupNotify=false
 
Now both run at startup, and that gives me the follwing dpms settings
 
[http://s14.postimage.org/6dpa1vzj5/dpms3.png](http://s14.postimage.org/6dpa1vzj5/dpms3.png)
 
But the xscreensaverdemo window stays open at startup. For my purpose it doesn't matter much, as the application I am running runs in fullscreen and therefore the xscreensaverdemo window is not viewable on the screen, unless I close that application.
 
But is there a way I can minimise or close that window, after having opened it? Without using the mouse of course. This is the window I want to close or minimise
 
[http://s12.postimage.org/k0ixkwfb1/xscreensaver.png](http://s12.postimage.org/k0ixkwfb1/xscreensaver.png)

---

