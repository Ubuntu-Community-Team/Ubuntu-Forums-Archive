---
title: "&quot;The file '/var/log/boot.log' does not exist.&quot;  Why doesn't it?"
date: 2007-03-09
forum: General Help
---

### Post by Phrawm48 on 2007-03-09
I tried to use *KSystemLog* to view the boot log, only to be told that **The file '/var/log/boot.log' does not exist.**  Sure enough, a file with that name did not exist in */var/log*.

So I then searched */etc/syslog.conf* for the word "boot".  Nope, not a single instance.

So I then used *man syslog.conf* to read the documentation(!)  Here again, a search of the *syslog.conf* man page for the word "boot" came up empty.

Finally I tried the Web.   There I found various comments advising that the reader *look at* */var/log/boot.log*, but nothing that explained how to get *boot.log* filled with information.

Holy Cow!  Finding out how to enable */var/log/boot.log* is turning out to be surprisingly difficult.  So, can anyone please point me to some information about enabling */var/log/boot.log*?

Cheers & thanks,
Ric
SFO

---

### Post by yabbadabbadont on 2007-03-09
```
/home/daffy $ cat /etc/default/bootlogd 
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

```
"man bootlogd" for details.

:D

---

### Post by Phrawm48 on 2007-03-09
Cool!  Thanks much!

It's easy when one knows where to look, huh?

Cheers & thanks 'gain,
Ric
SFO

---

### Post by yabbadabbadont on 2007-03-09
You're welcome.  You're right about it being easy when you already know the answer.  :D

When I was copying that information for you, I realized that I had forgotten to enable it myself after my last re-install (last night/early this morning)  So I guess I should thank you for reminding me.  :lol:

---

