---
title: "fax device error"
date: 2012-10-27
forum: General Help
---

### Post by RogerDavis on 2012-10-27
I'm having a major battle with efax-gtk, with the following results:
===================================================
Socket running on port 9900
efax-0.9a: 02:23:07 opened /dev/ttyS1
efax-0.9a: 02:23:07 failed page /home/roger/Documents/Libre Office/Saddleback Labs Request.pdf.001
efax-0.9a: 02:23:07 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:07 Error: fax device write: Input/output error
efax-0.9a: 02:23:09 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:11 Error: fax device write: Input/output error
efax-0.9a: 02:23:13 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:13 sync: dropping DTR
efax-0.9a: 02:23:13 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:14 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:16 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 sync: sending escapes
efax-0.9a: 02:23:18 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:18 Error: fax device write: Input/output error
efax-0.9a: 02:23:19 Error: fax device write: Input/output error
efax-0.9a: 02:23:21 Error: fax device write: Input/output error
efax-0.9a: 02:23:23 Error: sync: modem not responding
efax-0.9a: 02:23:23 Error: tcgetattr on fd=8 failed: Input/output error
efax-0.9a: 02:23:23 finished - unrecoverable error
========================================================
How do I correct these errors in the code operation?  I know efax-gtk works, these errors probably result from trying to give myself permission to use the serial port.  That denied permission problem is apparently a bug in Ubuntu.

I used this to try to give permission :
sudo adduser MyUser dialout
sudo chmod a+rw /dev/ttyUSB0

Also :
roger@roger-desktop:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.448980] 0000:04:01.0: ttyS4 at I/O 0xd000 (irq = 17) is a 16550A

---

### Post by RogerDavis on 2012-10-27
Now I get 

Socket running on port 9900
efax-0.9a: 14:25:32 opened /dev/ttyS4

with no modem sounds, no activity I can tell.  It will sit there forever, no change.  The light never goes "green".

---

