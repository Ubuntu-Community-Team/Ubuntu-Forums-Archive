---
title: "Input lag in Feisty?"
date: 2008-01-09
forum: General Help
---

### Post by jammadave on 2008-01-09
Hey guys - 

noticing quite a bit of keyboard-to-display lag recently (like when typing this, the word "quite" didn't show up until I was into "bit"), as well as tab-switching lag in Firefox, and a couple seconds of spinning pinwheel when I click on an app icon in the launch bar.

How do I fix this?  How do I see if it's the OS, SW or HW that's the issue?

Cheers!
Dave

---

### Post by jeffus_il on 2008-01-09
open a terminal and type "top"
to see the top CPU hoggers.

If you are in Gnome you can use "System Monitor" in the Menu and click on the CPU column to sort.

---

### Post by jammadave on 2008-01-09
if it helps at all - the *only* thing I have running on this machine is Firefox.  Oh, and a couple desklets.

---

### Post by jeffus_il on 2008-01-09
The only visible things,
"top" doesn't cost anything, try it !

---

### Post by jammadave on 2008-01-09
oh of course =0)

Top puts firefox-bin at #1 and Xorg at #2.   Occasionally Compiz pops up at #3 with 5% of the CPU.

Also with the key lag I get really, really bad scrollwheel lag on the mouse.

hmmmm, how to fix....   

(had to backspace a word in this post and it didn't show any change until i'd hit all the backspaces and waited a second)

---

### Post by jeffus_il on 2008-01-09
CPU's not very busy?

---

### Post by jammadave on 2008-01-09
no, not really - 2 CPUs, and FFX is using 20-50% of one of them.  (That does sound high for only having 5 tabs in a browser open tho)

---

### Post by jeffus_il on 2008-01-09
Search the threads about this, I think I saw someone solve a similar problem recently.
I will post it if I stumble across it.

---

### Post by ajgreeny on 2008-01-09
Perhaps try with compiz not running which could just be causing the problem if it is simply related to the display of things rather than when things actually happen as far as the cpu is concerned.  I do agree, however, 20 - 50% cpu with just FF running is high, on my system FF with 7 tabs open, plus Gnome System monitor, plus terminal running "top" my cpu usage is about 15 -20% max, on a machine with sempron 2400+, 1GB ram, which seems pretty good to me.

---

