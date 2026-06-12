---
title: "Ubuntu saved my bricked laptop! (Kinda)"
date: 2007-01-15
forum: General Help
---

### Post by Sicarius on 2007-01-15
My Toshiba Satellite has been dead for almost a year now, and nobody's been able to fix it. It was crippled by a virus that completely... Well, it was dead. After about 20 unsuccessful attempted installations of Ubuntu, it finally eradicated the virus on the HD and got to 97%, before it shut the computer off. But upon rebooting, it worked just fine. However, when I go to update everything (I wanted to so I could get my wireless card working), it pops up with this error message: "The Following Problems Were Found On Your System: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem. My question, quite newbishly, is: How do I fix this? Also, in the event that this can be fixed, how do I get a wireless card to work properly?


Thanks in advance guys.

---

### Post by Seadap on 2007-01-15
Grats Sicarius.  To fix the error, run dpkg --configure -a in a terminal.  You may have to do it with with root priviledges, I'm not sure.

Once that's sorted, we can work on your wireless card problem.

---

### Post by Sicarius on 2007-01-15
Where would I find a terminal? Heh, very new to this.

---

### Post by Seadap on 2007-01-15
If you are using Gnome, click on the Applications menu, Accessories, Terminal.  Failing that, press ctl-f2 and voila!  If you have gnome running, to switch back to it (after ctl-f2 method) press ctl-f7.

---

### Post by Sicarius on 2007-01-15
Ok, found the terminal. Now, how do I go about gaining 'superuser' privelages?

---

### Post by aysiu on 2007-01-15
> **Sicarius said:**
> Ok, found the terminal. Now, how do I go about gaining 'superuser' privelages?
```
sudo dpkg --configure -a
```

---

### Post by NeoLithium on 2007-01-15
The best way is to use ```
 sudo <command>
```; which basically gives you superuser for that specific task; so you don't accidentally tinker with other things (I've done that far too many times by ignoring my root@localhost.

---

### Post by Seadap on 2007-01-15
type sudo dpkg --configure -a at the prompt.  It will ask you for your password.  I would try runing it without sudo first.  Not sure if it's needed.

---

### Post by NeoLithium on 2007-01-15
dpkg does require root privilages

---

### Post by Sicarius on 2007-01-15
Ok, that error message has gone, but now there's this one: "Warning: You have 7 broken packages on your system! Use the "Broken" filter to locate them.

---

### Post by Seadap on 2007-01-15
Post the output of ```
dpkg -l | grep -v ^ii
``` here.

---

### Post by Seadap on 2007-01-15
Easier:

Got to System | Administration | Synaptic Package Manager.

Once it's open, go to Edit | Fix broken packages

---

