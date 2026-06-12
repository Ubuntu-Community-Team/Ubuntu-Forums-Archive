---
title: "Login Loop"
date: 2015-09-23
forum: General Help
---

### Post by physicist2 on 2015-09-23
When I try to login into my user account, the screen goes black and momentarily after I see the login screen. I have tried this with two other user accounts and they all failed to successfully log in. When I ran ```
cat ~/.xsession-errors
``` I got
```
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
Script for ibus started at run_im.
Script for auto started at run_im
Script for default started at run_im.
init: hud main process (6143) terminated with status 127
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: gnome-session (Unity) main process (6150) terminated with status 1
init: at-spi2-registryd main process ended ended, respawning
init: unity-settings-daemon main process (6138) killed by TERM signal
init: Disconnected from notified D-BUS bus
init: Iogrotate main process (6030) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_lib_ibus_ibus-ui-gtk3.1001.crash) main process (6066) killed by TERM signal
init: xsession-init main process (6128) killed by TERM signal
init: unity-panel-service main process (6158) killed by TERM signal
init: job window-stack-bridge failed to stop
```
I already tried the fixes in the thread [https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop), and needless to say, they did not succeed in fixing my dilemma. I am running Ubuntu 14.04 and have an Intel(R) Xeon(R) CPU E5530 @ 2.40GHz. My GPU is a FirePro V5700 and I am using the stock, open-source drivers for it. When I ran ```
ls -ld /tmp
``` I got 
```
drwxrwxrwt 4 root root 12288 Sep 23 23:24 /tmp
```. How do I fix this error?

---

### Post by Bucky Ball on 2015-09-24
When you get to the grub list of kernels to boot when you start the machine, highlight the kernel you want and hit 'e'.

Look for the kernel line ending in 'quiet splash' or something like it. Make it look like this:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to continue with boot. Any luck? If so, we can make that permanent as that change will be lost on reboot.

If it is .xauthority issues, best to just delete .xauthority and .iceauthority and reboot. There's info on the interwebs for how to do it.

* You could try these:

```

sudo rm -rf .Xauthority* 
sudo rm -rf .ICEauthority*
```

You can issue these commands from the login screen by pressing control+alt+F1, login to the CLI.

---

### Post by physicist2 on 2015-09-24
I tried both suggestions but sadly didn't have luck with either. I would like to add that I do not have any encrypted partitions and that when I sign in, there is a stage in which the wallpaper shows and it appears that I will successfully log in, upon which the screen goes black and about a second later I see the log in screen. I would also like to add that I do not want to change the desktop environment (at least permanently) and that a repair installation of Ubuntu is impossible for me to do (the live CD states that it did not find any operating system on the desktop). A clean install of Ubuntu is out of question for me.

---

### Post by Bucky Ball on 2015-09-24
What exactly happened prior to this issue occurring originally? Did you switch the machine on and this is what happened, the black screen? Did you install anything or do and update/upgrade, reboot and got this?

---

### Post by physicist2 on 2015-09-24
I had performed a standard update of the computer (sudo apt-get update,  sudo apt-get install dist-upgrade) and then rebooted the system before running into the login loop.  However, since my original post, I upgraded from Ubuntu 14.04 LTS to Ubuntu 14.10 and still cannot log in. However, I noticed that the black screen I  mentioned previously had some white text in it, so I took a picture when the  screen went black and found that it says ```
saned disabled; edit /etc/default/saned
```. I rectified the error and now just see a black screen stating ```
 saned.
```.

---

### Post by Bucky Ball on 2015-09-25
Wrong. 14.10 is dead, end-of-life, no longer supported. Go back, wrong way. Updates are not available and this is a step backwards.

We do not provide support for EOL releases.

---

### Post by physicist2 on 2015-09-25
Upgrading to Ubuntu 14.10 is a chain in the link from Ubuntu 14.04 LTS to Ubuntu 15.04 which I know has 9 months support. In any case, I still cannot log into my computer.

---

### Post by Bucky Ball on 2015-09-25
> **physicist2 said:**
> Upgrading to Ubuntu 14.10 is a chain in the link from Ubuntu 14.04 LTS to Ubuntu 15.04 which I know has 9 months support. In any case, I still cannot log into my computer.

You mean a link in the chain and I mean that link is missing. [See for yourself]("https://wiki.ubuntu.com/Releases"). It is not possible to upgrade to 14.10> 15.04. :)

Clean install of 15.04 if you want to go there for the next four months. Bear in mind that 14.04 LTS can be upgraded directly to 16.04 LTS when it is available, skipping the interim releases in between, but getting off topic.

Your best and only route is [this]("https://help.ubuntu.com/community/EOLUpgrades") if you want to try to get to an EOL release on your way to a supported one. A possibly long and treacherous path.

---

### Post by ptn107 on 2015-09-25
14.10 may be EOL but the archive is still hosted at the normal location ([http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)).  It has not [yet] been moved.  You can upgrade to 15.04 with the software updater application.  Full instructions [here]("https://wiki.ubuntu.com/VividVervet/ReleaseNotes#Upgrading_from_Ubuntu_14.10").

---

### Post by physicist2 on 2015-09-25
Bucky Ball, I just successfully upgraded to Ubuntu 15.04 from Ubuntu 14.10 whilst keeping all my files. I still cannot log into my computer but the black screen during the transition now displays the text ```
[ OK ] Started Light Display Manager.
       Starting Network Manager Script Dispatcher Service...
[ OK ] Started Network Manager Script Dispatcher Service.
[ OK ] Stopped LSB: Start NTP daemon
```
where OK is written in green.

---

### Post by deadflowr on 2015-09-25
Not sure, but something from the initial xsession error log shows the mesa gl library is messed up.
Is the package libgl1-mesa-glx installed?

When you login can you switch to a tty1-6 (you can try using ctrl + alt + F1-6)
If so, and it brings up a login prompt, login and run an apt-cache policy command for that named package
```
apt-cache policy libgl1-mesa-glx
```
You maybe even need to try a reinstall.

Not sure whether this is helpful.

---

### Post by physicist2 on 2015-09-25
I ran ```
apt-cache policy libgl1-mesa-glx
``` and got ```
 libgl1-mesa-glx:
  Installed: 10.5.9-2ubuntu1~vivid2
  Candidate: 10.5.9-2ubuntu1~vivid2
  Version table:
*** 10.5.9-2ubuntu1~vivid2 0
       500 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main amd64 Packages
       100 var/lib/dpkg/status
   10.5.2-0ubuntu1 0
       500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
```
with no change. I am not quite sure how to reinstall libgl1-mesa-glx. I ran ```
sudo lightdm restart
``` afterwards and was greeted with the message ```
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions? 
```. Going back to the Desktop with Ctrl-Alt-F7, I just see ```
[ OK ] Started Light Display Manager.
       Starting Network Manager Script Dispatcher Service...
[ OK ] Started Network Manager Script Dispatcher Service.
[ OK ] Stopped LSB: Start NTP daemon.
``` with OK in green letters as opposed to the login screen I saw before. However, I still see my cursor.

---

### Post by deadflowr on 2015-09-25
Well, worth a shot to look at.
Seems the packages is fully installed, so at least that seems ok, or fixed (maybe?)

As a sidenote, 15.04 now uses the systemd init system, as opposed to Upstart (which Ubuntu used prior), so you'd need to use the systemd commands to restart lightdm
```
sudo systemctl restart lightdm
```

Also, not quite a fix, but you might see if you can install and load a separate desktop.
I'd try gnome-session-flashback (Ubuntu's desktop unity and gnome-flashback functional pretty seemlessly, imo.)
```
sudo apt-get install gnome-session-flashback
```
and try to login with the NO Effects option--metacity.

(you can choose it at the login screen.
In Ubuntu's login to switch desktop sessions to load, click on the icon in the username/password box; it will be in the top right corner)

Like I state, not a fix, but it should at least give you a functional desktop, one would think.
(the metacity session doesn't require the opengl libraries, from what I remember)

---

### Post by physicist2 on 2015-09-25
Installing gnome-flashback and using the metacity option does allow me to log in. However, as you said, this is not a fix. I reran ```
cat ~/.xsession-errors
``` in a terminal and got ```
openConnection: connect: No such file or directorycannot connect to brltty at :0
upstart: upstart-event-bridge main process (1625) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application main process ended, respawning
upstart: indicator-application respawning too fast, stopped

```

---

