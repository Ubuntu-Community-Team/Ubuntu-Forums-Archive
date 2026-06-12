---
title: "How to run a gui application as another user who is not admin"
date: 2007-07-16
forum: General Help
---

### Post by doyston on 2007-07-16
Hello

I'm new to Ubuntu so apologies if this is trivial or been answered before.

I want to run a gui application as another user, but am hitting Xlib protocol errors.  Using gksudo doesn't help.  Note that I do not know the password of the other user (who is an ordinary, non-admin user) but I have full admin rights.  I can login as the other user without problems via sudo in a terminal window, but then don't have the ability to launch X11 applications.

Many thanks.

---

### Post by grahams on 2007-07-16
try "sudo gksu" then select the user in the drop down list.  As you started gksu via sudo I don't think it will ask for a password.

---

### Post by doyston on 2007-07-17
Hello
Unfortunately it only works if I select user 'root' from the gksu window's drop-down box.  Nothing happens for an ordinary user.  If I try using

sudo gksudo

again it works fine if user 'root' is selected.  If an ordinary user is selected, and I try and run for example, xterm, for that user, the following message is issued:

No protocol specified
xterm Xt error: Can't open display: :0.0

---

### Post by testube_babies on 2007-07-17
There has to be a graphical way to do this that I don't know about, but here's how to do it from a terminal:

Switch to a different non-root user:
```
sudo -i -u username
```

From the terminal, you can then launch the applications you want.

---

### Post by grahams on 2007-07-18
I believe your being blocked by the default X access control (which is a good security thing). As root run "xhost +" and then try xterm again as the other user.

---

### Post by doyston on 2007-07-18
Hello testube_babies and grahams
Adding the -i flag in sudo, and xhost + did the trick!
Thank you

---

