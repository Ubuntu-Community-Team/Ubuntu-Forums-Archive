---
title: "Only problem with Ubuntu is..."
date: 2006-07-10
forum: General Help
---

### Post by jimmygoon on 2006-07-10
Now I know that AIGLX and Compiz are "expirmental" technoology or some babble like that (grin) but I can not suspend or hibernate (more precisly, cannot awaken from suspend more or hibernation) with Compiz enabled. If I "switch to metacity" first and THEN suspend... it wakes up just fine.

Is there any work arounds/solutions for this or anything I can run to help provide better/more feedback?

thanks


edit: Also, I would like the "scale" plugin to include ALL windows, including those which are minimized! Any ideas on that? I have it set up (per one of the guides) to activate it when my mouse enters the top left hand corner of my screen, but even the keys f10-f12 don't open all (minimized) windows either

---

### Post by Shay Stephens on 2006-07-10
> **jimmygoon said:**
> Now I know that AIGLX and Compiz are "expirmental" technoology 

Don't run beta software if you need certain functionality.  If you are not willing to live on the wild side of stuff not working, breaking, or worse, then stick to the stable stuff.

I'm waiting for all the fancy stuff to stabilize before I try it, and even then I may not use it for performance reasons.  Nothing wrong with ***not*** living on the bleeding edge ;)

---

### Post by guice on 2006-07-11
That's not really a problem with Ubuntu. You're using beta software. Beta software will have bugs. The only way around them is to live with them or don't use the software until it gets fixed.

---

### Post by nanotube on 2006-07-11
hey guys, chill out. he knows it's beta. all he is asking is if anyone knows any tweaks or workarounds to this problem. if you don't know of any, just say so (if you really insist of saying something). 

saying "beta software has bugs, you gotta live with them" is not helpful or insightful. and some of your phraseology is not even friendly. ;)

sure, his subject line is not great. it would have been more helpful if you pointed out that a subject has to have meaningful content, since that makes it easier for people to parse posts. and maybe if you pointed him to a "making good posts" guide, such as one that can be found in the fourth link in my sig. 

and while i am here, no, i don't know of any workarounds. :)

---

### Post by loell on 2006-07-11
speaking of chilling out :)

i notice that there are number, if not yet many
thread titles that are flame bait. what could the reason be?

---

### Post by nanotube on 2006-07-11
> **loell said:**
> speaking of chilling out :)

i notice that there are number, if not yet many
thread titles that are flame bait. what could the reason be?

i suspect that it's due to the large influx of new ubuntu users (notice the sudden increase in online active users since dapper release), who are not yet aware of the proper forum manners. 

also, it probably gets more people to look at a post, to have an inflammatory post title. but on the converse, most of the people who do look at it will not know how to help, since they did not know what the post will actually be about when they looked. so it doesn't actually net the poster anything. but maybe they don't realize that.

---

### Post by mech7 on 2006-07-11
hmm that might be my problem... my laptop went into hibernation i have compiz.. and does not wake up anymore.. i cant even turn it off :| when i press the shutdown buttom i seem the hdd led flcikering for a bit and then nothing aaaarrgggg....

---

### Post by T700 on 2006-07-11
[One thread to rule them all]("http://www.ubuntuforums.org/showthread.php?t=148351").

Paul

---

### Post by jimmygoon on 2006-07-11
Sorry about the title. What I meant was that MY only problem with Ubuntu. I wasn't saying that its Ubuntu's fault and I stated that I understood it was experimental. It wasn't meant to be flame bait, but in retrospect it was a vague and unrelated topic title anyways...

But, so now that we have 8 replies... cough... has anyone else experienced similair problems or is there a *workaround*?

Thanks guys.

---

### Post by givré on 2006-07-11
That's a known issue that i hope will be solved in the future. But here is the better workaround we found for the moment (not mine but i couldn't remember where i found it 8) )
The thing is to switch to metacity before suspend. You could do it manually, but the best is to add a script to the ones which are launch before suspend. In a terminal,
```
gksu gedit /etc/acpi/suspend.d/25-compiz-stop.sh
```
and copy that in:
```
#!/bin/bash
#/etc/acpi/suspend.d/25-compiz-stop.sh

COMPIZUSER=`ps -Ao user,comm | grep compiz.real | awk '{print $1}'`
killall gnome-window-decorator &
killall compiz.real &

```
save and exit.
No to restart compiz after suspend, we will do the same thing,
```
gksu gedit /etc/acpi/resume.d/99-compiz-resume.sh
```
and copy that in:
```
#!/bin/bash
#/etc/acpi/resume.d/99-compiz-resume.sh

if test ! -z $COMPIZUSER;then
        export DISPLAY=:0.0
        sudo -H -b -u $COMPIZUSER /usr/bin/gnome-window-decorator
        sudo -H -b -u $COMPIZUSER /usr/bin/compiz --strict-binding --indirect-rendering --replace gconf
fi

```
That should work.

---

### Post by jimmygoon on 2006-07-11
> **givré said:**
> That's a known issue that i hope will be solved in the future. But here is the better workaround we found for the moment (not mine but i couldn't remember where i found it 8) )
The thing is to switch to metacity before suspend.
That should work.

I had been doing it manually! Thanks so much for those instructions... It literally is just a workaround, is there any idea as to why the xserver or gnome can't recover on its own?

---

### Post by RAOF on 2006-07-11
> **jimmygoon said:**
> I had been doing it manually! Thanks so much for those instructions... It literally is just a workaround, is there any idea as to why the xserver or gnome can't recover on its own?
Since the solution is switching to Metacity from Compiz, I 'd say the problem is that Compiz is trying to access the OpenGL subsystem before the system is fully ready.  As to **why** that kills things... no idea :)

---

