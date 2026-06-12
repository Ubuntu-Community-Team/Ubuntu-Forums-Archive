---
title: "Cannot log in via main login GUI, but can via Terminal"
date: 2014-06-04
forum: General Help
---

### Post by Rocket J Squirrel on 2014-06-04
I'm the administrator of a 12.04 computer we use as a file server. Last week I could no longer log into that account using the main graphic login screen, but I can log into other accounts. What happens is when I select the username ("sysadmin"), put in the password, and hit return, the screen goes black for a few seconds -- except the cursor is still visible -- then it dumps me back into the login screen. If I purposefully mistype the password, I am told that the password is incorrect. This with Ubuntu's Unity or the LXDE environment.

However, if I log into another user account and enter "su sysadmin" into Terminal, it prompts for password, I put in the password, and I can switch to the sysadmin account there. So the account is working. But of course the GUI / Desktop, etc. are still the other account. I can also login via PuTTY. 

This problem persists after a reboot, too.

So what gives here? It's like Ubuntu can't load the desktop for the sysadmin account.

---

### Post by steeldriver on 2014-06-04
[LIST]
[*]is the sysadmin user's account writeable? are its $HOME/.Xauthority owned and writeable by sysadmin?
[*]does the user's default desktop session exist (in /usr/share/xsessions)? have you tried selecting a different session from the login screen menu?
[/LIST]

---

### Post by Rocket J Squirrel on 2014-06-09
Thank you.

"is the sysadmin user's account writeable?"

I don't know what that means. The sysadmin's /home folder is writeable:

```
sysadmin@CCD-6-Linux:/home$ ls -l
drwxr-xr-x 25 sysadmin    sysadmin    4096 Jun  2 14:56 sysadmin

```

"are its $HOME/.Xauthority owned and writeable by sysadmin?"

No -- this is strange:

```
sysadmin@CCD-6-Linux:~$ ls -la .X*
-rw------- 1 root root 168 May 22 11:37 .Xauthority
```

"does the user's default desktop session exist (in /usr/share/xsessions)?"

I normally use Lubuntu, but the problem exists with Ubuntu, and Gnome desktops. Here is /usr/share/xsessions:

```
sysadmin@CCD-6-Linux:/home$ ls /usr/share/xsessionsgnome.desktop        Lubuntu-Netbook.desktop  openbox-kde.desktop
gnome-shell.desktop  openbox.desktop          ubuntu-2d.desktop
Lubuntu.desktop      openbox-gnome.desktop    ubuntu.desktop
```

"have you tried selecting a different session from the login screen menu?"

If "sessions" means desktop environments, then yes. None work. 

So, let me try becoming root, and "chown sysadmin .Xauthority"

Okay, ownership changed. I'll Submit this reply, log out, and see if I can start a session.

---

### Post by Rocket J Squirrel on 2014-06-09
Okay, that didn't work. In fact it got worse: instead of bouncing me back to the main login screen it just takes me to a black screen and the monitor goes to sleep.

I PuTTY'd into the computer and re-started the main login screen with ```
sudo service lightdm restart
```

But I still be bounced back to the main login screen when I sign in.

Interestingly, the other users' .Xauthority are owned by them. Sysadmin's is not, it is owned by root. But changing ownership to sysadmin leads to a black screen when I log in from the main login screen. 

Anyway, still can't start a session for sysadmin.

---

