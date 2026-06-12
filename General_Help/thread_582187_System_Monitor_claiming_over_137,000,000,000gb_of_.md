---
title: "System Monitor claiming over 137,000,000,000gb of RAM in use"
date: 2007-10-19
forum: General Help
---

### Post by khazor on 2007-10-19
So, I suppose this is largely irrelevant, because it is not causing any noticeable errors or malfunctions... But take a look at this screencap of my System Monitor: 

[http://img.photobucket.com/albums/v188/khazor/completelyridiculous.jpg](http://img.photobucket.com/albums/v188/khazor/completelyridiculous.jpg)

...Can anyone give me a logical reason that Gutsy would claim to be using over 17 petabytes for a single application, let alone why it would possibly think that 8 apps are doing that and that I have over 137pb available? ...Does that much data storage actually exist anywhere? hahaha.

But in all seriousness, is this going to turn into some sort of major system-usage error that will kill me?

---

### Post by mlissner on 2007-10-19
This is very odd...have you restarted the program? Is this also reported in top?

---

### Post by Can+~ on 2007-10-19
Weird, even the "last 1, 5, 15" minutes is wrong. I don't know the exact calculation that the system monitor does, but I imagine that the X / time, so, if time is 0, the result is infinite. But.. in that case, all of your processes should display the same insane numbers.

---

### Post by rbmorse on 2007-10-20
An update to system-monitor was pushed during my overnight, but I didn't look that the change blurb.

---

