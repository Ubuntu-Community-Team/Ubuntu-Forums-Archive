---
title: "How can I auto login without auto logging in?"
date: 2006-08-13
forum: General Help
---

### Post by brundles on 2006-08-13
This forum has been a God send in setting up my shiny new Ubuntu distro - I used to use SuSE but have definitely been converted :D 

Anyway - enough rambling!

Basically, what I want to do is have a user automatically login on bootup and start a remote desktop (VNC) session. However I still want the bootup to finish on the login screen. Is this possible?

As a bit of background on why I want this... The PC is a desktop PC that's about to have it's insides relocated into an HTPC case. Eventually I want one user to login and startup Myth on bootup but I will still want the other user logged in with VNC running on it's desktop session running in the background.

Hope someone can help!

---

### Post by woifi on 2006-08-13
Hmm I think I do not exactly understand what you want but autologin can be configured easily with gdm.

hth

woifi

---

### Post by brundles on 2006-08-13
Thanks for the suggestion Wolfi- unfortunately that only does half of what I want.

Assume there are two users on the machine: User A and User B.

I want to have user B login automatically to their desktop (covered by your auto login suggestion) and User A login automatically and have their GNOME session running in the background so it can be VNC'd to while User B still "owns" the actual screen - or switch users to an already logged in User A.

---

### Post by sizzam on 2006-08-15
What I do to make sure that I always know the correct session to VNC into is this:

Automatically log in with **user 1**:
```

System > Administration > Login Window

Click Security.

Enable Automatic Login, choose **user 1**.

```

Then, while logged in as **user 1**, I add a command to lock the screen automatically when that user logs in.
```

System > Preferences > Sessions

Click 'Startup Programs'.

Add the following command:
gnome-screensaver-command --lock

```

So, now whenever Ubuntu starts, **user 1** logs in automatically and then the screen automatically locks.  Then, the next person moves the mouse and is greeted with the screen that gives them the option to enter a password or 'Switch User', which brings them back to the welcome screen.

This assures that **user 1**'s session is always available on VNC via port 5900.

Does this help?

---

### Post by sizzam on 2006-08-20
Actually, gnome-screensaver-command --lock doesn't work on startup from Sessions.

Anyone know what command you can added to System > Preferences > Sessions to lock your screen on login?

---

### Post by CheShA on 2007-09-10
old post, I know but for the record the command i think you want is 
```
gdmflexiserver
```

---

### Post by frafu on 2007-09-17
@brundles

If you install NX from nomachine.com, the remote user can open a second gnome session that is independent from the session of the local user. There is also an open source version similar to nx, called freenx, but I don't know how well it works; I am using the propriety free edition of nx from nomachine.com and it works quite well. 

Have a nice day. 

Francesco

---

### Post by chaeron on 2007-09-19
> **sizzam said:**
> Actually, gnome-screensaver-command --lock doesn't work on startup from Sessions.

Anyone know what command you can added to System > Preferences > Sessions to lock your screen on login?

The gnome-screensaver-command --lock doesn't work from Sessions on Feisty.  I just tried it.  Also tried running gnome-screensaver-command --lock from .bash_login, but that doesn't seem to work either.

Anyone figured out how to auto-login a user but then immediately lock the screen?

Thanks!

---

### Post by lavajumper on 2007-09-19
Just to throw in another couple of pennys, you may be able to make use of X virtual terminals. Something like starting one X session on VT7 and another one on VT8. I use this, allocating VT8 for my remote xdmcp sessions and VT7 for the console.

---

### Post by lavajumper on 2007-09-19
Here's a couple of things that might help:

1. You can't lock root's screen. The workaround requires more than just flipping a switch.
2. This worked for non-root users:

- create scr.sh in the users home dir, snippit below :

---Begin-------------

#!/bin/bash
/usr/bin/gnome-screensaver
sleep 2
/usr/bin/gnome-screensaver-command -l

---end----------------

- make it executable-  chmod 700 scr.sh
- launch scr.sh using the session startup stuff:

Goto System->Preferences->Sessions and make a new entry called  ZZscr (i couldn't find the spinny control the help screens talked about)

The command for the ZZscr is "/home/<username>/scr.sh or the pathname to scr.sh
Logoff and log back in as the user.

On my system, the screensaver process was not starting soon enough to issue gnome-screensaver-command signals from the "session startup" control.

If you find that other processes need more time to "catch up" try adding a sleep statement at the beginning of the scr.sh script.

Hope this helps, or at least points you in the right direction.

---

### Post by chaeron on 2007-09-19
Thanks javalumper...I'll give that a try!

---

### Post by chaeron on 2007-09-19
Worked like a charm.  I even took the sleep down to 1 second and it still works fine.

Thanks muchly!

---

### Post by mocoloco on 2007-09-19
> **frafu said:**
> @brundles

If you install NX from nomachine.com, the remote user can open a second gnome session that is independent from the session of the local user. There is also an open source version similar to nx, called freenx, but I don't know how well it works; I am using the propriety free edition of nx from nomachine.com and it works quite well. 

Have a nice day. 

Francesco

I would second this suggestion.  I've found NX to be much faster than VNC, and it doesn't require me to leave a session running, or tie up the machine like VNC.  The [freeNX]("https://help.ubuntu.com/community/FreeNX") server is easy to install, and I use the client from noMachine.

---

### Post by stupid_browner on 2008-05-27
I know this is an old forum but for future reference, sizzam's suggestion works in Hardy.
> **sizzam said:**
> What I do to make sure that I always know the correct session to VNC into is this:

Automatically log in with **user 1**:
```

System > Administration > Login Window

Click Security.

Enable Automatic Login, choose **user 1**.

```

Then, while logged in as **user 1**, I add a command to lock the screen automatically when that user logs in.
```

System > Preferences > Sessions

Click 'Startup Programs'.

Add the following command:
gnome-screensaver-command --lock

```

So, now whenever Ubuntu starts, **user 1** logs in automatically and then the screen automatically locks.  Then, the next person moves the mouse and is greeted with the screen that gives them the option to enter a password or 'Switch User', which brings them back to the welcome screen.

This assures that **user 1**'s session is always available on VNC via port 5900.

Does this help?

---

