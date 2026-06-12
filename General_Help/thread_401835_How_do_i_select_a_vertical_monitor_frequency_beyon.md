---
title: "How do i select a vertical monitor frequency beyond 85 Hz?"
date: 2007-04-05
forum: General Help
---

### Post by steve196 on 2007-04-05
(dapper)
My new monitor looks best with a vertical frequency of 100 Hz (tested in win2k), but the screen resolution selector shows no frequencies above 85 Hz. How do i select 100 Hz, preferably without flagging xorg.conf as hand-edited/unupdateable?
Thanks!

---

### Post by steve196 on 2007-04-06
Wow, it seems, this question is actually a difficult one.
So another one instead: What is the name of the screen resolution selector program and where is its configuration file?
Thanks!

---

### Post by steve196 on 2007-04-06
Third try:
Where (into what config file) does the screen resolution tool actually write the settings?
Thanks!

---

### Post by steve196 on 2007-04-06
Talking to myself again. Seems, i am asking really impossible things here. I thought Linux was the flexible system and Windows the stubborn one that thinks it knows everything better. Well...
Anyways...
Did anyone find a documentation about the screen resolution tool, that says more than just the obvious?
Thanks!

---

### Post by RomanD. on 2007-04-11
Hi Steve196,
 
  I don't use Ubuntu, but Debian Etch, so I'm not shure if this reply resolve your problem...

 I think  you could use:

  sudo dpkg-reconfigure -phigh xserver-xorg

 or 
 
 try edit /etc/X11/xorg.conf. There is a section Monitor. Just comment (#) lines HorizSync and VertRefresh and restart X server. After that graphic card should use DDC to recognize monitor frequencies...

  by,

              RomanD.

---

