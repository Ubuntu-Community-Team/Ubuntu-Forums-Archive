---
title: "Help with USR modem string for efax-gtk"
date: 2008-06-01
forum: General Help
---

### Post by lhunsicker on 2008-06-01
I need help getting efax-gtk to receive faxes correctly.  Currently I can send faxes using _gfax_ (as a "printer") and they are received correctly.  But when I set up efax-gtk to monitor my phone line and receive faxes, the program answers the telephone, but the fax is received with errors and is unreadable.  

My fax.log reads as follows:

***** Beginning fax log: 1603 CDT 01 Jun 2008 *****

efax-0.9a: 16:05:48 opened /dev/ttyS0
efax-0.9a: 16:05:53 using U.S. Robotics 56K Voice Pro EXT V4.9.2U.S. Robotics 56K Voice Pro EXTOKOK in class 2.0
efax-0.9a: 16:05:54 waiting for activity
efax-0.9a: 16:07:33 activity detected
efax-0.9a: 16:07:48 fax call answered
efax-0.9a: 16:08:29 Warning: 1039 reception errors
efax-0.9a: 16:08:45 Error: timed out after waiting
efax-0.9a: 16:08:50 Warning: timed out after command: +FKS
efax-0.9a: 16:08:55 Error: modem command (Z) failed
efax-0.9a: 16:07:48 remote ID -> " L. G. Hunsicker FAX"
efax-0.9a: 16:07:48 session 196lpi  9600bps 8.5"/215mm  any   1D    -     -  20ms
efax-0.9a: 16:08:29 received 1039 lines with 1039 errors
efax-0.9a: 16:08:55 finished - invalid modem response
efax-0.9a: 16:08:55 opened /dev/ttyS0
efax-0.9a: 16:09:00 using U.S. Robotics 56K Voice Pro EXT V4.9.2U.S. Robotics 56K Voice Pro EXTOKOK in class 2.0
efax-0.9a: 16:09:02 waiting for activity

*** Stopping send/receive session ***

You see above that I am using a US Robotics 54K Voice Fax Modem Pro (ancient, but it works just fine).  I suspect that there is a problem in the modem strings that efax-gtk is sending the modem.

The modem string in the efax-gtk settings is what was given as a default:

Z &F0 E0 &D2 S7=120 &C0 M1 L0

So far as I can see, these seem to be OK.  

Can any of you help me?  Many thanks in advance.

Larry Hunsicker

---

### Post by rjbeeth on 2009-02-19
Unfortunately I can't help you with this one yet - has anyone helped you with it or did you eventually come up with a solution. I've tried to use the same strings that were configures when I used it with WinFax and still no joy. I've also tried hardware control on efax itself ( -oh) but that also does not seem to fix anything.

I'm getting the exact same problem - all incoming data lines error out and I get garbage for a fax page.

Anyone got any suggestions - do you want my log too (which is pretty well the same as the previous) tks

Rick

---

