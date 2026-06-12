---
title: "root partition checked on boot 2 times in three days"
date: 2006-08-12
forum: General Help
---

### Post by kinematic on 2006-08-12
the root partition is supposed to be checked after every 30 boots but on my box it's checked a lot more often.
when i booted up ubuntu this morning it was checked again even tho it was checked just 3 days ago and this has happened several times before. 
fstab uses the default parameters
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
and it's still being checked much more often then it should be.
now i don't want to disable the check completely but it would be nice if root wasn't checked so much.
does anyone have an idea what could be causing this?

---

### Post by ifokkema on 2006-08-12
Well, it could be just a weird setting that after much less mounts, it checks your file system. What's the relevant output of:
```
sudo tune2fs -l /dev/sda1
```
? It shows some info on your drive, including the maximum mount count before checking.

---

### Post by kinematic on 2006-08-12
maximum mount count says 30.
maybe i'll just disable it altogether...in all the time i've been using linux i've never had to do a hard reboot and the checking isn't really that nessesary with ext3.

edit:this is interesting.....tune2fs -T /dev/sda1(time of last check)gives the following output:
can't resolve date/time specification(i think that's the correct translation...i'm dutch).
makes sense now that's it's checked more often if it can't determen when the last check was.

---

### Post by rbmorse on 2006-08-12
As an aside, may I reveal my ignorance and ask how one forces a check between regularly scheduled checks?

---

### Post by ifokkema on 2006-08-12
> **kinematic said:**
> maximum mount count says 30.
maybe i'll just disable it altogether...in all the time i've been using linux i've never had to do a hard reboot and the checking isn't really that nessesary with ext3.
I've had to fix some errors once or twice, but that probably was related to me having to turn my PC off a couple of times because of some issue with a video driver...

> **kinematic said:**
> edit:this is interesting.....tune2fs -T /dev/sda1(time of last check)gives the following output:
can't resolve date/time specification(i think that's the correct translation...i'm dutch).
makes sense now that's it's checked more often if it can't determen when the last check was.
Well hello fellow Dutchman! :)
I think the error had to do with what you specified after the device name...

Can you remember seeing any errors when the device was checked? Maybe there was a reason for the system to force a check... If not, then I ran out of ideas, sorry :( 

> **rbmorse said:**
> As an aside, may I reveal my ignorance and ask how one forces a check between regularly scheduled checks?
```
sudo fsck -f /dev/hda1
```
(replace /dev/hda1 if needed)

---

