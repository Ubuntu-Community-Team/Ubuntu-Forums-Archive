---
title: "Have I Been Hacked ??"
date: 2023-03-13
forum: General Help
---

### Post by box02-0 on 2023-03-13
Ubuntu 22.04   Unity 7.50
American Megatrends BIOS

Today I was playing around installing Mate for desktop. I didn't like it, logged out, and went back to Unity. All looked AOK.

Afterwards I booted and got the following BIOS message:
ASUS Z97 Pro
ACPI BIOS revision 3503 (latest rev)
Detected ATA/ATAPI devices....
Please enter Setup to Recover

I went into the BIOS and found all my Drives were ENABLED where I usually only have Drive 1 ENABLED. I also noted that "Intel Virtualization Technology" was DISABLED when it was always ENABLED. Who know what else was "touched".

I saved the changes and let the system reset. I powered OFF then ON the system, and back came the BIOS message as above.

I can repeat this process multiple times with my modem powered OFF (in case the BIOS is going out to the internet). All this without even bringing up Ubuntu.

So after a while I decided to go into Ubuntu - all looks AOK. However, if I power down and back up, I'm greeted once again with the BIOS message.

Has my BIOS been hacked ?? Tomorrow I will try updating the BIOS and see what happens. It's late and I don't want to play around any more. I just will make this post and see if anyone has any ideas.

Thanks,
M...

---

### Post by QIII on 2023-03-13
Actually, my first question would be:  When was the last time you replaced your CMOS battery?

Did you remove MATE?

---

### Post by MAFoElffen on 2023-03-14
+1 To suspecting that it is either the CMOS battery being dead, or it having a bad connection in it's mount.

---

### Post by box02-0 on 2023-03-14
Thanks for the prompt response. I will check out the CMOS ASAP.

I didn't remove mate as I had backed up prior to installing it. I just restored.

FYI: I was playing around with GNOME instead of Unity a lot. Now back to Unity. Can't imagine this caused the problem.

Have you ever heard of a hack like this? There were Intel vulnerabilities a while ago, and my AMIBIOS is from 2014.

Okay it's time to change the CMOS.

Will keep you posted.

Thanks so much,
M...

---

### Post by box02-0 on 2023-03-14
THANKS :P. Battery was original from 2014 - was 1.2 volts. New one is 3.2 volts. It's all good.

How do I thank you? You made my day. That was the last thing I would have thought of.

Have a nice day - you made my day,
M....

---

### Post by oldfred on 2023-03-14
I had that motherboard until drive crashed & could not get back into system.
Drive crash I believe was caused by other motherboard issues, but do not know for sure.

But that motherboard always reset all the UEFI settings to defaults with UEFI update.
I had a long list of UEFI settings I had to redo to have it the way I wanted.

I looks just like you UEFI settings went back to defaults.

Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by MAFoElffen on 2023-03-14
Please go to the "Thread Tools" link in the upper right of this page, and mark the threas as "Solved"... So other mat find your solution to help others.

---

### Post by box02-0 on 2023-03-15
Hi.
I already marked it as solved yesterday and the thread does show "solved". Is that not okay?
Thanks,
M...

---

### Post by DuckHook on 2023-03-15
> **box02-0 said:**
> Hi.
I already marked it as solved yesterday and the thread does show "solved". Is that not okay?
Thanks,
M...
Everything is good.

Glad that everything worked out for your.

Good Luck and Happy Ubuntu-ing!

---

