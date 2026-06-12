---
title: "keypad home and end not working"
date: 2012-12-01
forum: General Help
---

### Post by chapra on 2012-12-01
Hi all,

I've recently run into a problem when logging remotely into my account at work from my laptop.  My laptop has Ubuntu, although my company has a different distribution of linux, a form of scientific linux.  Also, obviously, i am not the superuser on my work system.

I use an external keypad on my laptop for navigation and editing with arrow keys, page up/down, home/end, and insert/delete.  As long as the numlock is off, all of this works fine. However, the keypad home and end aren't recognized by the scientific linux.

The problem in part involves the signals the keys are sending to the machine. Both keypad left-arrow and regular left-arrow use the code  ^[[D, which can be seen by pressing control v in a terminal, and then pressing the key. The same is true for all of the other arrow keys, as well as page up/down, and insert/delete: the keypad versions all correspond to the same code as their standard keyboard counterparts.  

Insanely, the keypad home/end have different signals than the regular home/end on my laptop. The keypad home has ^[[1~, the keypad end has ^[[4~; while the regular home has ^[OH, and the regular end has ^[OF.

Because I don't need two different signals to exist for the same fuction, I had thought to simply modify my personal laptop so that keypad home and end send the same signal to the computer as the regular home/end.  I'm not sure how to do this, however.  I need to do so in a way that still allows the numerical values to be input when the numlock is on.

Thanks, Chopra

---

### Post by dcstar on 2012-12-01
> **chapra said:**
> Hi all,

I've recently run into a problem when logging remotely into my account at work from my laptop.  My laptop has Ubuntu, although my company has a different distribution of linux, a form of scientific linux.  Also, obviously, i am not the superuser on my work system.

I use an external keypad on my laptop for navigation and editing with arrow keys, page up/down, home/end, and insert/delete.  As long as the numlock is off, all of this works fine. However, the keypad home and end aren't recognized by the scientific linux.
.........

On the assumption that you are logging in using a terminal session, you have an issue with the TTY Emulation.

You need to find out what TTY emulation is required on the remote system and find - or set - the terminal emulator you are using on the Ubuntu system to match it.

[http://www.omgubuntu.co.uk/2011/10/five-alternative-terminal-emulator-apps-for-ubuntu](http://www.omgubuntu.co.uk/2011/10/five-alternative-terminal-emulator-apps-for-ubuntu)

---

### Post by chapra on 2012-12-04
I think maybe I gave too much information, and that led people off of what I was saying.  In general, the keypad home and keypad end are not supported on many systems, because they have a different input code than their primary-keyboard counterparts.

Even if I'm logged on to my work system with one of the company's local desktop computers, they don't work.  In addition, even on my own laptop, they don't work on the root command line, or with a text editor opened in the command shell.

I was trying to change the behavior of the keys so that they maintained their ability to output numbers when the numlock was on, yet gave the computer the same output (\e^OH/OF) as the regular home and end.  I'm not sure if this is possible.

Chopra

---

### Post by chapra on 2012-12-19
got the problem solved on my own.

i used the xmodmap -e command to change the keycodes to "kp_1 end kp_1 end" and "kp_7 home kp_7 home" from "kp_1 kp_end kp_1 kp_end" and "kp_7 kp_home kp_7 kp_home". Just took the "kp_" prefix off of the home and end keysyms, and left everything else the same.

Chopra

---

