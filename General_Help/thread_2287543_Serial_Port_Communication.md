---
title: "Serial Port Communication"
date: 2015-07-20
forum: General Help
---

### Post by Zach_Follette on 2015-07-20
Hi Guys, 

I'm stuck in a bit of a conundrum with serial communication. I have a desktop running Ubuntu 14.04 with 4 serial ports in it. The serial ports are on PCI slots, if it matters. Also they are 9 pin male. The device I am trying to communicate with is a Haas CNC machine panel with a 25 pin female port. This device takes commands such as Q100, Q200, etc... I am having trouble with communicating with this panel. I have tried minicom, gtkterm, and just using the terminal with echo and cat but nothing seems to work so far. I am getting no errors when I try these methods, just no response. All of the appropriate settings are enabled on the CNC panel.

So, is there any tips anyone can give me about sending simple strings over serial ports?

Thanks.

---

### Post by Lars Noodén on 2015-07-20
What about on the client?  Are you using the right configuration?  8N1 is common.  What about the speed?

---

### Post by Zach_Follette on 2015-07-20
I am using 9600 7E1 which is how the CNC panel is set up

---

### Post by tgalati4 on 2015-07-20
Welcome to the forums.

Typically there is a wakeup or status command.  You send the sequence and you should get a "ready" response.  What is that command?  Do you have the Haas command listing?

How do you have your 9-pin-to-25-pin cable set up?  Some machines use a proprietary cable with resistors, diodes, and cross connections, so using a straight through serial cable may not work.

---

