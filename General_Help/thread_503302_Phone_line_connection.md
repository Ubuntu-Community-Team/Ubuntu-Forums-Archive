---
title: "Phone line connection"
date: 2007-07-17
forum: General Help
---

### Post by bomb-24 on 2007-07-17
I have a dsl hookup for my high speed internet. I have a new modem that takes a regular phone line in the back, then the enthranet line that goes from the modem to my computer. I have a program that requires use of a telephone/dial tone. Do I need to connect a direct telephone line in the back of my computer? Or do I have access to dial tone with my modem? I am very new to linux and I am still getting use to it. Can anyone help?

---

### Post by scrooge_74 on 2007-07-17
Sounds like you have one of those usb/DSL modems which in windows you use a driver in the CD to get it working

On linux there are a couple of steps but it depends on the brand name.  I have the same issue when starting and in the end I just ended bugging my provider for a DSL modem with ethernet ports which in the end was better because latter i got myself a wireless router

---

### Post by Bartender on 2007-07-18
> **bomb-24 said:**
> I have a dsl hookup for my high speed internet. 

I have a program that requires use of a telephone/dial tone. 

I don't get it.  What program would require a dial tone?

Anyway.  If you need dial tone for some reason, take the dsl modem out of the loop.  Plug the telephone cord directly to the PC's modem port, not the ethernet port used by the DSL modem.

Wait a minute.  If you now have an ISP that's supplying a DSL feed to your house, that means you no longer have a dial-up service, correct?  Even if you had a Linux-compatible modem, set up the Linux dialer correctly, and dialed out, the modem wouldn't get an answer because you don't have an ISP server waiting at the other end of a phone number.

Correct?

---

### Post by scrooge_74 on 2007-07-18
i imagine the program he refers to is for windows to configure the DSL/modem.  I had in the past used one of those Speedtouch, DSL/USB modems.  Which require to install drivers and then a program to manage the modem.

You can't log in to internet by just using a regular modem, because those DSL modem dont need to dial anything, the moment it is up and running he gets and IP address and you can still use your phone line.  In Linux those USB modem are hard to configure even the Speedtouch because you need some input from your ISP (in my case Cable & Wireless).  But I told them to change it to a DSL/ethernet modem which gives me 4 ports for other PCs and I then added a wireless router on top.

A couple of days earlier they call to offer me an upgrade so I can have 1000 mbs download speed on the same modem and phone line.

---

