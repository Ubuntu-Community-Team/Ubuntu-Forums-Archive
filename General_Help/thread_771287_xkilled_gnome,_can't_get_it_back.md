---
title: "xkilled gnome, can't get it back"
date: 2008-04-27
forum: General Help
---

### Post by CorruptNoob on 2008-04-27
Hi I was demonstrating xkill and killed my gnome now can't get it back :D how do I do it? I've got terminal up

---

### Post by kavon89 on 2008-04-27
```
sudo /etc/init.d/gdm start
```

That should do the trick.

---

### Post by CorruptNoob on 2008-04-27
it's still dead..

* Starting GNOME Display Manager...                                     [ OK ]

---

### Post by kavon89 on 2008-04-27
> **CorruptNoob said:**
> it's still dead..

* Starting GNOME Display Manager...                                     [ OK ]

Hmm, do you remember what you xkilled, or what command you used before gnome stopped?

Try maybe... 

```
startx
```

---

### Post by CorruptNoob on 2008-04-27
I did sudo startx 

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.




I killed the top bar (where the applications, places, etc are)

---

### Post by kavon89 on 2008-04-27
Try Ctrl+Alt+F7, it should return you to x since it seems to already be started.

---

### Post by CorruptNoob on 2008-04-27
ctrl alt + f7 doesn't do anything :(

---

### Post by kavon89 on 2008-04-27
> **CorruptNoob said:**
> ctrl alt + f7 doesn't do anything :(

Well, I'm out of ideas... I'll let a more experienced person chime in.

I would suggest restarting the computer as a last option.

```
sudo reboot
```

---

### Post by meanburrito920 on 2008-04-27
try top or ps to find out what the PID of your xserver is, then kill it and use startx.

---

### Post by meanburrito920 on 2008-04-27
wait, I just read through your posts again and you said you killed the gnome-panel. is that all you xkilled? or did you actually bring down gnome and are in a tty terminal right now? if you still see your desktop background you can just enter 'gnome-panel' into the terminal. otherwise follow the instructions it gave you and remove /tmp/.XO-lock. Have you tried that yet?

---

### Post by CorruptNoob on 2008-04-27
I just got rid of the panel, I can see my desktop right now, I've got it to saved my session and restore it every time I reboot so rebooting does nothing! help! gnome-panel fixed it

---

