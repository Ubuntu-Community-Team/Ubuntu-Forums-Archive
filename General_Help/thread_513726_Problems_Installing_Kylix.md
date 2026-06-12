---
title: "Problems Installing Kylix"
date: 2007-07-30
forum: General Help
---

### Post by 64mgb on 2007-07-30
I've been trying for quite a while to install Kylix 3 on Fiesty Fawn.  I found early on that instead of running "sh setup.sh" as the instructions say, I have to run "bash setup.sh".  This works ok for a while, but somewhere along the line the setup process calls another script called main.sh and it calls it using "sh main.sh".  This results in the following error:

main.sh: 73: Syntax error: "(" unexpected

This is the same type of error in setup.sh that was resolved by using bash instead of sh.  I really don't know anything about scripting and what the differences are between bas and sh...can someone shed some light on this and help me through it?

Thanks,
Rich

---

### Post by yabbadabbadont on 2007-07-30
```
sudo dpkg-reconfigure dash
```
Answer 'No' when asked if it should be the default shell.  Log out and back in again.

---

### Post by 64mgb on 2007-07-30
> **yabbadabbadont said:**
> ```
sudo dpkg-reconfigure dash
```
Answer 'No' when asked if it should be the default shell.  Log out and back in again.
Thanks yabbadabbadont - that got me through that problem...now it's on the the next one (relocation error: /usr/local/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference).  As much as I hate Microsoft, even after over a year of pretty heavy Linux usage, I have to say that installing software on Windows is far easier than it is on Linux.  You really have to be involved with the OS.

Rich

---

### Post by yabbadabbadont on 2007-07-31
> **64mgb said:**
> Thanks yabbadabbadont - that got me through that problem...now it's on the the next one (relocation error: /usr/local/kylix3/bin/libwine.borland.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference).  As much as I hate Microsoft, even after over a year of pretty heavy Linux usage, I have to say that installing software on Windows is far easier than it is on Linux.  You really have to be involved with the OS.

Rich

kylix was designed to use an older version of glibc than that used on Feisty.  This is a common problem with commercial software that was abandoned.  Usually, you see someone complaining about this when trying to install/run an old game from Loki.  You'll need to do some google searches to see if there are any workarounds for it.  You might see what people have done to get old Loki games working.  It should be a similar solution.  I too have kylix, but I haven't tried to use it in a very long time.  (and even then, I was just playing with it)  I wish that companies that release non-open source software for linux would get a clue and statically link their binaries.  You wouldn't run into this issue then.

---

