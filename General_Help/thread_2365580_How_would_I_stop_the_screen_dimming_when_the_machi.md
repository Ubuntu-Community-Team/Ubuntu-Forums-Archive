---
title: "How would I stop the screen dimming when the machine is under load?"
date: 2017-07-07
forum: General Help
---

### Post by nigelgardiner on 2017-07-07
Hi there

With Ubuntu 16.04 the screens keep dimming every time the machine is running under load. It's quite distracting and difficult to continue working.
Is there any way to disable this feature?

thanks
Nigel.

---

### Post by oldos2er on 2017-07-07
What are your computer's hardware specs?

---

### Post by wildmanne39 on 2017-07-07
It's not a feature, your system is responding slowly that causes the dimming, could be a program not working right or you are just over taxing your system. When it happens look at your logs and see what is going on, or install top and check your resources at the time it is happening, see if it is using up all your cpu or memory and go from their.

---

### Post by nigelgardiner on 2017-07-07
Oh right, thanks.
I'm running a quad core 3.6ghz xeon with 64 gig ram and 8gig video card on a dell t3600 motherboard.

On reflection it only occurs when the software (Houdini) is running a live load so to speak. If the processes are running in the background I don't see the screen dimming.

Excuse my ignorance but I don't know how to look at my logs, will have to look that one up.
Looking at the system monitor tho I rarely run out of ram, cpu is maxxed out qquite often tho.

thanks
Nigel.

---

### Post by wildmanne39 on 2017-07-08
It sounds like you know what is going on now but you can check your logs like this in the terminal.
```
tail -n100 /var/log/kern.log
```
```
sudo tail -n100 /var/log/syslog
```
Good Luck and when you are satisfied you got the answer you need please use thread tools at the top of the page to mark the thread solved.

Thanks

---

