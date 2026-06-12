---
title: "CPU 99% awake and no process using it"
date: 2008-04-29
forum: General Help
---

### Post by rogeriovinhal on 2008-04-29
After installing Hardy (clean install) I've noticed some weird things once in a while. Sometimes firefox just stop responding for some time, like 10 - 15 seconds and become gray (because of compiz). If I look at HD led, it is wide lit and then suddenly it stops and firefox comes back to normal.

I opened a terminal and opened top to see what was doing that HD intensive activity, but then something strange comes up: top shows the processor 99% wake, but no process actually using it.

I have seen this many times, in the last one I managed to get a screenshot, which is attached.

What could this be?

---

### Post by djdarrin91 on 2008-04-29
This has also happened to me,I just updated my system and things seem to be ok now.Although i really don't know the cause. sorry:(

---

### Post by andied on 2008-04-29
There have been a couple of threads on this. For me, and other posts I have seen, in Firefox preference>security, uncheck the two boxes dealing with sites suspected of forgery and attack. Also delete the file "urlclassifier3.sqlite" in your Mozilla profile.


edit: my urlclassifier3.sqlite file had grown to 35MB; after unchecking the two boxes and deleting the urlclassifier3.sqlite file, Firefox rebuilt the file and it is now 9KB.

---

### Post by rogeriovinhal on 2008-04-29
The urlclassifier3.sqlite in my mozilla directory was 40MB large. I've deleted it and unchecked the boxes, lets see if it stops from now on.

But how could firefox trick top for not showing that it was the responsible for the 99% CPU wake?

---

### Post by scragar on 2008-04-29
because firefox wasn't useing 99% of your processing power, only 99% of your input/output when it was scanning the file and page for matches.

---

### Post by rude_lee on 2008-04-29
how do i find that file urlclassifier3.sqlite

---

### Post by bingoUV on 2008-04-29
> **scragar said:**
> because firefox wasn't useing 99% of your processing power, only 99% of your input/output when it was scanning the file and page for matches.

 rogeriovinhal, see the 99.0%wa in your top output. This is what scragar is pointing to. 99.0% of processor is serving processes that are waiting for I/O , from the hard disk in your case.

---

### Post by scragar on 2008-04-29
```
rm ~/.mozilla/firefox/*.default/urlclassifier3.sqlite
```
will delete it for you.

---

