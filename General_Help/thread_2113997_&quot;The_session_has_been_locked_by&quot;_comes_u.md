---
title: "&quot;The session has been locked by&quot; comes up"
date: 2013-02-08
forum: General Help
---

### Post by gizmobay on 2013-02-08
I just upgraded my kubuntu 12.04 system today which is kde 4.10. My login manager is kdm. Now I always get a password prompt to unlock my desktop when kde goes into screen saver mode. I didn't have the issue until today's upgrade. Under System Settings -> Display I have Screen Locker set to start automatically after 2 minutes, require password is unchecked and screen locker type is set to screensaver which is set to blank. What am I missing?

---

### Post by gizmobay on 2013-02-19
bump. no one else see this

---

### Post by rnerwein on 2013-02-20
> **gizmobay said:**
> bump. no one else see this
hi
i am running 12.04 too and in system settings (my box is in german) i can find brightness and locking. just swicht the locking off and only the screensaver appears. but i am have the gnome desktop.
ciao

---

### Post by gizmobay on 2013-02-20
I have gnome installed but I'm not using it. The popup box does have that gnome feel to it. I also get the feel that something to do with gnome is running in the background even though I'm running kde.

---

### Post by r.stiltskin on 2013-02-21
You can easily find out everything that's running by running
```
$ ps -e
``` in a konsole window.  I wouldn't be surprised if you find nautilus and maybe also gnome-screensaver and gnome-session listed there.

In my recent experience, even though apt lets you install them side by side, gnome and kde (and xfce) don't really get along nicely together.  Recently I was experimenting with gnome because I was unhappy with some of kde's "features" and ended up with various things going wrong even when logged into a kubuntu session.  My kubuntu system didn't return to normal until I purged nearly all of gnome.

On another machine I was experimenting with xfce which I had added to a kubuntu installation, but couldn't get all of xfce to work correctly until I did a clean reinstall of xubuntu, and then added to that just the specific kde apps that I wanted and their dependencies (EXCLUDING kdm, kde-workspace, kde-window-manager and systemsettings for example).

I haven't figured out exactly which components were conflicting on either box.  I'm sure some experts know what to tweak to get everything working together but I think that most of us are better off sticking to one desktop at a time.

---

### Post by zero2xiii on 2013-02-21
> **gizmobay said:**
> I just upgraded my kubuntu 12.04 system today which is kde 4.10. My login manager is kdm. Now I always get a password prompt to unlock my desktop when kde goes into screen saver mode. I didn't have the issue until today's upgrade. Under System Settings -> Display I have Screen Locker set to start automatically after 2 minutes, require password is unchecked and screen locker type is set to screensaver which is set to blank. What am I missing?


Hay switch off the screen locker aswell.. The require password part is only if you have a passwordless login. This is how it works on my system. For users with passwordless login enabled you just hit enter at the lock screen, for users with password required you need to type the password even though the password required checkbox is unchecked.

Might also be a gnome thing getting in the way.. I have also noticed weird things happening when both run side by side.. Especialy if you swap between them during log on.. 

Also +1 for the "ps -e" comment. Just to make sure nothing is is there that shoudn't. Might I suggest going a step further in debugging the issue:
install htop "sudo apt-get install htop"
GUI login to the user/environment giving issues
ctrl + alt + F1 to a TTY loging
Log in as SAME user as GUI login
run "htop" in the TTY session
ctrl + alt + F5/6/7/8 back to your GUI
Wait for screen to lock
move mouse and make sure it asks for password (hit enter to see if it is passwordless login)
Now jump back to TTY1 (WITHOUT unlocking session)
Search (F3) for any gnome processes and kill them (espesialy the screen saver one)
Swap back to GUI and see if the unlock screen still apears and what the behavior is.

[EDIT]
Instead of htop you can try doing:
ps -e | grep gnome

Good luck.

---

### Post by gizmobay on 2013-02-21
I turned off the screen locker and then I lose the screensaver but it does prevent the unlock dialog box ;)

I checked to see if something to do with gnome is running and I didn't see anything that looked suspicious.

---

### Post by zero2xiii on 2013-02-21
Interesting,

Read through this post:
[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

It has some interesting options you might consider in your situation such as:
> lockTimeout (class Time) 
 	 If locking is enabled, this controls the length of the "grace period" between when the screensaver activates, and when the screen becomes locked. For example, if this is 5, and -timeout is 10, then after 10 minutes, the screen would blank. If there was user activity at 12 minutes, no password would be required to un-blank the screen. But, if there was user activity at 15 minutes or later (that is, -lock-timeout minutes after activation) then a password would be required. The default is 0, meaning that if locking is enabled, then a password will be required as soon as the screen blanks.

KDE never was the beter choice in my opinion between GNOME and KDE... it feels alot like iOS vs Android... GNOME being android in my opinion... When it comes down to the "but I want THIS to happen" stuff... KDE lacks the flexibilty... Might just be my bad experience.. But I am partial to gnome..

Good luck though. Maybe there is a MUCH simpler solution...

---

### Post by gizmobay on 2013-03-13
Must've been a bug as it works now.

---

