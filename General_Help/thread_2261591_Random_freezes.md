---
title: "Random freezes"
date: 2015-01-20
forum: General Help
---

### Post by rafiqcombrinck on 2015-01-20
Good morning all

My apologies for the very vague question, but I have to start somewhere ;)

I recently loaded Ubuntu 14.04 LTS 64-bit on my laptop (Toshiba, i5, 8Gb Ram etc.) and I find that I have very random things freezing/crashing. I generally never switch the machine off, just suspend so not sure if that might be causing any issues, but never really had problem when I was running 12.04 LTS on my previous 2 machines. The other day nm-applet just stopped working (did not want to open at all) and I find that Libre Office stops responding (this is the one I have noticed the most as I use it daily) quite frequently and the only thing that helps is to reboot the pc. Other than that I also get the no keyboard so every now and again when waking up (I just put it to sleep again and then wake up and it usually starts working again).

Where do I start with this, how can one fault find these sort of occurrences?

Thanks.

---

### Post by kerry_s on 2015-01-20
look through /var/logs

normally what i do is delete all logs there, cause there are a lot. then you just do your thing, and if something happens, check the logs, it'll be less logs to go through.

---

### Post by rafiqcombrinck on 2015-01-20
> **kerry_s said:**
> look through /var/logs

normally what i do is delete all logs there, cause there are a lot. then you just do your thing, and if something happens, check the logs, it'll be less logs to go through.

Awesome, thanks kerry, have just cleared the log folder so will see what pops up in there next ;)

---

### Post by rafiqcombrinck on 2015-01-21
I'm not coming up with anything. There seems to be tons of logs and a quick scan through them shows no errors that I can see, but as soon as I wake my laptop up from suspend I can't get Libre Office to work at all. The only thing that helps is rebooting. Very strange, have been using Libre for quite some time and have never had issues like this. The only difference being this is my first 64-bit machine :P

I'm starting to contemplate changing to another DE or am I fixing an itch with a hammer?

---

