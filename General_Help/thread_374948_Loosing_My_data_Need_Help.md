---
title: "Loosing My data Need Help"
date: 2007-03-03
forum: General Help
---

### Post by cameron_diaz on 2007-03-03
On at least two occasions I have heard a sort of clicking noise (one or two at the most) coming from my pc. I have a 40 GB hd primary and a 160GB ide hd slave. I'm not sure if this is my hard drive failing. I have listened to the "failing hard drive" samples on I think maxtor or sony's site and the first sample sounded similar to the noise I heard, only the noise didn't repeat over and over, it just sounded once or twice really quickly. 
Also, my system has been crashing and I don't know if this is because of a program I installed or if it is my hard drive actually starting to fail. Is there a way to check what is causing it to crash? If I post the error report the next time it crashes, would someone be able to decipher what the cause is?

---

### Post by kidders on 2007-03-03
Hi there,

This doesn't sound good. :-(

If this happened to me, the first thing I would do is check my system logs. You may find that some of them complain about I/O errors, or moan about devices resetting. If you see anything like that, please post the messages. (They may be quite long.)

Without more information, I would guess that there are two possibilities:

**I - Drive failure**
As you suspect, one or both of your hard drives could be dying. Your system logs should tell you which one(s). Depending on exactly what's going on, it *may* be possible to continue using them. Either way, I would make backups of important stuff right away.

**II - Power-related problems**
Power to your drive(s) may be momentarily cutting out, which might cause them to make a clacking sound, and then reset themselves. (You would hear a noise similar to how they sound when you turn on your PC.) In this case, I would open my box, check _all_ the connections (even the ones that don't plug into my disks), and consider the possibility that my power supply could be dodgy.


Some additional questions:

[LIST]
[*]Are you actually losing data?
[*]Is your kernel panicking?
[*]What processes are affected by the hard disk problems (if any)?
[/LIST]

Your system logs can answer these questions for you. Basically, depending on what's going on, it *may* be advisable to reboot immediately whenever your hard disks go all weird on you, and I'm wondering what to advise.

I would certainly recommend using your hard disks in read-only mode as much as possible. That won't be possible in day-to-day operation, but if, for instance, you decide to make backups, you should boot from a live CD and manually mount your hard disks with the **ro** mount option. That would also be a good opportunity to **fsck** them (scan them for errors), which you should _never_ do while booted into your internal Ubuntu install.

I hope this is of some help. Btw, have you recently had reason to play around inside your box, or move it around more than usual?

---

