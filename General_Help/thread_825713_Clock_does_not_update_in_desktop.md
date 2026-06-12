---
title: "Clock does not update in desktop"
date: 2008-06-11
forum: General Help
---

### Post by hugo6xas on 2008-06-11
hi,

i'm running hardy amd64, and i'm having this annoying trouble with my system clock. The issue is that i have the clock in my desktop panel, and somewhy, it freezes and stops updating time.

However, if i right-click and select "adjust time and date", it is still running and with the right values. It seems it's just a problem with the panel clock itself, that does not update (if i change something in preferences, like 12h/24h hour format, it momentarily updates to the right time, but it ends up freezing some time afterwards)

Anyone has any idea ? It's getting very annoying having the clock randomingly freezing 

Thanks in advance, and sorry for my english..

---

### Post by hugo6xas on 2008-06-11
Updated Situation:

I found what seems to be the cause of this problem: network monitor
I have added this to panel, and it was causing the whole panel (not only the clock as i thought initially) to crash/freeze from time to time

I removed it from the panel, and it is not freezing anymore..
Still don't get why this happens, but at least now i know where the "trick" is :)

---

