---
title: "minicom not working correctly"
date: 2008-02-26
forum: General Help
---

### Post by gohsthb on 2008-02-26
I have a board that reads temperature and outputs it through USB.  Under windows the board shows up as a USB to serial device.  So in hyperterminal it is working fine.  If I do `echo "D" > /dev/ttcACM0` then `cat /dev/ttyACM0` then I see the temperature displayed and updated like I expect.

The problem is:  under minicom or gtkterm the text is garbled somehow.  It shows me strange characters.  I don't know why it won't work.  I have tried changing the terminal type from VT102 to ANSI but that didn't help.  The comm parameters are set correctly.

Thanks for your help:confused:

---

### Post by gohsthb on 2008-02-26
Found a post somewhere said that gtkterm -p /dev/ttyACM0 was working.  So I treid that.  If I don't change the port speed. then it works fine, just like in windows.  I wonder if it set up such that changing the speed somehow crashes the driver?

:guitar:

---

