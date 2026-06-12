---
title: "Battery issues"
date: 2008-03-31
forum: General Help
---

### Post by Tom--d on 2008-03-31
When I turn off my laptop (With 100% battery power) in the morning I have around 83% battery power. 

I've taken out the battery when at 100% and in the morning it is still at 100%

Ubuntu knows the details of the battery and all that.
My laptop is a Toshiba A200 1VO

Its never done this in vista when I had it. 


What does Ubuntu do when its off?

---

### Post by Slushdoot on 2008-03-31
This is quite odd.  When it's *off* it should do absolutely nothing.  Perhaps the issue is related to a "Wake On..." setting found in your BIOS.  The OS, however, shouldn't have changed anything related to that.

It might sound silly to ask, but you are turning it completely off, right?  Not suspended to RAM?

---

### Post by Tom--d on 2008-03-31
Its turned off completely. 

I will check the BIOS in a min.

---

### Post by Tom--d on 2008-03-31
Wake on LAN is disabled
Wake on wireless LAN is disabled

I do not need them.

What might be causing this?

---

### Post by Tom--d on 2008-03-31
Anyone?

---

### Post by nickoli_02 on 2008-03-31
You've got to be suspending to some sleep state and not a full shutdown. As an experiment, try issuing a shutdown from a terminal and see if your battery still drains.

```
sudo shutdown -h now
```

---

### Post by Tom--d on 2008-04-02
Will do when my battery is full.

---

### Post by Tom--d on 2008-04-06
Nothing,
It is says 80 odd % left of my battery when in the morning. 

I unplugged everything (Mouse and external speakers and still it is draining away) 

What is causing it. It cant be my BIOS as when Vista was on the laptop, it never did it. (or that I never noticed) 

What might be casuing it?

---

### Post by nickoli_02 on 2008-04-06
you did shutdown -h now, and your battery is still being drained? hum, I'm stumped. That should issue a complete shutdown of your system. 

I don't suppose you can open up your laptop and probe some points with a voltmeter?

---

### Post by Tom--d on 2008-04-13
Yep. it still does it even after shutdown -h :(

---

### Post by Tom--d on 2008-04-13
AlsoI got a free battery from Toshiba and I tried that one. It still does it. So its not the battery which is doing it.

---

