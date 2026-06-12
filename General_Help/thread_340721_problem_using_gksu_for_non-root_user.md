---
title: "problem using gksu for non-root user"
date: 2007-01-17
forum: General Help
---

### Post by abc_user on 2007-01-17
Trying to use gksu to open a gui app as another user. This works for root, but not for another user. I used to use gksuexec but that isn't available in 6.10. The -d option shows that it is trying to open the app but gets X errors. I also notice that it asks for my password while gksuexec used to ask for the other user's password. Any help?

Here is an example with the -d flag on.

[INDENT]
jerry@localhost$ gksu -d -u ben xterm
No ask_pass set, using default!
xauth: /tmp/libgksu-HSejBT/.Xauthority
STARTUP_ID: (null)
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: ben
cmd[7]: --
cmd[8]: xterm
buffer: -GNOME_SUDO_PASS-
Yeah, we're in...
Xlib: No protocol specified

xterm Xt error: Can't open display: :0.0
xauth: /tmp/libgksu-HSejBT/.Xauthority
xauth_env: /home/jerry/.Xauthority
dir: /tmp/libgksu-HSejBT
[/INDENT]

---

### Post by Stemp on 2007-01-17
why aren't you using gksudo ? (or even sudo)

---

### Post by abc_user on 2007-01-17
Because I'm trying to run as another regular user, not the super user.  Per your suggestion I tried it with gksudo and it seems to have the same problem.

---

### Post by Stemp on 2007-01-17
Sorry I didn't understood your need.

Well, I tried your command and I have the same problem.

```
cmd[8]: xterm
buffer: -GNOME_SUDO_PASS-
Yeah, we're in...
Xlib: No protocol specified

xterm Xt error: Can't open display: :0.0
xauth: /tmp/libgksu-0yGUMm/.Xauthority
xauth_env: /home/stemp/.Xauthority
dir: /tmp/libgksu-0yGUMm
```

---

### Post by abc_user on 2007-01-18
Thanks for the confirmation Stemp.  Moving forward.

a) Is there another way to run a gui from user_b in user_a's session?  I've tried using su to get a shell as user_b and start the app, but always run into the same X windows problems.  Tried doing xhost + localhost and such, but am stumped at this point.  Is there a way to get it to work "manually" or is there another gksuexec like app I can use?

b) Is this gksu problem a bug that should be reported?  Are other people having the same problem?

---

### Post by jbus on 2007-01-18
Sorry for asking, but I'm curious.  Why would you need run an app with gksu in this manner, as another non-root user?

---

### Post by abc_user on 2007-01-18
Jbus, various reasons.  It is often just more convenient to open up an app quickly without switching users, or to have one going as user_b while working primarily as user_a.

I took a quick look at the bug database and found these related bug reports.
Bug #47388 - this seems to hit the same problem.
Bugs #26291, #23917, #58704 may also be related.

#26291 mentions a package called "sux" which I couldn't find in Synaptic, anyone know anything about it?

---

### Post by abc_user on 2007-01-18
Here are links to the bugs

[#47388]("https://launchpad.net/ubuntu/+source/gksu/+bug/47388")
[#26291]("https://launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/26291")
[#23917]("https://launchpad.net/ubuntu/+source/gksu/+bug/23917")
[#58704]("https://launchpad.net/ubuntu/+source/gksu/+bug/58704")

---

### Post by jbus on 2007-01-19
> **abc_user said:**
> 
#26291 mentions a package called "sux" which I couldn't find in Synaptic, anyone know anything about it?

Sux is in edgy universe.

---

### Post by gradstudent on 2007-03-28
I was wondering if this problem has been solved?
I am getting the same error (although I am doing something slightly different)
Running strace showed me that the connection to /tmp/.X11-unix/X0 is being refused, but I don't know why. 
How did you solve the problem? sux does not solve it for me.

Thanks

---

### Post by Stemp on 2007-03-28
Still the same bug in Feisty.

---

