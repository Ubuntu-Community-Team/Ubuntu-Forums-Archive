---
title: "synchronize clock more often -- editable script?"
date: 2006-11-23
forum: General Help
---

### Post by gregconquest on 2006-11-23
Hi,

I am running ubuntu 6.10 from within VMware Player, and I do close the system down quite often and restart it. Since there is no boot during this process, I am having clock problems.

How can I get the clock to synchronize more often?

Is there any way I can synchronize on demand -- an app that is just one or two clicks of a Button? As it is now, to resynchronize manually I have to de-select the automatic synchronization, then manually synch, . . . It takes quite a while.

Thanks for any help,
Greg Conquest

keys: script, edit, wrong time, synchronize more often

---

### Post by jpkotta on 2006-11-23
Use ntpdate, or even better, ntpd.

[https://help.ubuntu.com/community/NTPTimeSynchronisation](https://help.ubuntu.com/community/NTPTimeSynchronisation)

---

### Post by gregconquest on 2007-03-04
Thanks for the reply, jpkotta. I'm sorry I neglected to follow up on this earlier. ntpdate and ntpd appear to be overkill and would not have addressed my problem, from what I can see on the info pages. One of them is actually to correct for clock drift. I'd hate for it to try and nudge my PC clock into the proper rhythm based on the awakenings of a virtual machine. My clock would seem to advance only a second or so in a few days. That would mean my clock would have to be slowed down 86,400 fold or some such. I only need more often sycs, or best of all, on-demand syncs. Neither of the above seemed to address this point.

I have now changed over from a virtual ubuntu to a dedicated partition, so the issue is moot for me. 

Greg Conquest

---

