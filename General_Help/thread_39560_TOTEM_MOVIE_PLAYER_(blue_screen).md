---
title: "TOTEM MOVIE PLAYER (blue screen)"
date: 2005-06-05
forum: General Help
---

### Post by xbilly on 2005-06-05
When I try to play videos, I only get a blue screen and audio. How can I fix this?

billy

---

### Post by frodon on 2005-06-09
do you install totem-xine plugin from synaptic ? if not, do it and retry.

---

### Post by MepisReign on 2007-06-04
Everything is actually installed and I have the same problem. I also installed Kaffeine for testing purposes and the result is just the same. All the plugins are there.

Any ideas?

Regards,

MepisReign

---

### Post by jsenner on 2007-07-19
I have the same problem with my Libretto u100. Maybe the next edition of Ubuntu will have this problem fixed....

Jeremiah

---

### Post by ZeroPerCento on 2007-07-25
Hi guys,
try this, it worked for me:
in a shell type:
> gstreamer-properties
when the program starts go to the tab **VIDEO** --> Plugin and select X Windows System (no XV)

Bye!!!

---

### Post by danceswithcats on 2007-07-25
Zeropercento-Thank you.  It works.  

=D>

---

### Post by nycityguy on 2008-01-17
it worked once and no longer is working. I went to the options and changed it as per the instructions, however, when I rebooted, the blue screen came back and the X windows option is still selected.

---

