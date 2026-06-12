---
title: "Enable the desktop wall in ccsm"
date: 2014-08-25
forum: General Help
---

### Post by riley_mcmahon on 2014-08-25
So I was messing around with compizconfig settings manager tryin to set difderent wallpapers on my dual monitors. However during this I accidentally disabled the desktop wall itself and now when I boot up its just a black screen. It still gives me the notification tht im connected to wifi but I cant figure out what to do. Im not very experienced with ubuntu and I really need help.

---

### Post by deadflowr on 2014-08-25
Your best bet is reset
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by riley_mcmahon on 2014-08-25
How am I suppose to launch terminal? Everythings black...just my cursor

---

### Post by riley_mcmahon on 2014-08-25
Ctrl + alt + T isnt working either

---

### Post by mc4man on 2014-08-25
Try - 
ctrl+alt+F3
Then login with username & password, run the command
(just -  dconf reset -f /org/compiz/
At that point while ctrl+alt+F7 will return you to desktop I'd just do a reboot instead with 
sudo reboot

If you boot up to the greeter/log in screen then do the above, (ctrl+alt+F3, login, command, reboot)  from there instead of logging in normally

---

### Post by riley_mcmahon on 2014-08-25
Im confused how to enter the command. But ctrl+alt+f3 worked and I logged in but I must be messing up on the command

---

### Post by deadflowr on 2014-08-26
> **riley_mcmahon said:**
> Im confused how to enter the command. But ctrl+alt+f3 worked and I logged in but I must be messing up on the command

what are you typing?
```
dconf reset -f /org/compiz/
```
is all you should need to type. 
as per mc4man's advice:
```
sudo reboot
```
will reboot the machine.

Is it having no effect?
or is it giving out weird error messages, or something?

---

### Post by riley_mcmahon on 2014-08-26
When I put the code in it says:
Error: cannot autolaunch D-bus without  $Display
Usage: dconf reset [-f] path
Reset a key or dir. -f is required for dirs.
Arguments:
PATH   either a key or dir
KEY      a key path (starting, but not ending with '/'
DIR       a directory path (starting and ending with '/

---

### Post by mc4man on 2014-08-26
It appears you can't reset dconf from a tty. If you search the error you'll probably find some convoluted workarounds that may or may not work out
(search Error: cannot autolaunch D-bus without $Display

Otherwise you could try 'resetting' most all your current gsettings by getting a new, default  user file
To try - 
boot up
Preferably at login screen go ctrl+alt+F3
login with username & password

Then run this, copy carefully, note there is a . (period) before config, ie. the folder is .config
```
mv .config/dconf/user .config/dconf/user.bak
```
```
sudo reboot
```

---

### Post by riley_mcmahon on 2014-08-26
Tht managed to help slighty by turning my background purple but I still have no desktop

---

### Post by mc4man on 2014-08-26
Well then your issue may extend beyond some compiz setting. To test - 
If you boot to the login screen then try logging inti a Guest session, see if it works ok

---

