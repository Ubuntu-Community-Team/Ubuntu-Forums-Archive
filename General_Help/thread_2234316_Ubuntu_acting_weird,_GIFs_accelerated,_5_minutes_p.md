---
title: "Ubuntu acting weird, GIFs accelerated, 5 minutes pass like 1 minute."
date: 2014-07-14
forum: General Help
---

### Post by rodvaN on 2014-07-14
Hello guys..
I am new to this forum, but not new to Ubuntu.
I had a problem with my kern.log being flooded by a problem so I had to turn ACPI = off to debug.
I now solved that issue, but then several issues appeared:
[LIST=1]
[*]My keyboard suddenly repeats keypress like ttttttthhhhhhhhhhiiiiiiiiiisssssss  in just 1 second. I fixed that turning off they keypress repetition.
[*]GIFs get suddenly very quick, like 5x faster, then they stop and everything runs normal.
[*]Also the clock runs 5x times faster, then it runs normal.
[*]When all that happends, flash also bugs out and sound its the only thing that runs normal, flash then get 5x faster and then comes to track again.
[/LIST]

Ive been trying to google out what could be the issue, but cannot find the problem.
My kern.log doesnt register any problem when that happens.

Anyone knows what could be happening with my Ubuntu installation?

---

### Post by tgalati4 on 2014-07-14
Sounds like a motherboard issue.  The kernel isn't logging issues because none of the modules are sending errors, just running faster.  It's possible that you have a faulty real time clock (rtc) or front side bus (fsb).  What is the make and model of this computer?

Boot into BIOS and try declocking.  Slowing the computer down will sometimes fix this issue--at least give you a clue that it is clock speed related.

---

### Post by rodvaN on 2014-07-17
Its a Dell Precision M4600
So I boot into BIOS, I will have to google what is declocking.

---

### Post by tgalati4 on 2014-07-18
Look for settings in BIOS to slow the CPU down.  Because this is a large, high-performance laptop, it is susceptible to dust causing issues--it is running at the limits of what is possible in a laptop, so any dust on the motherboard can cause problems.  It might need cleaning.  How old is it?

The other issue is the large size.  Dell is not known for building robust laptops--they tend to fall apart just by looking at them.  If the chassis has flex in it, that can cause problems with the motherboard flexing and strange problems.  Does the behavior change if you try to bend/flex the chassis?  Put a pencil under it at different locations and see if the bottom part of the laptop bends and if the behavior changes.  Is it under warranty?  How often is is moved?  Is it a daily commuter?

---

