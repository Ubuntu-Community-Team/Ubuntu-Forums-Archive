---
title: "Black screen and weird cursor on startup"
date: 2017-07-29
forum: General Help
---

### Post by lauchahuman on 2017-07-29
Hello everyone, So today I turned on my laptop (Thinkpad x220) and found out this: Cursor shaped as an X and no backgroud, also not possible to close or minimize any windows. 

[URL="http://imgur.com/a/5vAdH"]http://imgur.com/a/5vAdH
[/URL][IMG]http://i.imgur.com/u9JDtST.png[/IMG]

If I press ctrl + alt + f1 and run "startX" command  it shows me the desktop again, but not perfectly normal as seen in the images below

[URL="http://imgur.com/a/aVOfI"]http://imgur.com/a/aVOfI
[/URL][img]http://i.imgur.com/QFkm746.png[/img]

[http://imgur.com/a/GNrWL](http://imgur.com/a/GNrWL)
[IMG]http://i.imgur.com/0hyzDQm.png[/IMG]

You can see a horizontal line near the bottom of the screen. Also I'm pretty sure the fonts are displaying different than before (a little bigger) and some of the windows manager settings are not loading correctly (for example I had the background of highlighted text in red and now is showing in blue).

If I enter in the Guest session the desktop is displayed correctly (no dark line in the bottom, no weird size fonts).

Any ideas how can I fix this?

Thank you and sorry for my potato english.

---

### Post by BenginM on 2017-07-29
Hiya , if the Guest session behaved and worked properly , then it's a user miss configration on your part,.. custom theme , something along the line..

---

### Post by lauchahuman on 2017-07-30
> **BenginM said:**
> Hiya , if the Guest session behaved and worked properly , then it's a user miss configration on your part,.. custom theme , something along the line..
Hello! Thank you for your reply.
Hum.. I see. That's weird because I haven't touched anything related to the theme/visuals since February. Do you think there's any way to solve it without reinstalling the OS?

Thanks.-

Edit: Also I forgot to mention that the console starts on it's own without me executing it..

---

### Post by BenginM on 2017-07-30
Hiya , ok then.. if it's not related to a custom them configuration , then it's a weird behaviour indeed , did this happen after packages upgrade! we can't tell yet if it's graphic driver at fault, X11 not starting .. whichever the cause is we need to look at the logs , any hint in .xsession-errors on your home directory , and Xorg.0.log in /var/log , did you add/change something in .Xauthority ! also, which GPU is in use .. no need to reinstall , we might be able to troubleshoot this.. as you stated no such behaviour in a guest session .. so even if you create a new user you shouldn't have this issue either.

 if you run these commands , it will generate a result pastebin link for each :

sudo cat /var/log/dmesg | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat /var/log/syslog | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat /var/log/Xorg.0.log | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat ~/.xsession-errors | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)


so we may have a look at the logs ..

---

### Post by lauchahuman on 2017-07-30
> **BenginM said:**
> Hiya , ok then.. if it's not related to a custom them configuration , then it's a weird behaviour indeed , did this happen after packages upgrade! we can't tell yet if it's graphic driver at fault, X11 not starting .. whichever the cause is we need to look at the logs , any hint in .xsession-errors on your home directory , and Xorg.0.log in /var/log , did you add/change something in .Xauthority ! also, which GPU is in use .. no need to reinstall , we might be able to troubleshoot this.. as you stated no such behaviour in a guest session .. so even if you create a new user you shouldn't have this issue either.

 if you run these commands , it will generate a result pastebin link for each :

sudo cat /var/log/dmesg | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat /var/log/syslog | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat /var/log/Xorg.0.log | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)

sudo cat ~/.xsession-errors | curl -F 'sprunge=<-' [http://sprunge.us](http://sprunge.us)


so we may have a look at the logs ..

Hello! I hope I ran the commands correctly (The first says "nothing has been logged yet"). 

First command: [http://sprunge.us/BfDB](http://sprunge.us/BfDB)

Second command: [http://sprunge.us/TKci](http://sprunge.us/TKci)

Third command: [http://sprunge.us/ThNK](http://sprunge.us/ThNK)

Fourth command: [http://sprunge.us/EdDD](http://sprunge.us/EdDD)

Thank you!

---

### Post by BenginM on 2017-07-31
Thanks , well your .xsession-errors shows :

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
Xsession: X session started for laucha at dom jul 30 19:05:50 ART 2017
localuser:laucha being added to access control list
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Unable to create /home/laucha/.dbus/session-bus
/usr/bin/x-session-manager: X server already running on display :1
xfce4-session-Message: SSH authentication agent is already running
gpg-agent[2216]: WARNING: "--write-env-file" is an obsolete option - it has no effect
gpg-agent: a gpg-agent is already running - not starting a new one

```

mine looks like this , running lubuntu with lxqt
[http://sprunge.us/ERHU](http://sprunge.us/ERHU)

I wonder what does:

```

ls -lanF .Xauthority


```

Shows!

mine shows:
```


sary@tru:~$ ls -lanF .Xauthority
-rw------- 1 1000 1004 48 Jul 29 07:09 .Xauthority


```

also, what does :

```

ls -l ~/.cache/sessions
ls -l ~/.config/
ls -l ~/.config/autostart/

```

has to shows us ..

and since you're using lightdm , There are also 2 log files in var/log/lightdm that might be useful. However, you need root privileges to read them. They are:

 /var/log/lightdm/lightdm.log

 /var/log/lightdm/x-0-greeter.log

lets see what those logs shows ..

you might just try login with a fresh profile session by removing ~/.config and ~/.cache directories as a qucik fix ..

something like:
[https://unix.stackexchange.com/questions/52087/clear-xfce4-session](https://unix.stackexchange.com/questions/52087/clear-xfce4-session)

Drop out of XFCE with Ctrl + Alt + F1, navigated to ~/.cache/sessions/ and delete the contents with the following command:    rm -rf *
Do the same in/for ~/.config 



see if that solve the issue , if not then we're dealing with a different issue , a graphic driver would be next to check!

---

### Post by BenginM on 2017-07-31
I also see this from syslog :

LauchaAA lightdm[1107]: ** (lightdm:1107): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed

i don't know what the error exactly means, you might want to try using a different login manager , i use sddm which stable and looks nice too!

sudo apt install sddm
sudo dpkg-reconfigure lightdm

You will be presented with an option box.  Choose sddm, press TAB to select the OK button, then press enter.

save your works and reboot .. test sddm stability for some time.

---

### Post by lauchahuman on 2017-07-31
Hello man. Thank you for your time. I installed sddm but could not log in with it, so I went back to lightdm, but then entered on a login loop, so I googled a bit an executed the command "sudo rm -r ~/.ICEauthority, now I can at least log in (I uninstalled sddm)

1)```
ls -lanF .Xauthority 
```

Shows ```
  -rw------- 1 1000 1000 53 jul 31 09:52 .Xauthority 
```
2)  ```
 ls -l ~/.cache/sessions
```  Shows this ---> [http://sprunge.us/IOSP](http://sprunge.us/IOSP)
3) ```
ls -l ~/.config/ 
```   Shows this ---->[http://sprunge.us/JEFS](http://sprunge.us/JEFS)
4)```
 ls -l ~/.config/autostart/ 
``` shows ----> [http://sprunge.us/FUKi](http://sprunge.us/FUKi)


I entened  */var/log/lightdm/lightdm.log  *using* "sudo nano [I]/var/log/lightdm/lightdm.log" *[/I]from the console (I hope that was ok) and it displayed the following: 
> [+845.79s] DEBUG: Session pid=1168: Terminated with signal 1
[+845.79s] DEBUG: Seat seat0: Session stopped
[+845.79s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+845.79s] DEBUG: Sending signal 15 to process 1109
[+845.81s] DEBUG: Got signal 15 from process 1
[+845.81s] DEBUG: Caught Terminated signal, shutting down
[+845.81s] DEBUG: Stopping display manager
[+845.81s] DEBUG: Seat seat0: Stopping
[+845.83s] DEBUG: Process 1109 exited with return value 0
[+845.83s] DEBUG: DisplayServer x-0: X server stopped
[+845.83s] DEBUG: Releasing VT 7
[+845.83s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+845.83s] DEBUG: Seat seat0: Display server stopped
[+845.83s] DEBUG: Seat seat0: Stopped
[+845.83s] DEBUG: Display manager stopped
[+845.83s] DEBUG: Stopping daemon
[+845.84s] DEBUG: Exiting with return value 0
[+0.23s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.39s] DEBUG: Starting Light Display Manager 1.18.3, UID=0 PID=1074
[+0.39s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.39s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/40-kde-plasma-kf5.co$
[+0.39s] DEBUG:   [SeatDefaults] is now called [Seat:*], please update this configuration


Also looks like I don't have the /var/log/lightdm/x-0-greeter.log file. ```
/var/log/lightdm ls command
``` showed this-->
```
lightdm.log       lightdm.log.7.gz        seat0-greeter.log.6.gz  x-0.log.5.gz  x-1.log.4.gz
lightdm.log.1.gz  seat0-greeter.log       seat0-greeter.log.7.gz  x-0.log.6.gz  x-1.log.5.gz
lightdm.log.2.gz  seat0-greeter.log.1.gz  x-0.log                 x-0.log.7.gz  x-1.log.6.gz
lightdm.log.3.gz  seat0-greeter.log.2.gz  x-0.log.1.gz            x-1.log       x-1.log.7.gz
lightdm.log.4.gz  seat0-greeter.log.3.gz  x-0.log.2.gz            x-1.log.1.gz
lightdm.log.5.gz  seat0-greeter.log.4.gz  x-0.log.3.gz            x-1.log.2.gz
lightdm.log.6.gz  seat0-greeter.log.5.gz  x-0.log.4.gz            x-1.log.3.gz


```

Next I'm going to try to remove ~/.config and ~/.cache directories and see what happens.

Edit: I ran the commands *rm -rf *  on ~/.config and ~/.cache, and even though the desktop config theme went back to stock, I'm Still getting the black screen, X shaped mouse pointer and no windows "minimize, expand and close". :(*

---

### Post by BenginM on 2017-08-01
Salutations! Hiya laucha ..*Please excuse the delay , i guess we're in a different time-zone.*

Because startx works just right .. It seem like for some reasons the  login manager "lightdm" does not start the window manager and not  setting up the session correctly.

now we see ..

```


DEBUG: Session pid=1168: Terminated with signal 1


```

are you somehow connection login'in remotely ..!

```

DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0

```

make sure .ICEauthority and .Xauthority are owned by YourUser ..

$ sudo chown laucha:laucha /home/laucha/.ICEauthority
$ sudo chown laucha:laucha /home/laucha/.Xauthority

##

awww! wow, to many logs under /var/log/lightdm .. no need to keep these old logs feel free to remove them.

Well, it's unfortunate that SDDM didn't work for you , and removing [I]  ~/.config and ~/.cache , but now with those removed and (  .ICEauthority, .Xauthority ) are set for your own user .. you should now  have a clean slate .. if that doesn't result in a clean login to the  desktop with prober behaviour then it's lightdm's fault's , or the  window manager in use , you may want to try a different login manager ,  there is GDM , SLIM ,..

you can see the default window manager in use by runin': sudo update-alternatives --query x-session-manager

up next we should try rebootin' with a new kernel that should have a newest kernel driver version for the current GPU ...

you can see which driver/s in use $ inxi -G

you may install inxi if it's not present , sudo apt install inxi

I see form the Xorg.0.log , that you have 



[/I]```
intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1.2
intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 3000
```[I]

Just so you know, some users had this issue with lightdm ,

[https://askubuntu.com/questions/346738/13-04-lightdm-crashing-black-screen-flashing-cursor](https://askubuntu.com/questions/346738/13-04-lightdm-crashing-black-screen-flashing-cursor)
[https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot](https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot)
[https://askubuntu.com/questions/744089/cursor-is-an-x-and-panel-isnt-working-correctly](https://askubuntu.com/questions/744089/cursor-is-an-x-and-panel-isnt-working-correctly)
[https://askubuntu.com/questions/720321/15-10-lightdm-broken-gdm-works](https://askubuntu.com/questions/720321/15-10-lightdm-broken-gdm-works)
[https://forum.xfce.org/viewtopic.php?id=10114](https://forum.xfce.org/viewtopic.php?id=10114)
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1172018)
[URL="https://bugs.launchpad.net/ubuntu/+bug/1573454"]https://bugs.launchpad.net/ubuntu/+bug/1573454
https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/944784[/URL]

[/I]

---

### Post by lauchahuman on 2017-08-01
Hello!! Hey, no problem about the delay, yes different times zones indeed, at least you're helping :grin:
So I ran this commands 
```
$ sudo chown laucha:laucha /home/laucha/.ICEauthority
$ sudo chown laucha:laucha /home/laucha/.Xauthority
```
And looked like nothing happened afte I hit enter, so I rebooted and all  was a mess (more than before) Image link Since the post was too image  heavy


[http://i.imgur.com/9WF3TGk.png](http://i.imgur.com/9WF3TGk.png)


[SIZE=2]I coudn't even right click, also firefox would start  automatically in every log in.   So what I did was install DGM, and good  news: No more black screen and no more weird shaped mouse pointer,  although I did got and error that I don't know what it means.[/SIZE]

[http://i.imgur.com/fHnwcvU.png](http://i.imgur.com/fHnwcvU.png)


[SIZE=2]Still some things ****ed up, like the top panel and other minor theme configs (colors, icons, etc)
After running ```
[I]sudo update-alternatives --query x-session-manager
[/I]
```
This is what I get.
[/SIZE]
[http://i.imgur.com/FQf5aNW.png](http://i.imgur.com/FQf5aNW.png)[SIZE=4]


[SIZE=2]Also is it possible to have two windows managers at the same time? Because look:
[/SIZE][/SIZE]
[http://i.imgur.com/h9X6vdm.png](http://i.imgur.com/h9X6vdm.png)

[SIZE=2]I wonder if that would cause trouble....

After runnin "inxi -G" 
> ```
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 17.0.7
```

So...Long story short looks like the problem was the login manager wasn't it?

Edit: Still getting system problem detected error, desktop passes thru black and x shaped mouse pointer and then I get normal desktop, pretty annoying. 
Edit2: Also I see the dark horizontal line that can be seen in the 1st post is back afetr some time of use :S. This is getting on my nerves!! lol.
[/SIZE]

---

### Post by BenginM on 2017-08-01
Ok, thanks for your understanding ... 

setting the ownership and group to your YouUser name on these file won't make a mess, if anything it's the opposite .. **~/.ICEauthority and ~/.Xauthority are updated automatically whenever you log in to a graphical environment. Losing those only breaks things until a reboot, at worst. (Besides, if they were empty, then they weren't being used in the first place.)** it's completely safe to remove the .Xauthority after your X session has ended as long as you aren't storing any other tokens in it that you might need to keep (e.g. tokens for logging into remote X servers).

looking [At]("http://i.imgur.com/9WF3TGk.png")  , is differently a strange behaviour almost looks like you're logging remotely and forwarding X...

the Firefox and terminal starting [SIZE=2]  automatically i believe this answer's it :

[https://askubuntu.com/questions/125718/how-can-i-stop-terminal-and-firefox-from-launching-on-startup](https://askubuntu.com/questions/125718/how-can-i-stop-terminal-and-firefox-from-launching-on-startup)
[/SIZE]
lookin' [At]("http://i.imgur.com/FQf5aNW.png")

you have a gnome-session and kde .. and startxfcr4 is set to auto  ... when you see the login manager try loggin using the Xfce4-session .. maybe startxfce4 is the cause of the odd behaviour ..!

it's ok to have two different window managers as long as you logout-back in when you switch between them , you can use sudo update-alternatives --config x-window-manager to set the default WM , or use the Xubuntu session settings like in lubuntu i can use :

[ATTACH=CONFIG]276227[/ATTACH]


but [looking At]("http://i.imgur.com/h9X6vdm.png")  .. i think you mean that you have two file managers which is fine too .. 

Regarding [This]("http://i.imgur.com/fHnwcvU.png") , it's a system wide internal issue maybe it crashes because you're bootin' with [This]("https://help.ubuntu.com/community/vt.handoff") , you may report it to an existing bug report in launchpad or creat a new bug report.

Ok, it's good to know that Intel is the driver in use for the Intel GPU and not the fallback generic Vesa driver..

Chea it's annoying indeed .. i think the cause might be login in with startxfce4 instead of Xfce4-session .. could you please try logging with Xfce4-session and check the behaviour ..

in my system lubuntu with lxqt, am logged in with startlxqt with no issue , #see:

[ATTACH=CONFIG]276226[/ATTACH]

Edit: now reading :
[http://manpages.ubuntu.com/manpages/xenial/man1/startxfce4.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/startxfce4.1.html)
[URL="http://manpages.ubuntu.com/manpages/xenial/man1/xfce4-session.1.html"]http://manpages.ubuntu.com/manpages/xenial/man1/xfce4-session.1.html

[/URL]

---

### Post by lauchahuman on 2017-08-02
Hello again :). 
So I logged in with xfce session as you said aaaaaannddd.....No X shaped cursor, no dark horizontal line, no terminal or firefox launching on startup!!!:D:D.

About the window manager, yes, I meant to say file manager (still some terms are difficult for me to learn), because I saw that sometimes a windows would launch on thunar and other times would launch on the other file manager (that I don't remember the name now), and I thought maybe having two file managers wasn't normal.

Also I'm not getting the "System error" at startup either anymore! :).

You're awesome men! thank you for your time and your PATIENCE, now the time consuming task of "ricing" the OS awaits.


Cheers!

I would edit if I see some weird behavior again (fingers crossed).

Edit: The dark horizontal line appears after some time of use. I'm thinking it may be a hardware issue...(maybe the monitor is about to break), which is weird because I just turned the laptop off and on inmediatelly and the line is not there

---

### Post by BenginM on 2017-08-03
Hey, good to know , np glad to assist :) 
So, Now you were having this second issue on an external monitor and not the laptop built-in screen!Which monitor is it , and is it connected through HDMI ..!

---

### Post by lauchahuman on 2017-08-03
No,no, the dark line it's on the laptop screen (sorry it was very late and my English was potato). Also I got the system problem detected error again at login, but no further problems, only that error. It's weird because it's like the system is very inconsistent, sometimes login normally, sometimes the error would appear. I did report the error though. Also I tried to install SLIM and it didn't work properly (also geting black screen), so it appears that GDM3 is the only one that works -which is a shame because it's pretty ugly :p-.  
I'll re-read everything that you posted and orginize everything in my head, and see if I get it to work properly on my own. I'll keep you updated!.

Cheers!.

Lau.-

Edit 1: I ran read some of the links you posted and looked like this guy-->[https://askubuntu.com/questions/744089/cursor-is-an-x-and-panel-isnt-working-correctly](https://askubuntu.com/questions/744089/cursor-is-an-x-and-panel-isnt-working-correctly)   Had very similar error codes. I followed the instructions in the thread and still light is non functional.

Edit 2: Is this normal? [http://imgur.com/a/kmvq6](http://imgur.com/a/kmvq6)  /var/log/lightdm folder appears with an x.  Trying to reinstall lightdm now---> ```

[LIST=1]
[*]sudo apt-get remove lightdm* --purge 
[*]sudo reboot 
[/LIST]

```

Should I change the permissions to lightdm directory?  I did ran ```
 sudo chown -R lightdm /var/lib/lightdm


``` to see if that changes something....but I did't change the permissions yet nor reinstalled lightdm

Edit 3: Reinstallin lightdm didn't work,  I installed lxdm but entered into a login loop, so I went back to gdm.

---

### Post by BenginM on 2017-08-06
Hiya , laucha , Yes the X on the file in /var/log/lightdm is how it looks in my system , i've installed lightdm to conform ..

Well, this is how you remove a package

```



sudo apt-get remove --purge PackageNameHere

so ..

sudo apt-get remove --purge lightdm

purge flag, will remove all config files too ..

This is how you reinstall a package ..

sudo apt install --reinstall Package

so..

sudo apt install --reinstall lightdm



```

---

### Post by lauchahuman on 2017-08-08
> **BenginM said:**
> Hiya , laucha , Yes the X on the file in /var/log/lightdm is how it looks in my system , i've installed lightdm to conform ..

Well, this is how you remove a package

[PHP]


sudo apt-get remove --purge PackageNameHere

so ..

sudo apt-get remove --purge lightdm

purge flag, will remove all config files too ..

This is how you reinstall a package ..

sudo apt install --reinstall Package

so..

sudo apt install --reinstall lightdm


[/PHP]

I see. I was using the command improperly. Anyway I couldn't make any other login manager to work, only GDM. 

Cheers.

Lau.-

Edit: Ok almost 2 months later problem are solved, not perfectly but better than nothing. I'll edit in case some reads this while googling solutions. 
The dark horizontal line is easily fixed by launching Windows manager tweaks, going to the compositor tab and unchecking the "Show shadows under dock windows options"
The "system program problem detected at startup was a /sbin/plymouthd error, so I installed Synaptic package manager and downloaded the Plymouth-x11 package (I downloaded others packages also while messing around that broke other things lol, but that one solved the problem).
The only thing I could not figure it out was why I can only start session when GDM is the display manager, other displays managers give me a dark screen with X cursor. (tried almost every other display manager).

---

### Post by BenginM on 2017-08-08
Yeah, that's unfortunate as SLIM and SDDM are lightweight and decent to look at.. see some screenshots on google-image.

---

