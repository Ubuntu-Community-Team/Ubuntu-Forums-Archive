---
title: "How many processes"
date: 2005-09-17
forum: General Help
---

### Post by andrewsawyer on 2005-09-17
A question:

My laptop tells me I am running anywhere between 175 and 190 processes at any given time.  I've moved over from Windows XP a while ago, and for M$ this is very high.  Is this normal for Ubuntu, or should I be looking at cutting this down?  How many processes to other people seem to be running?

Also, gkrellm (which tells me how many processes I have) is also telling me that I have users.  Now as far as I'm aware, I am a user, and I can CTRL ALT F7 to switch to my girlfriends profile, however that is only two users.

So where are the other two?  How do I find out what they are?

Can someone also direct me to any info that might help me lower the number of processes on my laptop, and therefore speed it up a little (not thats it's slow now)?

Any help would be much appreciated.

---

### Post by xmastree on 2005-09-17
System>Administration>Boot up manager will allow you to disable certain services at boot up. If you don't have a printer, you can probably disable cupsys for example.

```
users
``` will tell you who's logged on.

---

### Post by andrewsawyer on 2005-09-17
```
andrew@ubuntu:~$ users
andrew andrew andrew andrew katie
andrew@ubuntu:~$
```

Urm... which one is me?  Obviously I have a number of user areas open. As this is a fresh reboot, there is obviously something wrong happening.  Can anyone explain what is happening and how I might fix this?

Many thanks,

Andy

---

### Post by fordfan753 on 2005-09-18
[QUOTE=][/QUOTE]
 Having heaps of users is normal (not sure why) maybe it counts terminal sessions as a new login....

---

### Post by andrewsawyer on 2005-09-18
Thats a relief - at least I know I've not got a hacker in my system!

Thank you.

---

