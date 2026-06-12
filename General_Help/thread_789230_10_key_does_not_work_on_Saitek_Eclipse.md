---
title: "10 key does not work on Saitek Eclipse"
date: 2008-05-10
forum: General Help
---

### Post by williambertram on 2008-05-10
Hello,

I have a Saitek Eclipse illuminated keyboard, and the 10 key does not work in Ubuntu.  Actually it appears to be functioning as arrow keys, but will not type numbers.  Yes numlock is on.  :)  Tried it with Numlock off as well.  Verified that it works in XP sp2.  Running Ubuntu 8.04 fully patched.  Has never worked on my Ubuntu install (as opposed to it was working then stopped).

Current keyboard layout under System / Preferences / Keyboard is USA Default, Generic 104 key.  I checked but Saitek does not show up under the "Keyboard Model" list.  I tried modifying all of the options related to Numeric Key Pad under Layout Options to no avail.  Tried deleting the Default USA layout, and adding a new one just to make sure that layout wasn't corrupt or something, also to no avail.

Any ideas?

Interesting - I brought home a USB Dell keyboard, and the 10 key does not type numbers on that either.  Am I the only one out there having this problem?

Found the solution in the DSL (Damn Small Linux) forums.

System - Preferences - Keyboard - Mouse Keys -- Uncheck the box that says "Allow to control the pointer using the keyboard".

Man --  That should *really* be off by default.  Most people expect the numeric keypad to output numbers when numlock is on.  :\

---

### Post by booshire on 2009-11-12
I just ran into this problem as well with my HP G60 with 9.10 -15. It did not manifest until the -15 kernel update. This fixed the issue. Weird this would be enabled out of no where by default...

---

