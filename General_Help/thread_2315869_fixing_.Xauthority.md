---
title: "fixing .Xauthority"
date: 2016-03-03
forum: General Help
---

### Post by Arathorn on 2016-03-03
Every time I try to boot into Kubuntu, Xorg fails to start. When I try startX in the recovery console, I get the error "Error in locking authority file .Xauthority". I've already found out that removing /root/.Xauthority fixes this for the next boot, but a new and apparently faulty .Xauthority files keeps getting created, so I would have to go through all this again for each boot.

So I am wondering whether it is possible to either:
[LIST]
[*]fix .Xauthority so X will start or
[*]automatically remove .Xauthority every time I shut down.
[/LIST]

Obviously I would prefer the first option. Any ideas?

---

### Post by Arathorn on 2016-03-10
Nobody? If additional information is required to help me, please tell me.

---

### Post by steeldriver on 2016-03-10
It's really not recommended to startx as root (as in the recovery console) - why do you feel you need to do that?

---

### Post by Arathorn on 2016-03-10
I have no other choice, without going through the recovery console I wouldn't be able to boot at all because X would never start.

---

### Post by steeldriver on 2016-03-10
Well FWIW I'd focus on why your user-session fails to start, rather than substituting a root X session

Are you using lightdm or kdm as display manager?

Have you tried logging in as yourself at one of the VTs (Ctrl-Alt-F1) and running startx **as user** from there?

Have you looked in your user's ~/.xsession-errors file?

---

### Post by Arathorn on 2016-03-10
I use kdm as a display manager, but please note that I'm not even getting to that point. After the glowing Kubuntu logo I get a black screen, so there is no way for me to log in as any user. The only way I can get somewhere is through the recovery console. And even the workaround I started this thread with doesn't work any more, so there's no way into any gui at the moment (though I can access the file system through my Windows partition and the recovery console).

No errors are written in .xsession-errors, neither in /root nor in /home/username/

These are the errors I get when I startx in the recovery console:
```
(EE)
Fatal server error:
(EE) Could not create lock file /tmp/.tX0-lock
(EE) 
(EE)
Please consult the Xorg [...] for help
(EE) 
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth: error in locking authority file /root/.Xauthority

```

---

### Post by steeldriver on 2016-03-10
You shouldn't need any kind of X session in order to log in at one of the CLI virtual terminals (Ctrl-Alt-F1 thru F6)

In the above, are you trying to startx in recovery mode *without remounting the filesystem in rw mode*? That might explain why it can't write the lock file.

---

