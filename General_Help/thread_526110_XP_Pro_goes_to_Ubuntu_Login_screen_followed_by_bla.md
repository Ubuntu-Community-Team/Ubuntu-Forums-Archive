---
title: "XP Pro goes to Ubuntu Login screen followed by black screen with white text  etc...."
date: 2007-08-15
forum: General Help
---

### Post by 2percentright on 2007-08-15
This is my first post, so bear with me.

I'm writing this entry since I couldn't find a single thing here or on google.

I was on XP Pro.  Was turning in for the night to try and get some sleep.  Xp had gone to its screen saver.  This was at least a minute.  Of a sudden, I notice that it got suddenly brighter in my room. XP does this often. It will go to screen saver, then, after a bit, will go back to showing the desktop.  So, sleeply I thought it had done this again.  But I then noticed that the color was all wrong. I roll over to see the Ubuntu login screen showing! I get over to my desk and confirm that Ubuntu has somehow started without restarting the computer, logging out of XP pro, or booting up Ubuntu.  I run back to my bed to grab my glasses and turn back to see the screen go black with several lines of white text on the screen, as I go back to the desk, the text gets larger and large, as though zooming into the text until eventually, my whole desktop just shuts down.

Now, 
A) It's very late
B)I'm tired
C)I had a low blood sugar
and
D)I suffer from a very low level paranoia.  

Needless to say, I proceeded to unplug every single PC related item, and completely removed my router as well.  (cough)then proceeded to pull my harddrives, but ignore that)

Far as I know, it is completely impossible to go from one, RUNNING, OS to another in a blink of an eye.


Some info on my system

I have two hard drives. One is strictly XP Pro.  The other is strictly Ubuntu.
XP can not even see the other harddrive.
XP profile was limited powers.
Ummm...
Running a 4 year old Athlon 32 bit.
What else am I forgetting?

So...like I said. I'm completely freaked out. I have no idea what's going on. If this is some kind of crazy interaction between the two OS's which is causing a Kernal Panic (see, I read, sometimes) or what.

Feedback?  Should I write up a bug report? what should I do?  I'm at a loss.

like I said, I looked on Google, and this forum for more than an hour and couldn't find a damn thing that came even close to describing my situation.

---

### Post by shad0w_walker on 2007-08-15
Is Ubuntu your default option in grub? If it is then XP might simply have crashed out, rebooted and you would have gone to Ubuntu.

As for the kernel panic logs would probably be quite useful in figuring that out.

---

### Post by kellemes on 2007-08-15
> **shad0w_walker said:**
> Is Ubuntu your default option in grub? If it is then XP might simply have crashed out, rebooted and you would have gone to Ubuntu.

As for the kernel panic logs would probably be quite useless in figuring that out.

Great story..
Trying to extract the most relevant info, I see XP restarted for whatever reason (is possible) and PC booted into Ubuntu, correct?
Up to now not problem it seems, well, except for XP restarting that is..

As previous poster I wonder how your Grub looks, probably one of your Ubuntu-kernels is default.
Now, I assume you can boot into Ubuntu? Or am I missing something here?
So the problem is the growing text.. Can you startup X at all? Or what's going on here..
Try to startup X and explain the problem please..
Don't forget to investigate (maybe post) /var/log/Xorg.0.log

---

### Post by 2percentright on 2007-08-15
> **shad0w_walker said:**
> Is Ubuntu your default option in grub? If it is then XP might simply have crashed out, rebooted and you would have gone to Ubuntu.

As for the kernel panic logs would probably be quite useful in figuring that out.

Well...ok. Assuming that I somehow completely missed XP crashing, my computer restarting...on its own, and Ubuntu booting up, what the heck was the text?

You ask for a log. Ok. What command do I need to run?

---

### Post by 2percentright on 2007-08-15
> **kellemes said:**
> Great story..
Trying to extract the most relevant info, I see XP restarted for whatever reason (is possible) and PC booted into Ubuntu, correct?
Up to now not problem it seems, well, except for XP restarting that is..

As previous poster I wonder how your Grub looks, probably one of your Ubuntu-kernels is default.
Now, I assume you can boot into Ubuntu? Or am I missing something here?
So the problem is the growing text.. Can you startup X at all? Or what's going on here..
Try to startup X and explain the problem please..
Don't forget to investigate (maybe post) /var/log/Xorg.0.log

Yeah. Grub is set to boot to Ubuntu if I don't choose.  But I swear, the damn thing went from black screen saver to Ubuntu log-in with in seconds.

I wasn't THAT tired. (I've been having some insomnia problems recently.)

---

### Post by 2percentright on 2007-08-15
OK. Update.

XP updated last night. I MUST have drifted off and woke up to Ubuntu as it restarted.

Though that doesn't really explain away the crazy crash that occurred on the Ubuntu login screen.

---

### Post by kellemes on 2007-08-16
/var/log is the directory where logfiles are.. always interesting to investigate.

---

### Post by 2percentright on 2007-08-16
> **kellemes said:**
> /var/log is the directory where logfiles are.. always interesting to investigate.

Which log you want to look at? theres logs all over the freaking place in /var/log

---

### Post by kellemes on 2007-08-17
Well, most graphic-related issues are in Xorg.0.log.(old)

---

### Post by 2percentright on 2007-08-17
> **kellemes said:**
> Well, most graphic-related issues are in Xorg.0.log.(old)

Hmmm...I tried to copy/paste the log in here, but I got an error about including too many images.

:-/

Not sure what to do to show the log.

---

