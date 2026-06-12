---
title: "Help with linux key logger and keymap issues please"
date: 2008-05-02
forum: General Help
---

### Post by JimmyHopkins on 2008-05-02
Hello all, I'll cut to the chase. I installed "lkl" (linux key logger), and it asks for a keymap. I'm running hardy haron, with a P4 3 GHz. Anyway, I do

sudo lkl -k /usr/share/lkl/keymaps/us_km

and then

sudo lkl -l

and I get:

Started to log port 0x60. Keymap is (null). The logfile is (null).

unable to find keymap-file: Bad address
a keymap is required!! run lkl with -k <keymap>


Yes, I have already set the logfile with

sudo lkl -o /home/name/keylog.txt

and I've tried:

sudo lkl -o /home/name/keylog.log

No luck, I always get the same error. Any help?

---

### Post by weirdtalk on 2008-07-16
you have to use the keymap everytime like this:

sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /home/name/keylog.txt

but I didn't find lkl useful since the mouse messes it up (good for termials though)

---

### Post by Titoolsen on 2009-05-23
i have set up lkl but the keylog file contains nothing - how do i activate it?

---

### Post by liquider on 2009-12-14
should anybody else have trouble with lkl, a superior alternative IMO is [logkeys linux keylogger]("http://code.google.com/p/logkeys/").
sorry for bump :P

---

