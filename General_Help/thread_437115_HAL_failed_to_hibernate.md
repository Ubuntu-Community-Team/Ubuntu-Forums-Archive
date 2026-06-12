---
title: "HAL failed to hibernate"
date: 2007-05-08
forum: General Help
---

### Post by rygar on 2007-05-08
I've noticed ever since I installed Ubuntu, I've been getting errors when I resume from hibernation ("HAL failed to hibernate")

I searched around on the forum, and this seems to be an issue with a bunch of people.  However, I'm wondering if I 'm really having the same problem, and really if this is an issue at all.

When I resume from hibernation, my computer has a black screen for a few seconds, followed by a password prompt.  I enter my password, and I am presented with gnome (and the error message), and I can continue running Ubuntu with no ill-effects.

The point is, I seem to hibernating fine.  But I've never used Ubuntu before, so maybe there's something I'm missing.  Can I ignore this error?

---

### Post by rygar on 2007-05-09
no?  if anyone wants to just tell me its not harming my computer and i can keep on doing this, i'd be satisfied!

---

### Post by spankymasterc on 2007-05-09
dude dont start yelling and use google my friend 

as for your problem i found that a bug has been sent to launch pard so relax....

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/68258](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/68258)

---

### Post by rygar on 2007-05-09
not yelling, just asking!
tried google, couldn't find a solution.

also, that bug does not fit the description of my problem.  my computer does not wake up by itself, as in the bug description.  and when i resume, my programs are just as i left them.  in fact, it seems to work pretty well--except that it gives me an error message, and that worries me.

---

### Post by Stefan Björk on 2007-05-10
Actually, there seem to be a lot of issues with Feisty and hibernation... I whish there would be somewhere to summarize all the different problems.

---

### Post by rygar on 2007-05-11
hmm i've seen to make things better and worse

the bad news, i seem to be getting the error described in the launchpad bug listed earlier when i close the lid or press "hibernate" from the shutdown menu.

the good news is, if i type "sudo hibernate", it hibernates correctly and resumes without error.
how can i re-wire the lid-close or the hibernate button to do "sudo hibernate"?  i even tried creating a launcher on the desktop that runs "sudo hibernate", but that does nothing.

for now, i'll just type in the command.

---

### Post by Stefan Björk on 2007-05-13
'sudo hibernate' works for me. However, the computer resumes when I close the lid... :-(

---

### Post by rygar on 2007-05-13
here's what i ended up doing, this might work for you too:

sudo cp /etc/acpi/lid.sh /etc/acpi/lid.sh_backup
gksudo gedit /etc/acpi/lid.sh

delete everyting that's there and replace it with this:

```
#!/bin/sh
  sudo hibernate

```

now hibernate works fine on lid close!  i assume the hibernate button will fail on me, but i havent tried since i dont really use that anway.  and if you did, you can probably just do the same to hibernatebtn.sh or whatever it's called (ls in /etc/acpi for a list of actions)

---

### Post by Stefan Björk on 2007-05-14
My problems with hibnernation are these:

1. Hibernation sometimes fails when pressing the power button, closing the lid or chosing "hibernate" from the menu. The computer ends up with keyboard completely locked.

2. Hibernation seem to work all the time when I use 'sudo hibernate'. At least, it has not failed yet.

3. When computer is hibernated or shut down (no power), it sometimes starts up when the lid is closed (or opened), which is not good - if I hibernate with 'sudo hibernate' I would like to be able to close the lid and bring the computer with me. This problem sometimes occurs when the computer is shut down, not only hibernated, and at one occation the computer started up when I plugged in the chord. It seems that the computer resumes on arbitrary ACPI events...

Stefan

---

### Post by rygar on 2007-05-14
did you try what i said?
i was also only able to hibernate via sudo hibernate.

the reason your computer is waking up on lid close is because it's supposed to.  normally, i'll close the lid to hibernate, and when i open it up, it should resume.  in lid.sh it checks your computer status and says "hey, im already hibernating and the lid button was pushed--so i'll wake up".

of course, now i have it set so that i have to manually hit the button when i open the lid, but its not a big deal for me.  if you want to stop other acpi events from interrupting, just "sudo mv /etc/acpi/event /etc/acpi/event_backup", so long as its not vital to your computer's operation.

---

### Post by amadeus266 on 2007-06-28
My desktop gives the same message but I have not seen any ill-effects. I have it set to hibernate automatically when idle for 1 hour, and I have to hit the power button to turn it back on. Just an annoyance as far as I can tell. I have had it set up this way since I fist installed Feisty back in April. It would be nice if it didn't come up anymore though. Now that I think of it, I have an ATI AIW 9200 and seem to remember having hibernation issues with the driver in Windows XP.
 "A driver is preventing your computer from entering standby or hibernation. Contact the vendor of the driver for an update to correct this problem."
 If I disabled the specific driver (don't remember exactly which one it was now) the problem was solved. I wonder if this is also an issue under Ubuntu. I'm not a programmer and still somewhat of a noob so I have no Idea how to troubleshoot it in Linux. I am, however, convinced that this is actually a hardware problem.

---

