---
title: "Trying to run GUI over ssh"
date: 2015-01-31
forum: General Help
---

### Post by lsutiger on 2015-01-31
I recently upgraded my office computer from 10.04 to 14.04. I used to be able to run GUI apps over ssh (form home to office), but I can not longer do so. 
I would ssh -XC user@domain, then run the command (mostly being tsclient).
Now when I try to run a program, I get errors 
At first I was getting the error form remmina:
(remmina:22832): Gtk-WARNING **: cannot open display: 
So I would set the display with:
export DISPLAY=:0.0
Now I am getting the error:
(remmina:22837): libappindicator-WARNING **: Unable to get the session bus: Could not connect: Connection refused

(remmina:22837): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: Could not connect: Connection refused

I am using Gnome Flashback as the desktop on the server computer.

I tried using NoMachine, but the I can not get the resolution correct and it is impossible to work with.

So help with either of these would be appreciated.


UPDATE: I changed owner of the .dbus file to my user from root. I no longer get the error, but the app never appears. Could it be the incorrect export DISPLAY=:0:0?

---

### Post by TheFu on 2015-01-31
You don't need to set the DISPLAY when using -X with ssh.  ssh does the right thing automatically. You cannot set the DISPLAY to :0 --- that is localhost and when you are trying to run remotely, that most definitely is NOT the correct answer.

I'd guess that the server ssh settings don't allow X-forwarding. Check that first.
[http://itg.chem.indiana.edu/inc/wiki/software/openssh/200.html](http://itg.chem.indiana.edu/inc/wiki/software/openssh/200.html) has more details.
```
X11Forwarding yes
X11DisplayOffset 10

```are the settings in the sshd_config file to check.

I assume you can ssh fine - no gui, correct?

---

### Post by lsutiger on 2015-01-31
Those items were set. I can ssh without any problem.  
I used to be able to do this, but now can't. $DISPLAY variable isn't set to anything...hmm

---

