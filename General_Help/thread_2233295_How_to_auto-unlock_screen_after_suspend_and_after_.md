---
title: "How to auto-unlock screen after suspend and after waiting 10 minutes-black screen?"
date: 2014-07-07
forum: General Help
---

### Post by linux_dream on 2014-07-07
Hello,
I use Lubuntu 14.04. I've already tried google (returned several "answers") to solve my problem but so far I couldn't. 
If I wait 10 minutes my screen goes black (fine for me), but then if I move the mouse I'm asked my password. I would like to get rid of this and instead, auto login into my session.
The same "problem" appears once I suspend my computer. When I move the mouse or press a key, I'm asked my password again, in order to enter into my session. 

What I've did so far: 
1)Menu ->Preferences -> Power Manager -> Extended -> unticked the "Lock screen when going for suspend or hibernate".  
2)Menu ->Users Settings->Password: Not asked on login.
3)I've typed the command ```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```
4)Typed "[FONT=Ubuntu Mono]sudo leafpad /etc/lxdm/default.conf", the output is [/FONT]```
[base]## uncomment and set autologin username to enable autologin
autologin=linux_dream


## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10


## default session or desktop used when no systemwide config
session=/usr/bin/startlubuntu


## uncomment and set to set numlock on your keyboard
# numlock=0


## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp


## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk


[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1


[display]
## gtk theme used by greeter
gtk_theme=Clearlooks


## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png


## if show bottom pane
bottom_pane=1


## if show language select control
lang=1


## if show keyboard layout select control
keyboard=0


## the theme of greeter
theme=Lubuntu


[input]


[userlist]
## if disable the user list control at greeter
disable=0


## whitelist user
white=


## blacklist user
black=



```

None of these commands worked. Any help is appreciated!

---

### Post by linux_dream on 2014-07-08
And now thanks to this thread: [http://ubuntuforums.org/showthread.php?t=2225413](http://ubuntuforums.org/showthread.php?t=2225413) I have added light-locker to Prefs > Default Apps > Autostart. My lightlocker settings are such that it should never automatically lock the session. Lock on suspend is set to off.  However nothing of this works. Everytime I suspend or wait 10 minutes of innactivity and then move my mouse, I'm asked my password... This is becoming quite annoying, I'd appreciate any help.  Thank you once more.   EDIT: I've downloaded and installed dconfEditor. I ran it and went to "org -> gnome -> desktop -> screensaver" and then I set "Ubuntu lock on suspend" to false. And "lock-enabled" to false, both of these settings were set to true by default.  I suspended my computer... and the locking screen appeared once more!  I can't seem to solve the problem...

---

### Post by linux_dream on 2014-07-09
Problem solved: in Light Locker Settings, "Enable light locker" must be set to off.

---

### Post by linux_dream on 2014-07-10
Correction. The problem is not solved, because after a reboot, although "Enable light locker" is set to off in the Light Locker Settings, I'm still asked my password after 10 minutes of innactivity...

---

### Post by J.P._Kalishek on 2015-01-18
> **linux_dream said:**
> Correction. The problem is not solved, because after a reboot, although "Enable light locker" is set to off in the Light Locker Settings, I'm still asked my password after 10 minutes of innactivity...

I have run out of fixes for this issue as well. Can anybody tell what to do other than trashing lubuntu? I get the screen lock every time I update, and I have now got everything set not to lock, screensaver removed, and still the screen blanks and calls for the password after 10 minutes and after suspending. It has even occured while watching streaming video. Getting into infuriating instead of highly annoying.

---

### Post by linux_dream on 2015-01-18
> **J.P._Kalishek said:**
> I have run out of fixes for this issue as well. Can anybody tell what to do other than trashing lubuntu? I get the screen lock every time I update, and I have now got everything set not to lock, screensaver removed, and still the screen blanks and calls for the password after 10 minutes and after suspending. It has even occured while watching streaming video. Getting into infuriating instead of highly annoying.

What worked for me was ```
sudo apt-get remove light-locker
```. My screen still turns black after 10 minutes of innactivity but I'm not asked my password anymore when I move my mouse.

---

### Post by J.P._Kalishek on 2015-01-19
Yeah, it did once for me as well, or just killing the process does it as well, but every update it returns, and is harder to get rid of. Now, I too can stop light-locker, but blanking every 10 minutes is annoying when watching streams while working on stuff (the laptop with lubuntu is in the garage) gets irritating when you have to stop, clean the grease off, then go move the mouse or otherwise get things to clear the screen. And Of course it happens right as the action gets good.

I think the only fix is going to be moving away from lubuntu and so far that has worked best on that old laptop (formerly a win7 machine) except the updates ruin all settings and this hangover issue no one with support seems to be able to fix.

---

### Post by kerry_s on 2015-01-19
did you get the 1 in control center under privacy?

---

### Post by J.P._Kalishek on 2015-01-19
> **kerry_s said:**
> did you get the 1 in control center under privacy?

I was going to ask where in setting this particular control panel is, but for whatever reason the screen has stopped its ten minute blanking. 
I shut the cover and moved the laptop to the living room so I have something while installing a hard drive in my main computer and again it has not gone to screen blank, so who knows why it is doing this. If I am successful with my other computer, I think I will just change flavors on this one,

---

