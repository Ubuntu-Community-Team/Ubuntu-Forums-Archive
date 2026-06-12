---
title: "I WANNA BE ROOT dammit!"
date: 2007-09-24
forum: General Help
---

### Post by timdoc1 on 2007-09-24
Is there a root account in Ubuntu, how do I login? can I make one?  What gives?

-T

---

### Post by kerry_s on 2007-09-24
ubuntu uses gksu, gksudo, sudo, sudo su

example:
press alt+f2 type gksu nautilus /

---

### Post by timdoc1 on 2007-09-24
Thanks, why alt + f2 (been using alt + f1) and you're telling me I have to type sudo b4 every command (or every 5 mins -when it times out?)  I am not too familiar with sudo and it's variants.  Tell me how you get about doing your ROOT business?

Thanks,
J

---

### Post by yabbadabbadont on 2007-09-24
My personal favorite is ```
sudo -i
```  Of course, I tend to use either a terminal window, or the console, for most administrative operations.  ;)

Edit: Just an FYI, that command drops you into a root shell.

---

### Post by distroman on 2007-09-24
Just for reference.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by timdoc1 on 2007-09-24
Thanks. All.  I'll work on it and be back if I continue having PEBKAC.
-T

---

### Post by Linder on 2007-09-24
Ubuntu is built with the thought in mind that NOONE is root all the time. It's just too damn unsafe and you could screw stuff up by mistankenly clicking the wrong thing or misspelling a command (could happen). So in order to do root stuff, you either gksudo (graphical version of sudo), or sudo, or su.

I recommend gksudo for all graphical tasks (such as starting nautilus in root mode), sudo for all commandline tasks. Don't use su unless you need to do a LOT as root at once.

---

### Post by lisati on 2007-09-24
BTW, this is an international forum - there's an unfortunate meaning to your thread title which could be misconstrued in NZ and Australia......

---

### Post by OoooMatron on 2007-09-24
> **lisati said:**
> BTW, this is an international forum - there's an unfortunate meaning to your thread title which could be misconstrued in NZ and Australia......

So everyone has to be aware of International Political Correctness now do we :-#

---

### Post by lisati on 2007-09-24
> **OoooMatron said:**
> So everyone has to be aware of International Political Correctness now do we :-#

Nah, don't sweat it....... :)

---

### Post by timdoc1 on 2007-09-24
I am American (no relation to our current Prez.) and can guess as to the the meaning of your Aussie idiom, but really, is there any avoiding it?   Surely, many of your  younger kids Down Under snicker during there Comp Sci instructor's lectures on privileges and ROOT.

Regards,
T

---

### Post by timdoc1 on 2007-09-24
BT TW The helpfull link on SUDO goes to the trouble of telling how to disable ROOT (no snickers) if you enabled it, but not HOW TO ENABLE it.

SO HOW DO YOU (no snickers) GET ROOT?


-T

---

### Post by distroman on 2007-09-24
When your done getting the Aussies all hot then maybe you could step off the tabs? ;-)
[http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

---

