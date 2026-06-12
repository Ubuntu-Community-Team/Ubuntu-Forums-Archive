---
title: "Login, X trouble - flailing."
date: 2020-01-08
forum: General Help
---

### Post by crackers_altitude on 2020-01-08
I thought I posted this earlier, but it seems it disappeared? Sorry about this:

The clearest statement of my symptom : login to the desktop works as expected, however, in about 2-3 seconds, the user (not root) seems to be kicked out to the login screen again.

some more info:

Ctrl-F1 or Ctrl-F3 can get the command line login up for the user. I can login, then `sudo startx`. Sometimes that works to get a desktop up, but leads to trouble, for example when starting Firefox. Also, seems the user is “root”, and this is just a mess.

There are no “EE” in the Xorg.0.log.
I tried moving the .Xauthority out.
I’m not sure what to look for in grub or elsewhere.

I expect my dabbling with installing wine and some other python-related items is the cause of this. Apt-get update has been done enough that there are zero new or updated packages.

I’d like to avoid reinstalling the OS. Maybe updating to 19 would make this go away.

Ubuntu version 18.0.4

Apologies for the poor clarity of the description. Thanks for any guidance.

---

### Post by dragonfly41 on 2020-01-08
I can only intuitively suggest an approach I would try in these circumstances (not from any direct experience).

If you can get into a stable desktop position can you create a new user account to see if these symptoms carry into the new user profile after reboot.

---

### Post by crackers_altitude on 2020-01-10
Made a new user account. Went OK until I starting Firefox. GUI never appeared. System seemed to freeze or slow way down.... and now it is frozen, can’t Ctrl-Alt-Del or use ctrl-alt-F[1-3].

---

### Post by crackers_altitude on 2020-01-10
... (ongoing work updated as I try to solve this)...

Ctrl-Alt-F1 (or was it F3? Pretty sure F3, not F1) login ok, ‘startx’ as the test user ok, Firefox ok... use plain old login screen, also OK...  looking like my own account contains the problem....

Doing ‘Switch user’ produces the same problem - the Desktop shows up (but with a black background, and only the Trash icon), and rapidly kicks the session out (logout, i guess), to the plain old login screen.

My own account: try C-A-F3 login, works. However, ‘startx’ fails, producing error (updated post-facto):

“xauth: timeout in locking authority file /home/myownuser/.Xauthority.”

oh no - the screen went black, pointer is frozen. Ctrl-Alt-F1 gets back to the plain old login screen...(I will try to put the error output above if I see it again)....

Eventually I get a Desktop session using the test user. I can see different .Xauthority files, with “-l” or “-c” appended to them. Also, .x-session-errors and .Xauthority were owned by root - my fault. Moved them out, but still getting kicked out. It appears that no new .x-session-errors or .Xauthority files are being written after doing this. Finally get to ‘startx’ as my own user, and I get a stable Desktop. But cannot get there from login screen where the mouse pointer can click on the users.

And now a new clue :

“Enter password to unlock your login ... The login keyring did not get unlocked when you logged into your computer”

It keeps coming up every time the Desktop (or ‘startx’) comes up.... or.... no, it’s only with Google Chrome!... ok, leaving that aside... [Googles this problem]... you know, this might be the reason.. 

Ok, so I have a lead of some sort. Apologies for the dramatic moment-to-moment post.

---

### Post by crackers_altitude on 2020-01-14
should anything in a users's .cache be owned by root?

because during some backups, I noticed .cache/gnome-shell and .cache/dconf were owned by root.

---

### Post by Impavidus on 2020-01-15
> **crackers_altitude said:**
> 
I’d like to avoid reinstalling the OS. Maybe updating to 19 would make this go away.
It won't. Release upgrades don't fix problems; they make them worse.

The only exception is when a problem is caused by incompatible hardware and a more recent kernel fixes it, but that's not the case here.
> **crackers_altitude said:**
> should anything in a users's .cache be owned by root?

because during some backups, I noticed .cache/gnome-shell and .cache/dconf were owned by root.

Nothing in your home directory should be owned by root. Everything should be owned by you.

It's a common mistake amongst new Ubuntu users. Misusing sudo can lead to root-owned files in your home directory in places you don't expect, like configuration files and cache files written whilst you were editing something else. These root-owned files cause problems, which can be circumvented by using more sudo. People get "Permission denied" and think "Maybe sudo helps." Indeed it does, but it makes the problem worse. That's why people should only use sudo when they know why they need it.

Anyway, one thing you can try to solve this is a recursive chown:```
sudo  chown  -R  username:username  /home/username
```Substitute your username. Be careful. Make sure you get all the spaces right. Single spaces are enough, but I used double spaces so you can see them more easely. A recursive chown on the wrong directory will destroy your system.

But you shouldn't be scared of a fresh install.

---

### Post by crackers_altitude on 2020-01-15
thank you Impavidus. as I work to solve this, I will put notes here. 

first, the two directories in this discussion so far : 

```

sudo ls -ltraF dconf/ ; sudo ls -ltraF gnome-shell/
total 12
drwx------  2 root   root   4096 Jan 10 12:03 ./
-rw-------  1 root   root      2 Jan 10 12:04 user
drwx------ 30 myusername myusername 4096 Jan 11 11:24 ../
total 20
drwx------  2 root   root   4096 Jan  8 10:37 runtime-state-LE.:0/
drwx------  2 root   root   4096 Jan  8 10:54 runtime-state-LE.:1/
drwx------  5 root   root   4096 Jan 10 11:41 ./
drwx------  2 root   root   4096 Jan 10 12:04 runtime-state-LE.:2/
drwx------ 30 myusername myusername 4096 Jan 11 11:24 ../

```

can any of these things be simply removed and then get re-written by myusername at next login?

I looked around for more root-owned things with ```
ls -ltraFR | grep " root "
```, and sure enough, there are files and hidden directories in particular that have "Permission denied" on them. including .dbus - that doesn't sound good to me.

I have to think about how to do this, but in the meantime, I'm posting this as a sort of problem-solving log...

---

### Post by Impavidus on 2020-01-15
It seems to be quite a mess, like a lot of things have been done with sudo that shouldn't. A recursive chown on your home directory as described in my previous post won't harm and may fix some things. I don't know a lot about the internals of dconf, dbus and gnome-shell.

---

### Post by crackers_altitude on 2020-01-15
OK - well, I did chown and chgrp on a few things, and the user still gets kicked out of the Desktop after about 1-3 seconds, then has to use Ctrl-Alt-F3 to get in. I'll see what else turns up...

---

### Post by crackers_altitude on 2020-01-16
tried some more things :

moved .Xauthority, .xsession-errors, .ICEauthority, .bashrc, .sudo_as_admin_successful out of the home directory and renamed them. got fresh .bashrc from a test user account. logout/login : same result (have to use Ctrl-Alt-F3 to get in, then as myusername (NOT SUDO) run startx. Desktop comes up ok.

some more internet searching with "ubuntu user login desktop kicked off" turned up useful pages (but no solution I can see), for instance :  

[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

and I note that I am using plain Nvidia drivers with an Nvidia card - that is, not the proprietary driver. glxgears works fine. There are no errors ("EE") in the Xorg.0.log.

---

### Post by crackers_altitude on 2020-01-22
one more clue surfaces :

~/.local/share contains :

-rw-r--r--  1 root   root      76 Jan  4 15:24 session_migration-(null)

... gotta work on this later.

---

### Post by Impavidus on 2020-01-23
Is that a new root-owned file in your home directory or are you trying to hunt them down one by one?

They seem to be all over the place. A recursive chown as described earlier should fix all of them at once.

---

### Post by crackers_altitude on 2020-01-23
notwithstanding - did a chown/chgrp on it. we'll see what happens.

---

### Post by crackers_altitude on 2020-01-25
I SOLVED IT!!

gnome-session-properties

[ uncheck the "System Load Indicator" ]

---

