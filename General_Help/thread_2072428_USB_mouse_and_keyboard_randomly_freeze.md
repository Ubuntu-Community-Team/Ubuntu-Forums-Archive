---
title: "USB mouse and keyboard randomly freeze?"
date: 2012-10-17
forum: General Help
---

### Post by xavieranderson on 2012-10-17
When I'm working for some amount of time (usually around 30 minutes) my mouse and keyboard completely stop working. I have to do a cold reboot to get it working again.

They are USB. I am running 12.04 64 bit.

I am a novice to linux, and I need help to troubleshoot this issue. This is obviously a large issue for me.

---

### Post by Dude-PWB- on 2012-10-17
I can't tell you what the problem is, or how to fix it, but I had this issue once before, and I'm not even sure how it fixed itself but instead of rebooting, have you tried to just unplug and replug the devices? Thats what i used to have to do however my issue didn't occur as often as yours seems to occur.

Maybe with that information someone with more knowledge might be able to help.

---

### Post by xavieranderson on 2012-10-17
Yes, I have unplugged and plugged it back in.
It gives me a little relief that this occurs to others.

Now I did have mint before, and it occured there as well. Is it an Ubuntu issue, since Mint originated from Ubuntu.

---

### Post by xavieranderson on 2012-10-17
I think it may be my SWAP file.

I have 8 gigs of ram, but my swap is only 500 mb.

---

### Post by 2F4U on 2012-10-18
> **xavieranderson said:**
> I think it may be my SWAP file.

I have 8 gigs of ram, but my swap is only 500 mb.

Unless the machine really needs that swap space, it is unlikely that this is the reason. I had problems with my usb keyboard too, and the simple reason was that the machine was under my desk. After attaching a cable to the receiver and putting on top of the desk the connection problems disappeared.

---

### Post by anderson123 on 2012-10-18
Hello Friends,

It's your PC hardware problem. please check it by good repair.

_________________________:guitar::guitar:_______________
----------------------------------_______________-----------------------
:popcorn::popcorn:

---

### Post by elytron on 2012-10-18
My mouse also freeze sometimes, it's quite annoying. When it happen I have to unplug it then plug in again. Also interested in a more permanent fix for this issue.

---

### Post by sienile on 2012-10-18
It's definitely a hardware problem. I used to have similar issues many years ago in Windows. My solution was to get a powered USB hub to plug them in to. My computer wasn't supplying the proper voltage to the devices, so the powered hub fixed everything.

---

### Post by xavieranderson on 2012-10-18
It happens more often now, but I have a lazer mouse that is still on when it freezes.
I dont have these issues with Windows 7, which is dual booted.

If this is a hardware problem, can I fix it? This is a 1000 dollar machine...

---

### Post by efflandt on 2012-10-18
I had a similar problem when I had a cheap video card (not the video chip maker, but the card maker Galaxie) that was past its 1 year warranty.  Although, symptoms in my case were that keyboard would freeze, mouse cursor would usually (not always) still move, but I could not click on anything.

At the time, it happened most frequently in 11.10 and did not seem to happen in 10.10.  But it would also sometimes freeze in Win7 and then Windows would say that the video driver stopped responding, but it recovered.  But I rarely ran Windows and eventually it started happening more frequently in 11.10 and in 10.10 as well.  I got a new quality video card (EVGA) with 3 year warranty and have not had a problem since.

Not that it is necessarily your problem, but sometimes the problem is not the hardware that seems to be glitching.

In a terminal read through:```
dmesg | less
```or the file /var/log/syslog to see if there are any errors that may give a clue.

---

### Post by Edith Abbott on 2013-01-02
Hello friends,

I have also face this problem. My mouse is stop working then i need to start my PC again. If I restart my PC after that mouse also not work. Why this problem come? suggest me and sole my problem.
:-({|=___________](*,)

---

