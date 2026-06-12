---
title: "How can I see if all of my hardware installed ok? And check for 64bit version"
date: 2008-06-11
forum: General Help
---

### Post by theedudenator on 2008-06-11
How can I see if I am running a 64bit version of Ubuntu.

How can I see if all my hardware is installed and working fine?
Is there a Hardware manager like windows?

---

### Post by overdrank on 2008-06-11
> **theedudenator said:**
> How can I see if I am running a 64bit version of Ubuntu.

How can I see if all my hardware is installed and working fine?
Is there a Hardware manager like windows?

You can use the command ```
uname -a

```
Example
 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux
this is 32 bits

---

### Post by oldos2er on 2008-06-11
For hardware, type "sudo lshw | more" in a terminal.

---

### Post by drs305 on 2008-06-11
And the following will format the command mentioned above into a nice html file on your desktop. Name it whatever you wish:
```
sudo lshw -html > ~/Desktop/**hardware**.html
```

---

