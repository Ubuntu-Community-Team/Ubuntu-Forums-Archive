---
title: "The startup programs list is not saved"
date: 2006-10-28
forum: General Help
---

### Post by deggial on 2006-10-28
Hi everyone,

I am using Ubuntu Edgy Eft and when I try to add new programs in the System->Preferences->Sessions->Startup Programs, the list does not update properly. When I close the window and re-open it (or logout to see if they will open) the list reverts back to the original one.

Any ideas how I can fix this?

---

### Post by deggial on 2006-10-28
Never mind, problem solved.

Just in case someone else encounters it, the problem was that the ~/.config/autostart folder has root as owner and files cannot be created in it. I solved the problem by changing the owner to the normal user (chown normaluser autostart).

---

### Post by abrarey on 2006-10-30
Thanks i had the same problem.
its solved now

---

### Post by Chippendale on 2006-10-31
yeah! thanks, i was having the same thing and was a little "?!?"

---

### Post by geokok1981 on 2006-11-10
It seems that the problem appears to some users while not on others.

Also I filled a bug report at launchpad here:
[https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200](https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200)

please go there and confirm the problem if u face it too....

---

### Post by Zeratul7 on 2006-11-10
Strange thing, I have had many familiar problems in Edgy that are also related to user rights (with gDesklets, /tmp dir etc.). I have never had them in previous releases. I think it might be a quite wide problem.

---

### Post by RSX311 on 2006-11-26
thanks deggial! It was annoying the crap out of me that I had to manually startup my programs through the console on each reboot.  Your fix worked!

---

### Post by bazerk on 2006-11-28
sorry for being a bit stoopid but how exactly did you enter that command?
same problem on 2 machines, messing with beryl. not good. thanks in advance.

---

### Post by RSX311 on 2006-11-28
open up terminal and replace <user name> with your log in user name

```
sudo chown <user name> ~/.config/autostart
```

then enter in your password

---

### Post by bazerk on 2006-11-28
nice one bruv, worked like a charm.

---

### Post by Falcorian on 2006-11-29
Same problem, same solution worked. Thanks!

---

### Post by Cactus Sediento on 2007-03-21
thaks...had the same problem, now resolved

---

### Post by pirothezero on 2007-04-11
posting to say I had the same thing happening and this solution fixed it for me.

Strange how the occurrences of this are sporadic hope they get this fixed, whatever it is.

---

### Post by ZERO_SHIFT on 2007-04-22
I love the ubuntu community

LLTC!!!(Long Live The COMMUNITY!!)

---

### Post by 3ntity on 2007-04-23
I just had the same with Feisty... It seems to be solved with this :D 
Thanks a lot!

---

### Post by acheton on 2007-05-07
Worked great for me on Feisty as well, thanks!

---

### Post by Faust942 on 2007-06-26
> **RSX311 said:**
> open up terminal and replace <user name> with your log in user name

```
sudo chown <user name> ~/.config/autostart
```

then enter in your password

Thanks bud!

---

### Post by lando786 on 2007-11-29
I have tried this fix and have had no luck at all.
I cannot even see the file if i run gksudo nautilus. Might there be a program changing the permission constantly?

---

### Post by slibuntu on 2008-03-04
I tried the fix, and the terminal says that the permission has been changed, but it still doesnt work! I've restarted and confirmed it doesn't work, anyone got any other ideas as to the problem? I'm not really running many extra programs on top of the default setup, apart from compiz I suppose.

---

