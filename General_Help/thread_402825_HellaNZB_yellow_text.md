---
title: "HellaNZB yellow text"
date: 2007-04-06
forum: General Help
---

### Post by stuples on 2007-04-06
Hi,

HellaNZB is great, works effortlessly. But I have one problem and it's the awful yellow font colour used for the ETA. I've tried disabling colours in the hellanzb.conf but they are still being used. Any ideas?

Solution:

Just change the colour profile used for the terminal. To do this open a terminal go Edit > Current Profile > Colours Tab.

---

### Post by stuples on 2007-04-06
One solution I'm going to accept is to switch the terminal colour scheme from black-on-white to white-on-black so the yellow is actually readable.

---

### Post by CulleyS on 2007-09-25
I had the same problem and here is what I did, but your suggestion works as well.

I edited the Logging.py file that came with Hellanzb.  For me, it was located in /var/lib/python-support/python2.5/Hellanzb

I did a search in the file for "yellow" (I was using gedit to edit the file) and found two lines.  One was a class statement of ASCII codes, the other set the color for the ETA.

             ACODE.F_YELLOW, eta, ACODE.RESET, paused, ACODE.KILL_LINE)

I changed "YELLOW" to "DRED" for dark red, now it looks just fine. :)

---

