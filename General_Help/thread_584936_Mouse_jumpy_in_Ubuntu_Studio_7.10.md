---
title: "Mouse jumpy in Ubuntu Studio 7.10"
date: 2007-10-21
forum: General Help
---

### Post by iukekini on 2007-10-21
Please help, 

I have just loaded ubuntu studio 7.10. I love the way it looks and the features but I have one major problem. My mouse becomes VERY jumpy and shoty at best.

The mouse will work fine when the system loads. As soon as I start any program, doesn't matter which one the mouse will becomes very jumpy and and erratic. It acts like the system is bogged down. However, system monitor shows CPU usage at 10% core 1 and 3% core 2. I have 2 gb of ram, of which only a few hundred mb are being used.

The mouse is a USB optic mouse. and this issue does not happen on my XP boot


Any help on issue would be great.

---

### Post by mark_lar on 2007-10-21
Does this happen with every app or just some? And by the way, where did you get 7.10 from? I have 7.04 and can't see a obvious update on the site...

---

### Post by iukekini on 2007-10-21
happens with every program, unless its a system tool or system prefer. 
I got the iso from Canonical Hosted download link at ubuntustudio.com which is 7.10 gusty.

:confused:

---

### Post by por100pre1 on 2007-10-21
My question will seem to be dumb but, are you running the LiveCD or Ubuntu Studio installed in your PC?

---

### Post by iukekini on 2007-10-21
its installed

I am not aware of a live cd for ubuntu studio. But none the less, I did a fresh install for it on a 200 gb sata

---

### Post by iukekini on 2007-10-22
ok, so I since my post I have done the following:

Deleted the drive and (zero)0-ed the disk.
reinstalled Ubuntu Studio 7.10 only installing the software I will be using. 
Same issue happens, The mouse becomes very hit and miss with no major bogging on the system. The mouse just starts to suck. no matter what program I open.

My new question is, anyone else having this issue in Ubuntu STUDIO 7.10?

My next question is: anyone have a WORKING link for STUDIO 7.04 as per the official website only gives links to 7.10


HELP ME PLEASE

---

### Post by FlabbyCat on 2007-10-25
I've been struggling with a problem similar to yours.  The answer in my case is anti-climactic and probably not directly your answer but I might be able to give you a clue to discover your problem.

I've been using Ubuntu 7.04 on two machines.  One upgraded OK.  The other is an old Presario which has 'issues' with Ubuntu that I've mostly been able to work through.  It was unable to do the upgrade but I was able to have Synaptic mark all the updates and it updated everything so it looked like it was functioning almost identically to the computer that updated without any problems. (There may be differences but if I couldn't tell I don't care...I'll do a clean install one of these days anyway.)

Unfortunately I noticed the jumpy mouse and missed clicks problem much as you describe.  Looked like an interrupt conflict to me.   So I dug into my notes from when I originally installed Fiesty and had problems.   I got it to boot completely by adding the following boot options (via F6 on the livecd boot) 
acpi=off noapic

I don't fully understand the acpi or apic functions but interrupts are involved so I figured messing with the boot options might fix the mouse problem too.
So I've been using combinations of acpi=off,force,or noirq; noapic, irqpoll, and pci=conf1.   I list these not so you can try them but to give you some useful guidance for google searches because there are interrupt problems that these settings can solve.   Nothing solved my mouse problem.

In my case it turned out to be my wireless mouse.   Early on, I did swap the batteries but it didn't help.  The jumping and missed clicks go away if the receiver is right next to the mouse.  I got another mouse and it works fine.  Maybe it's a coincidence and the mouse just happened to fail while I was doing the upgrade...I think it has something to do with the upgrade though.   When I find my Fiesty LiveCd I'll load it to see if it has the problem and post the results.  

Hope this helps.

---

### Post by Therion on 2007-10-25
All I can add is that on Feisty I had no problem with my mouse.  On Gutsy, it was acting... Jittery for lack of a better word.  Like it was overdosing on caffeine or something.  It's hard to describe.  Jumpy, jittery, erratic twitching...  This was with any application from Open Office to Firefox.  Whatever you call it, it's hella-annoying.  

As for my solution, well, I happened to have a different mouse lying around, installed it and the problem disappeared.  Old mouse (the one with the problem) was/is a Logitech MX1000, while the older, non-problematic, mouse is a Microsoft something or other ... Just a simple, two-button jobber, with a scroll wheel.  Both are USB, optical.

---

### Post by por100pre1 on 2007-10-25
> **iukekini said:**
> its installed

I am not aware of a live cd for ubuntu studio. But none the less, I did a fresh install for it on a 200 gb sata

You are right, there's no US Live CD... :oops:

---

### Post by emarkd on 2007-10-26
Just wanted to chime in and say that I'm also having these issues on my desktop PC running Gutsy.  I can't tie it to a specific cause, but I know that it will happen when I've not touched the computer for minutes.  I'll just be sitting at my desk and all of a sudden Compiz's Expose thing will happen because my mouse is jumping around and has hit the hot-corner.  This happens with both a wireless usb mouse and a wired ps2 mouse.  No difference.  When it's happening, I can swap from one to the other and there's no change.  I can even restart X (ctrl, alt, backspace) and when GDM comes back up, my mouse is still going crazy.  I just rebooted for the first time in a week because of this problem.

---

### Post by ryanez on 2007-11-06
I have the same problem with Gutsy and Debian etch unstable. If I connect only the USB optical mouse, it behaves erratically and jumpy (the touchpad is working correctly), Only when I boot the laptop with the USB mouse and an USB hard drive connected, the mouse behaves correctly (and also the hard drive). When I disconnect the USB hard drive, in 30 seconds or so, the mouse, again, behaves strangely, Now, if I reconnect the USB hard drive, I don't recover the good behavior (neither of the mouse nor the drive).

I think it's a bug in the kernel (or in the xserver), as the behavior was correct under debian etch stable and in ubuntu edgy. When I updated to debian etch unstable (and the other partition to ubuntu feisty or gutsy), I started getting the bad behavior.

---

