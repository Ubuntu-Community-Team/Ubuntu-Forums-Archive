---
title: "No login screen after reboot. [kubuntu]"
date: 2007-08-28
forum: General Help
---

### Post by Cleric. on 2007-08-28
I have quite a large problem. I was moving some things between two hard drives and Konqueror (I am running Kubuntu) stopped responding. So, I went for the GUI restart, but after the screen went black, nothing happened. So I restarted the machine, and now i get no login.

The "nvidia" screen comes up to show that the drivers are working, but nothing more.

If it matters, all I was running at the time was Compiz Fusion, Konqueror, and Firefox.

---

### Post by sumguy231 on 2007-08-28
Hit Ctrl+Alt+F1, log in, and type 
```
sudo /etc/init.d/kdm stop
```
HIt Ctrl+Alt+F1 again and type
```
sudo /etc/init.d/kdm start
```
What happens?

---

### Post by Cleric. on 2007-08-28
It sets me right back where I started: just a black screen.

I dunno if this will be of any help, but...
 I had noticed that, right before I tried to restart X, an attempt to start Amarok failed, but I don't know if that is linked to my problem or not.

---

### Post by Cleric. on 2007-08-28
Is there any way I can see if X is outputting any errors when trying to start up?

I'm a little bit of a CLI noob, so I wouldn't know what to look for or input.

---

### Post by sumguy231 on 2007-08-28
> **Cleric. said:**
> Is there any way I can see if X is outputting any errors when trying to start up?

I'm a little bit of a CLI noob, so I wouldn't know what to look for or input.

Yeah, good idea. Do this:
```
less /var/log/Xorg.0.log
```

See what's in there. Though usually you should be able to see any errors X throws without looking at the log, so that's weird.

---

### Post by Cleric. on 2007-08-28
It seems that the problem was much bigger than I thought, but I am going to just reformat and save me the trouble.

Thanks for your help.

---

