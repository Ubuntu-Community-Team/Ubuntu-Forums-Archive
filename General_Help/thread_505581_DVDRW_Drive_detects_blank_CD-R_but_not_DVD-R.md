---
title: "DVDRW Drive detects blank CD-R but not DVD-R"
date: 2007-07-20
forum: General Help
---

### Post by Eastisle on 2007-07-20
Hi,
I was trying to burn some media to a DVD-R using my DVDRW drive but it wont recognize/detect the blank DVD. 
I can hear the drive reading the DVD but it never shows on the desktop as a blank DVD-R. 
It is as if there was no DVD in the drive in the first place. I dont get any error messages or anything of that matter.

I know my drive works since I have burned many CD-Rs without a problem. When blank CD-Rs are inserted Ubuntu recognizes them immediately and I get prompted with options to make a Audio or Data CD. Audio CDs are also recognized and I play them with no problems.

I have tested out different DVD-R brands(Memorex, Dynex, etc.) to see if that would be a factor but none have been detected. I have tested commercial DVD movies as well but they also aren't recognized.

My Drive brand:  HL-DT-ST 
Model: DVD+-RW GWA4164B

In case this is a factor:
I have a dual drive and my Sony DVD-ROM DDU1615 has no problems playing DVDs of any sort.

Anyone know why this is? Any solution? Thanks in advance. :)

---

### Post by Eastisle on 2007-07-21
anyone? could it be driver related?

---

### Post by geraldm on 2007-07-21
Possibly this is normal, your DVD burning application is just not starting automatically.
Can you burn from the command line OR by starting a DVD burning app? 

Gerald

---

### Post by Eastisle on 2007-07-22
Hi Gerald,  thanks for the reply. I've tried burning through the command line and tried using various burning applications but none detect the blank DVD-r. 

Any other thoughts?

This is what I get in the terminal when trying to burn using tovid:

ea@agent:~$ makedvd -burn "/home/ea/OUT_PREFIX"
--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.30
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
=========================================================
Please insert a blank DVD+/-R(W) disc into your DVD-recorder
(/dev/dvdrw) if you have not already done so.
expr: syntax error
(standard_in) 1: parse error
=========================================================
Found no disc in /dev/dvdrw. Cannot burn to this disc!
Found  no disc. Please insert a usable DVD into /dev/dvdrw.
Trying again in  1 seconds...
Looking for usable media...
expr: syntax error
(standard_in) 1: parse error
Found  no disc. Please insert a usable DVD into /dev/dvdrw.
Trying again in  1 seconds...
Looking for usable media...
expr: syntax error

---

### Post by Eastisle on 2007-07-28
Anyone else with ideas? Please..

---

