---
title: "quick script - send mail with output of diff"
date: 2007-02-28
forum: General Help
---

### Post by neill on 2007-02-28
hi

can anyone knock up a quick script for me - i'm very new to this !!

i need to take the output of:

diff -u /path /another/path

if the output is zero (ie: no diff) then i want to mail an "OK" to root

if the output <> zero (ie: some diff or other) then i want to mail that to root

i guess you have to pipe the output of the diff to a temp file, then mail it's contents if they're not zero, and delete it for next time or drop out to an "OK" mail

so the crux is - how do i test for a zero byte file ??

sure it's dead easy for you gurus out there 

:lolflag: 

ta

neill

---

### Post by lamego on 2007-02-28
You can check the lines count: diff whatever | wc -l

---

