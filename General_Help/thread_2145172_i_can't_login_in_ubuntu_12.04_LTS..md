---
title: "i can't login in ubuntu 12.04 LTS."
date: 2013-05-14
forum: General Help
---

### Post by alpimj on 2013-05-14
i can't login with the correct password in ubuntu desktop. i cant get through. it keeps me back in to login page when I try to login  correctly. please help me. what am i gonna suppose do to?

---

### Post by alpimj on 2013-05-14
[COLOR=#000000]i can't login with the correct password in ubuntu desktop. i cant get through. it keeps me back in to login page when I try to login correctly. please help me. what am i gonna suppose do to?[/COLOR]

---

### Post by JnPson on 2013-05-14
What account are you using?
If your'e trying to login with root you can't. root is disabled by default, you have to login using the account you created during install.

---

### Post by matt_symes on 2013-05-14
**Threads merged.**

Please don't create multiple threads on the same subject.

It dilutes community effort and creates work for staff.

---

### Post by TheFu on 2013-05-14
If you cannot login using the same account created during the installation, then you have a few choices.
a) reinstall, noting the userid and password carefully this time
b) some easy hacking of the password and shadow password files using a LiveCD. This method is very fast for someone already familar with the shell and CLI, but for someone used to point-n-click, it is likely too complex. [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/) provides instructions.
c) Find a Linux password-reset tool and use it.  Looks like this method [http://naveenubuntu.blogspot.com/2012/05/recover-login-password-of-ubuntu-1204.html](http://naveenubuntu.blogspot.com/2012/05/recover-login-password-of-ubuntu-1204.html) makes resetting a password trivial.

**I would try option C first.** That appears to be trivial, if it actually works. It also points out a huge security problem wiht default Ubuntu installs. Physical computer access means complete access.

---

### Post by matt_symes on 2013-05-14
Hi

> **alpimj said:**
> i can't login with the correct password in ubuntu desktop. i cant get through. it keeps me back in to login page when I try to login  correctly. please help me. what am i gonna suppose do to?

When did this start happening ?

In the session before it happened, did you install graphics drivers, any other software or have a software update ?

Are you getting any message telling you the password is incorrect ?

It sounds like X windows may be crashing.

Kind regards

---

### Post by Bashing-om on 2013-05-14
Guys; 'nother thought;

Have the permissions on the .ICEauthority or .Xauthority files changed ? Could be the cause if these files are no longer owned by <the user> account. Easy enough to check:

1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
Terminal Code:
```
ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
Terminal Code:
```
sudo chown USERNAME:USERNAME .ICEauthority
```
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
If it worked, see here about a possible cause:
[URL="http://www.psychocats.net/ubuntu/graphicalsudo"]http://www.psychocats.net/ubuntu/graphicalsudo


better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

[/URL][INDENT=2]
hope this helps

[/INDENT]

---

### Post by TheFu on 2013-05-15
~/.ICEauthority and ~/.Xauthority can be deleted safely when you aren't running X ... or just before logout. They will be recreated as needed.

The only time I've needed to remove those were after I started X/Windows from a different account by my $HOME was not reset for the other account.  Basically, it is when **sudo** gets used when it shouldn't.

---

### Post by zombifier25 on 2013-05-15
> **Bashing-om said:**
> Guys; 'nother thought;

Have the permissions on the .ICEauthority or .Xauthority files changed ? Could be the cause if these files are no longer owned by <the user> account. Easy enough to check:

1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
Terminal Code:
```
ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
Terminal Code:
```
sudo chown USERNAME:USERNAME .ICEauthority
```
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
If it worked, see here about a possible cause:
[URL="http://www.psychocats.net/ubuntu/graphicalsudo"]http://www.psychocats.net/ubuntu/graphicalsudo


better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

[/URL][INDENT=2]
hope this helps

[/INDENT]

Seconded. About 8 out 9 times I encountered the error was due to the permissions of those files. Worth fixing them before going nuclear.

---

### Post by alpimj on 2013-05-15
> **Bashing-om said:**
> Guys; 'nother thought;

Have the permissions on the .ICEauthority or .Xauthority files changed ? Could be the cause if these files are no longer owned by <the user> account. Easy enough to check:

1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
Terminal Code:
```
ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
Terminal Code:
```
sudo chown USERNAME:USERNAME .ICEauthority
```
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
If it worked, see here about a possible cause:
[URL="http://www.psychocats.net/ubuntu/graphicalsudo"]http://www.psychocats.net/ubuntu/graphicalsudo


better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

[/URL][INDENT=2]
hope this helps

[/INDENT]





it didn't work

---

### Post by alpimj on 2013-05-15
> **matt_symes said:**
> Hi



When did this start happening ?

In the session before it happened, did you install graphics drivers, any other software or have a software update ?

Are you getting any message telling you the password is incorrect ?

It sounds like X windows may be crashing.

Kind regards
it started when my desktop hanged. when i forced to shutdown, and try to login, that is the time that  i cant log in but i input the correct password

---

### Post by linuxvstheworld on 2013-05-15
I have an idea. If you have any files that you need to retrieve, I recommend that you boot up via a live cd and retrieve the files if possible, then do a reinstall, I've heard that can work, it would show the hard drive as a mounted disk.

EDIT regarding your newest post: If you can login via terminal successfully (implying that's possible), then it may be a GUI issue.

---

### Post by alpimj on 2013-05-15
> **linuxvstheworld said:**
> I have an idea. If you have any files that you need to retrieve, I recommend that you boot up via a live cd and retrieve the files if possible, then do a reinstall, I've heard that can work, it would show the hard drive as a mounted disk.

EDIT regarding your newest post: If you can login via terminal successfully (implying that's possible), then it may be a GUI issue.


i login successfully in terminal when i type "ctrl+alt f1"

---

### Post by matt_symes on 2013-05-15
Hi

Login to a console (ctrl + atl + F1) and type

```
sudo apt-get install pastebinit
```

This will install paste bin and allow use to see your logs.

Then type

```
pastebinit /var/log/Xorg.0.log
```

Post the URL created back here and we can see your X log file.

Kind regards

---

### Post by walter3 on 2013-09-23
I have the same issue. I follow the pastebinit instructions and this is what I got:

[http://paste.ubuntu.com/6145216/](http://paste.ubuntu.com/6145216/)

Thanks in advance

---

### Post by Bashing-om on 2013-09-23
walter3 ; Hi ! Welcome to the forum .

I did not notice anything alarming in your output.

Let's back up to square one.
Can you log in from the text console (ctl+alt+f1 at the GUI login) ?
show the out put of terminal commands:
```

ls -al .ICEauthority
ls -al .Xauthority

```

[INDENT][INDENT]good as any place to start
[/INDENT][/INDENT]

---

### Post by walter3 on 2013-09-23
Hi Bashing-om! This is my first hard issue with Ubuntu since 2010...

I can login to TTY1. I can also login from the GUI to the Guest User, and I have created a new user, which also works in the GUI.

I have already tried to reassign the owner of .ICE and .X 

This is what I got:

-rwxrwxr-x 1 walter walter 27984 sep 15 14:34 .ICEauthority
-rw------- 1 walter walter 0 sep 23 21:50 .Xauthority

And again, thanks for your help (and sorry for using this old thread)

---

### Post by Bashing-om on 2013-09-23
walter3; Welp;

That do narrow things down to a config file, huh .
What version and distribution are you running ?
Have you tried resetting the desk top back to defaults ?

And let's see what is:
```

sudo ls -la /var/lib/lightdm

```
ownerships - "assuming" that is your DE

Lemme check ! Why is your .Xauthority file size "0" ?

Edit: File size "0" not as expected -> no cookies to authorize access. Do:
```

xauth list

```
to confirm.

When you get caught up to here, and ready to proceed, I may have an easy solution.

[INDENT][INDENT]I be look'n
[/INDENT][/INDENT]

---

### Post by walter3 on 2013-10-06
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

I try to reset trough unity --reset from tty1, but it failed. Errors from D-Bus daemon (no protocol) and X11 initialization. Should I run this from the other session I've created?

Results from lightdm 
> total 48
drwxr-x--- 10 lightdm lightdm 4096 oct  6 09:55 .
drwxr-xr-x 71 root    root    4096 nov 20  2012 ..
drwx------  5 lightdm lightdm 4096 may 27  2012 .cache
drwx------  4 lightdm lightdm 4096 nov 11  2011 .config
drwx------  3 lightdm lightdm 4096 nov 11  2011 .dbus
-rw-------  1 lightdm lightdm   16 nov 11  2011 .esd_auth
drwx------  2 lightdm lightdm 4096 oct  6 09:55 .gconf
d?????????  ? ?       ?          ?            ? .gvfs
drwxrwxr-x  3 lightdm lightdm 4096 nov 11  2011 .local
drwx------  3 lightdm lightdm 4096 may 27  2012 .nv
drwx------  2 lightdm lightdm 4096 oct  6 09:40 .pulse
-rw-------  1 lightdm lightdm  256 nov 11  2011 .pulse-cookie
-rw-------  1 lightdm lightdm   51 oct  6 09:55 .Xauthority

The xauth from the other session (I can't get this from the session with the issue): 
walter/unix:0  MIT-MAGIC-COOKIE-1  3125a9171a7f80d8d49be21193085df0

Thanks

---

