---
title: "Stuttering keyboard issue"
date: 2007-08-02
forum: General Help
---

### Post by Mascot on 2007-08-02
I find this pretty peculiar. It's as if, every 2-3 seconds, something occurs that delays a keystroke. As if it sticks in a buffer somewhere before getting passed on.

It's consistent at every 2-3 seconds and occurs whether I type fast or slow. Though it's obviously more noticeable at regular touch speed. It does not happen if I hold a key down and just let it repeat.

It's completely application independent. It happens on the login screen even.

I found another thread that suggested watching the interrupts to see if it coincided with activity there, it does not. I'm at a loss as to how to troubleshoot this further. Any suggestions?

Less than a week old 7.04 installation on an Asus G1 laptop
Intel Core Duo T7200 2.0GHz Processor
Mobile Intel 945PM Express Chipset ICH7M (chipset info off a webpage so might not be accurate)
NVIDIA GeForce GO7700

---

### Post by Mascot on 2007-08-02
Well isn't that just typical. Pretty much as I hit submit on the previous post, the update notification popped up. A handful of opengl related stuff I believe. 

I've since rebooted twice and the problem has yet to manifest itself again. Keeping fingers crossed whatever it was got sorted with that update.

---

### Post by Mascot on 2007-08-02
False alarm, unfortunately. Two more reboots later and it's back again.

When I wrote the original post I was trying to remember if the issue arose on every boot or not. At least that part is answered. Whatever goes wrong does so when booting, and while it's consistent once fully started, it varies at boot time.

Which only serves to further complicate things I guess.

I've now saved this startup's dmesg and will do the same once I produce one that's ok. Hopefully there's some discrepancy.

---

### Post by Mascot on 2007-08-04
Too many things are the same just loaded in a different sequence to be able to effectively diff the two. At least for me with no clue what to look for.

Any purpose in posting them here? Considering the lack of response I'm guessing it's a rare or unique problem. While it may seem like a detail it's a show stopper for me. I didn't spend a few thousand bucks on a computer to have it not be able to keep up with me while I type :P

---

### Post by Mascot on 2007-08-13
I guess that concludes my Ubuntu experiment until next release. I'll leave the thread watched and partition intact on the off chance someone should encounter the same, manage to solve it, and stumble upon this thread.

---

### Post by wolfger on 2007-08-15
I thought this was just a Gentoo/Sabayon issue... Sadly, it happens for me with Feisty as well. In Gentoo, I gotttttttt rid of it by enabling the "nptl" use flag and recompiling.......... Not really an option with Ubuntu. Very freaking annoying. Mepis 6.5 (Dappeeeeeeer base) does not havvvvvvve this problem.

---

### Post by buffalo2001 on 2007-08-28
I am having the same problem and have no idea how to fix it.  This is my first experience with Ubuntu and it's been okay so far but this is just aggravating.  It's not the keyboard (since it will work just fine in XP) and it is very intermittent.  It started after a bunch of updates and a ndiswrapper wireless driver install and then went away until I tried to use the ATI Linux driver.  ARGGGGH!  Hope someone can help with a fix or maybe this is a genuine bug.

---

### Post by zachtib on 2007-08-28
i think i have a related problem

in quake4 on linux, if i hold down 'W', every couple of seconds my character stops moving for a split second, then keeps going

i have a logitech wireless mx3100 combo

---

### Post by bean77 on 2007-09-02
I am having this issue too.  Conversely, there are times I have to pound on a key to get it to type.  So annoying!

---

### Post by Mascot on 2007-09-03
> **zachtib said:**
> i think i have a related problem

in quake4 on linux, if i hold down 'W', every couple of seconds my character stops moving for a split second, then keeps going

i have a logitech wireless mx3100 combo

Yup, that sounds like the exact same issue. You might just not notice it's present when typing as well, would be my guess. Cause for me, when it does appear, it does so even when I type my login name. It's readily apparent if I just keep hitting two keys repeatedly. Within a second or two I can see the momentary pause. If I keep rebooting I eventually get lucky and get a startup without the issue.

In my case I get it even without external keyboard/mouse connected, so doubt it's a compatibility issue with your Logitech stuff.

I installed Ubuntu primarily to have an environment without temptation (read: games) to write in. The irony of everything else that normally has failed for me when trying to use Linux on the desktop (sound, networking, proper graphics drivers) working just fine, but not being able to type properly, does not escape me.

I just boot it up once a week or so to keep it updated now.

---

### Post by zachtib on 2007-09-04
> **Mascot said:**
> Yup, that sounds like the exact same issue. You might just not notice it's present when typing as well, would be my guess. Cause for me, when it does appear, it does so even when I type my login name. It's readily apparent if I just keep hitting two keys repeatedly. Within a second or two I can see the momentary pause. If I keep rebooting I eventually get lucky and get a startup without the issue.

In my case I get it even without external keyboard/mouse connected, so doubt it's a compatibility issue with your Logitech stuff.

I installed Ubuntu primarily to have an environment without temptation (read: games) to write in. The irony of everything else that normally has failed for me when trying to use Linux on the desktop (sound, networking, proper graphics drivers) working just fine, but not being able to type properly, does not escape me.

I just boot it up once a week or so to keep it updated now.

i solved my problem. i have a keyboard/mouse combo that share the same usb port, turning off the mouse and using a separate mouse solves the issue, the kb and mouse must have been conflicting for use of the single usb port

---

