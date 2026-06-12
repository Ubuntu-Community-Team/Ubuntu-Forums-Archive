---
title: "Viewing boot-up progress messages after boot-up?"
date: 2007-11-07
forum: General Help
---

### Post by imbjr on 2007-11-07
I was watching the OS boot and it decided to give the main ext3 partition a check. After it finished that, I briefly saw a message that contained the word "cannot".

I checked the logs - nothing obvious. I check dmesg - again, nothing obvious. Is there a log of what Ubuntu displays during boot progress somewhere, or am I going to have to disable usplash somehow and try and catch the message again?

---

### Post by bakeneko on 2007-11-07
Have you taken a look at **/var/log/boot**?

---

### Post by imbjr on 2007-11-07
Just tried recovery mode, but nothing showed up!

I wonder if it had something to do with setting up the X server - but the logs didn't reveal anything particularly unexpected.

---

