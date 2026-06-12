---
title: "HELP! big problem while ugrading to Hardy!"
date: 2008-04-30
forum: General Help
---

### Post by Jarramundi on 2008-04-30
I just tried to upgrade to Hardy Heron from Gutsy Gibbon, but I fell asleep while it was downloading and woke up to a non-responsive black screen. So I restarted the computer which was all messed up saying that it couldn't initialise !HAL. So I restarted in recovery mode, and it told me I needed to run:

dpkg --configure -a 

So I did, and it got a long way through, before it started to run into errors. The error message is  

dpkg ../../src/packages.c:252: process_queue:Assertion'!queuelen' failed. Aborted

I have no idea what to do. 
Please help oh wise ubuntu gurus. :confused:

I got it sorted. tried:

dpkg --force-a --configure-a 

which gave me a different list of errors. Problems with dbus. so I:

mkdir /usr/bin/dbus

and then 

dpkg --configure -a

and it worked!

Solved

---

