---
title: "Keyboard mapping issue - I think..."
date: 2007-12-05
forum: General Help
---

### Post by dianeh on 2007-12-05
I recently install Ubuntu 7.10 as a dual boot with my Windows XP Home PC
(and HP Pavilion).  In general, the keyboard works fine except for the key with
the single/double quote symbol.  I have to hit the key twice before any symbol
displays on the screen.  I am trying to write some Perl scripts and I get an
error for any line with the double quotation mark on it.  I also seem to have
this problem with the colon/semicolon key as well.  When I installed Ubuntu
it detected that my keyboard is US/Intl.  Any suggestions?

---

### Post by geraldm on 2007-12-05
The littlest finger hits both of the keys in question.  I would suspect that the keys are not hit hard enough the first time ?  You can test the keys using the xev command within a terminal.
Move the mouse pointer within the square.  The keypress events are logged to the terminal.
That should test whether the keys are actually hit one or two times, and show the key events.
It is doubtful that the keyboard type has anything to do with the problem keys.  

Gerald

---

### Post by Bill Jones on 2007-12-05
As you say it's a problem with keyboard mapping. Change from US International to US English and you'll be happy.

---

### Post by N-t-F on 2007-12-05
If I remember correctly, the US International keyboard is designed to allow the typing of special (foreign) characters with combination or repetition of keys. This might be your problem. :confused:

---

### Post by dianeh on 2007-12-05
Thanks to everyone for your quick suggestions.  I changed my keyboard
preference from US International to US English and that solved my problem.
My perl scripts are running fine now too!  Thanks again everyone!:)

---

