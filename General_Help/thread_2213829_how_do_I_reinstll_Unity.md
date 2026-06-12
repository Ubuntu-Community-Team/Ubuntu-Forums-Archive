---
title: "how do I reinstll Unity"
date: 2014-03-28
forum: General Help
---

### Post by bigbill on 2014-03-28
I am running Ubuntu 13.04 I went into the software center and removed Unity. Now on the reboot all I have is my wallpaper. Can I reinstall Unity?

---

### Post by Bashing-om on 2014-03-28
bigbill; Hello,

Somewhat tall order,
13.04 has reached End Of Life - no longer supported - and "that" software repository no longer exist.
The recommended solution is to upgrade to a current release.


One must keep up
[INDENT][INDENT]to keep keepn' on
[/INDENT][/INDENT]

---

### Post by bigbill on 2014-03-30
Thank You for your reply Bashing-om
I have a correction to my post, I am running 13.10 not 13.04. Isn't there a way to repair the OS?

---

### Post by grahammechanical on 2014-03-30
You can try

1) At the Grub menu select Advance Options for Ubuntu
2) At the Advanced Options sub-menu select Recovery Mode
3) At the Recovery menu select Network
4) When back at the Recovery menu select Root
5) Run

```
apt-get install unity
```

6) Type exit to get out of the Root session and back to the Recovery menu.
7) Select Resume. That should get you to a desktop and fingers-crossed with Unity but using a fall back video driver.
8) Reboot.

Regards.

---

### Post by bigbill on 2014-03-30
Thank You grahammechanica for your reply,
I did your suggestion but came up with this error

W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt/
E: the package lists or status file could not be parsed or opened

I also tried "sudo apt-get install unity"

regards  Bill

---

### Post by steeldriver on 2014-03-30
The filesystem is mounted read-only in recovery mode; try executing

```
mount -o remount,rw /
```

before the apt-get command (note there is no space between the remount,rw options).

---

### Post by deadflowr on 2014-03-30
If getting it to work with recovery mode is daunting, then try simply booting up till you get to the login screen and press
```
ctrl+alt+F1
```
to get to tty1.
From here login as you would normally
Name
Password
Then run the apt-get commands.

The thing about recovery mode is it starts up with networking disabled.
Hence the reason to go to Networking before entering the root session.

The method I posted should have all that ready to go.

If the commands run without problems then try
```
sudo restart lightdm
```
This should bring you back to the login screen.
See if that helps.

If it does, then go back to ctrl+alt+F1 and type "exit" and hit enter.
Then press ctrl+alt+F7 to get back to the desktop.

---

### Post by grumblebum2 on 2014-03-30
I might recommend here, that when you're back up and running to install something like
**synapse** or **kupfer** so you can still launch applications when you have no unity interface.
Even the **easystrokes** mouse gestures application where you can set gestures to open a terminal or reset and reload unity
can simplify some recoveries.

---

### Post by bigbill on 2014-03-31
HI again,
I did the above suggestions and still not working.  I did receive a message after running this twice "apt-get install unity". It said that I have the latest version installed I just need to know how to turn it on.

Thanks again for your time and suggestions.
Bill

---

### Post by steeldriver on 2014-03-31
maybe you need to **reset **it?

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by grumblebum2 on 2014-03-31
If you can get to the desktop and open a terminal with ctrl+alt+t run this command....
```
dconf reset -f /org/compiz/ && setsid unity
```
Leave the terminal open and let it run for at least 30 secs.

If you can only log in using ctrl+alt+f1 ...just run ...
```
dconf reset -f /org/compiz/
```
and then try to login normally.

---

### Post by Bashing-om on 2014-04-01
grumblebum2; Hey;

We are hangn' with you. Awaiting results from the last postings, before suggesting other options.

[INDENT]where there is a will there is a way
[/INDENT]

---

### Post by bigbill on 2014-04-07
My apologies for not responding sooner I have been away. I did try the website suggested by steeldriver to no avail. I will try your suggestion grumblebum2 tonight.

 Thanks again for your efforts to help me.
Bill

---

### Post by bigbill on 2014-04-08
Hi to all.
grumblebum2 I entered the suggested code and got an error message stating -f needs a path.
I don't know what to do now?

reguards
Bill

---

### Post by grumblebum2 on 2014-04-08
> **bigbill said:**
> Hi to all.
grumblebum2 I entered the suggested code and got an error message stating -f needs a path.
I don't know what to do now?

reguards
Bill

Check you entered code correctly observing spaces.
```
dconf reset -f /org/compiz/
```

---

### Post by bigbill on 2014-04-13
Hi to all
This is the error that I get when I enter  dconf reset -f /org/compiz/

ERROR:ERROR spawnung command line 'dbus-launch  --autolaunch-3e14637d742e3d6871e 9613f51bfc7dfc7df--binary-syntax--close-std err' :child process exited with code 1
Usage: dconf reset [-f] path

I hope this helps to solve the problem.
This is a dual boot computer, so if I can't get Unity to work I am thinking of booting from the CD and taking the files that I need and just reinstall Ubuntu.

Thanks again for your help

Bigbill

---

### Post by grumblebum2 on 2014-04-13
Try reinstalling the default components of ubuntu.
```
sudo apt-get install --reinstall ubuntu-desktop
```

Then try dconf command again.
No luck...it's often easier to backup and reinstall.
You need to take care with what you uninstall and would recommend to 
use synaptic as it shows you dependent packages to be also removed.
Don't understand why you would install ubuntu and then remove unity.

---

### Post by steeldriver on 2014-04-13
It looks like you tried to run the dconf reset from outside the GUI desktop (e.g. from a Ctrl-Alt-Fn virtual terminal) - in that case I think you need to tell it about the X session else it tries to spawn its own dbus instance (and fails with the message that you noted). 

It's usually sufficient to set the DISPLAY variable I think i.e.

```
**DISPLAY=:0** dconf reset -f /org/compiz/
```

---

### Post by bigbill on 2014-04-13
Hi to all,
I finally got it.

here is what I did.

boot normal
I entered Alt,Contrl,F1
sign up screen entered name and password
I entered sudo apt-get install --reinstall ubuntu-desktop
it down loaded and installed something but did not change my screen
then I rebooted

Boot normal
I came up with my wallpaper, nothing else.
I did Alt,Contrl, F1
sign up screen, entered name and passwprd
I entered    DISPLAY=0 dconf reset -f/org/compiz/ && setsid unity
I did Alt,Cntrl,F7
The screen came up with the side bar but not the top bar.
I rebooted and the desktop came up normal and complete

Thanks to all for your help and patience in solving my problem.

---

### Post by Bashing-om on 2014-04-13
@ bigbill; Outstanding.

Persistence pays off again ! Pleased you sorted through it and provided the steps to resolution. Will surely aid others (hey I am one of those others).

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by grumblebum2 on 2014-04-13
> **bigbill said:**
> Hi to all,
I finally got it.

here is what I did.

boot normal
I entered Alt,Contrl,F1
sign up screen entered name and password
I entered sudo apt-get install --reinstall ubuntu-desktop
it down loaded and installed something but did not change my screen
then I rebooted

Boot normal
I came up with my wallpaper, nothing else.
I did Alt,Contrl, F1
sign up screen, entered name and passwprd
I entered    DISPLAY=0 dconf reset -f/org/compiz/ && setsid unity
I did Alt,Cntrl,F7
The screen came up with the side bar but not the top bar.
I rebooted and the desktop came up normal and complete

Thanks to all for your help and patience in solving my problem.
Good to see.
Where do we send our big bill to? :p

---

