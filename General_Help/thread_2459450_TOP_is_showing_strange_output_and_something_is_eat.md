---
title: "TOP is showing strange output and something is eating memory"
date: 2021-03-18
forum: General Help
---

### Post by asinabe12 on 2021-03-18
I was having trouble with something eating too much memory in Ubuntu. I ran TOP to see what was consuming so much memory, but TOP didn't appear as it normally should. It displayed two separate windows for activity on my computer.  It's hard to describe, so I will show pictures of it. 

I was wondering if it is normal for TOP to look like this. If not, I'm wondering what could be causing this. TOP used to not appear this way. TOP always displays in this  abnormal way when some process is eating up excessive amounts of memory.  This seems to happen daily at around 6 pm. At times when there isn't excessive memory usage, TOP appears  normal. 

Is this just some quirk in Ubuntu 20.04 or is it something else?

---

### Post by TheFu on 2021-03-18
Looks like a problem with the terminal program.

Try typing "resize" into the terminal before you run top in the same terminal.  You may need to use a different terminal program. The line wrap seems off in all those images. I'm 100% positive that an xterm won't have this issue.  But xterms are fairly minimal terminals and use techniques from 1990 to control fonts, sizes, and other terminal settings.

---

### Post by CharlesA on 2021-03-18
Seconding the "that's not normal" bit.

I'm curious to see what your terminal is set to. You can find out by running this command:

```
echo $TERM
```

Mine says "xterm" and handles resizes fine with top.

---

### Post by Yellow Pasque on 2021-03-19
Try htop.
Anyway, I don't see anything too intensive in your screenshots. Firefox and its "Web Content" processes are the biggest users, but nothing out of the ordinary.

---

