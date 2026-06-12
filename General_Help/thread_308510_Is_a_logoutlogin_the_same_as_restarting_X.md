---
title: "Is a logout/login the same as restarting X?"
date: 2006-11-28
forum: General Help
---

### Post by richardq on 2006-11-28
I'm a pseudo-newbie and I have a quick question:

Almost every time I try to restart x with Ctrl-Alt-Backspace it closes X and goes back to the GDM login screen. But when I log in again it never gets back to the desktop. Just a blank light blue screen with full mouse movement but no desktop. Another Ctrl-Alt-Backspace will only bring me back to the login screen again. I end up having to reboot.

The above behaviour is the same whether I'm running Beryl or Metacity.

Does logging out and then logging in again accomplish the same thing (restarting X)? Because that seems to work no problem. It's only the Ctrl-Alt-Backspace method that seems to hang it so to speak.

I'm running Edgy with Gnome and Beryl. I ran into this repeatedly when getting my Graphire Tablet up and running. I ended up having to reboot to get changes to my xorg.conf file to 'take'.

Is there some other way to restart X without rebooting?

---

### Post by David Marrs on 2006-11-28
Hmm, that's not usual behaviour. I suspect it will be something to do with beryl, which is still new software and (from what I've heard) rather buggy. Logging out and in again certainly seems to be the same as ctrl-alt-bksp, but I don't know if is or not. However, if I find the need to restart my session, I just use that key combo as a quick shortcut.

---

### Post by xopher on 2006-11-28
> **richardq said:**
> 
Is there some other way to restart X without rebooting?

Go to a tty (CTRL+ALT+F1..F6) log in and issue:

```
sudo invoke-rc.d gdm restart
```

restart to restart X and gdm
start to start
stop to stop

Simple? ;)

---

### Post by jazzgossen on 2006-11-28
Logging out does not restart X. To restart X you have to ctrl+alt+backspace or "sudo killall gdm", for example. Conversely though, killing X will log out all users who have logged in through GDM. 

I have no idea why the blue desktop thing is happening when you restart X.

---

