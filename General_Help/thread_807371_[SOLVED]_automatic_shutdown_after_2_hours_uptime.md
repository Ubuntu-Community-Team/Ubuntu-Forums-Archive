---
title: "[SOLVED] automatic shutdown after 2 hours uptime"
date: 2008-05-25
forum: General Help
---

### Post by jakupl on 2008-05-25
Is there any way of making the computer automatically turning off two hours after it powered up?

maybe using crontab (but i only know how to set an absolute time there)

I tried adding

```
sudo shutdown -P 120
```

to the sessions list, but it did not work

---

### Post by HalPomeranz on 2008-05-25
You could put something like this in /etc/rc.local:

```
echo shutdown -h now | at now + 2 hours
```

"at jobs" are wonderful things for firing off "one-shot" jobs at some point in the future.  It's a shame people don't use them that much anymore.

May I ask why you're doing this?  It seems like a very strange thing to be doing...

---

### Post by jakupl on 2008-05-25
> **HalPomeranz said:**
> You could put something like this in /etc/rc.local:

```
echo shutdown -h now | at now + 2 hours
```

"at jobs" are wonderful things for firing off "one-shot" jobs at some point in the future.  It's a shame people don't use them that much anymore.

May I ask why you're doing this?  It seems like a very strange thing to be doing...

hehe yes it might seem very strange.
This is because I am very busy but at the same time lacking a some self-discipline. Doing this, I can give myself two computer hours every day.

How could I then change the parameter? could i write "minutes" in stead of "hours"?

and could I disable it for one session if I were to, say watch a movie, or doing something work related?

---

### Post by HalPomeranz on 2008-05-25
> **jakupl said:**
> hehe yes it might seem very strange.
This is because I am very busy but at the same time lacking a some self-discipline. Doing this, I can give myself two computer hours every day.


Heh.  Whatever works for you!  :)

> **jakupl said:**
> How could I then change the parameter? could i write "minutes" in stead of "hours"?

Yes, you can use "minutes", "hours", "days", or "weeks".

> **jakupl said:**
> could I disable it for one session if I were to, say watch a movie, or doing something work related?

You certainly may.  "atq" will show you the currently scheduled jobs, and "atrm" allows you to remove a job using the job number displayed in the output of "atq":

```

elk$ sudo atq
2	Sun May 25 17:28:00 2008 a root
elk$ sudo atrm 2

```

For more documentation about all of this, try the command "man at".

---

### Post by jakupl on 2008-05-25
wow thankyou very much!

what a handy thing that.

and by default does nothing... why? being that handy ;)

---

