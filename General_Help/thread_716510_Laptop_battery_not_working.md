---
title: "Laptop battery not working"
date: 2008-03-06
forum: General Help
---

### Post by Jackle on 2008-03-06
Hi, I recently installed ubuntu 7.10, and was loving it until I wanted to use the laptop on battery power. The computer just died, ubuntu would not recognize the battery. I then booted up windows, same thing happened. Does anyone know what the problem is? The battery will not work for either windows or linux. The laptop is a vaio vgn-c140g if that helps. Much thanks.

---

### Post by TigerWolf on 2008-03-06
Could the battery be dead? Batteries after a while can stop working. How old is it?

---

### Post by Jackle on 2008-03-06
The computer is like 1 year old, and rarely on battery too. Im in xp right now, and it doesn't recognize the battery at all. I'm decent with computers, but I wouldn't think that installing ubuntu on another partition would affect the battery at all, on xp even. So what do you think I should do? If i use my windows recovery discs, will it remove the ubuntu partition and give me a clean slate? I have a 3 year warranty from best buys on this laptop, so if the battery still doesnt work, i can give it to them and tell them to replace it or something.

---

### Post by Bubba64 on 2008-03-06
This may of no help but there may be a place where you live that will test your battery and if your computer is charging it.

---

### Post by Distro Jockey on 2008-03-06
> **Jackle said:**
> The computer is like 1 year old, and rarely on battery too. Im in xp right now, and it doesn't recognize the battery at all. I'm decent with computers, but I wouldn't think that installing ubuntu on another partition would affect the battery at all, on xp even. So what do you think I should do? If i use my windows recovery discs, will it remove the ubuntu partition and give me a clean slate? I have a 3 year warranty from best buys on this laptop, so if the battery still doesnt work, i can give it to them and tell them to replace it or something.

Batteries usually only have a 1 year warranty, even if the notebook has a 3 year warranty.
As neither OS is seeing the battery, I would try disconnecting it, check the contacts and then reconnect it.
The following link has some tips on extending the life of a battery:
[http://labnol.blogspot.com/2006/03/10-tips-to-make-your-laptop-battery.html](http://labnol.blogspot.com/2006/03/10-tips-to-make-your-laptop-battery.html)

---

### Post by Jackle on 2008-03-06
ill check the contacts now, but look what the warranty says

"This Plan provides battery repair/replacement for notebook computers, cellular and PCS phones when original is determined defective by us."

And also, installing ubuntu in the first place wouldn't have caused this would it? I mean, what the hell, the two shouldn't have any connection? Because windows xp can't see it either.

---

### Post by Distro Jockey on 2008-03-06
> "This Plan provides battery repair/replacement for notebook computers, cellular and PCS phones when original is determined defective by us."
That's an interesting quote with a couple of different meanings I guess. Definately worth using if you do need to replace it though. :)
As for installing Ubuntu causing the issue, I very much doubt it.

---

### Post by Jackle on 2008-03-06
I've heard a lot of bad things about best buy, would they void the warranty if they saw the ubuntu partition or anything?

---

### Post by Distro Jockey on 2008-03-06
I take it that taking the battery out and putting it back in (re-seating) did not resolve the issue?
I did a bit of a google and there is no evidence (I searched for "ubuntu laptop battery", but didn't dig too deep) of Ubuntu killing batteries, the majority of results were related to the battery being drained quickly (for which there are work-arounds).
With Best Buy, I guess it depends on what they consider defective to be and within what time frame said defectiveness occurred.
What OS you have on there should be none of their concern.

---

### Post by UBUSNAFU on 2008-03-06
You could also try booting on battery to a DOS CD or floppy, maybe a live CD version of Linux. If it wont do that then the battery is most likely to blame.

---

### Post by nlong on 2008-03-06
It's nearly impossible that Ubuntu had anything to do with not being able to run off battery power.  You might find an ignorant Best Buy employee that would blame it on Ubuntu, but changes are you'll be ok.  They replace batteries frequently for laptops covered under their warranty.

---

### Post by Jackle on 2008-03-06
the comp wont turn on on battery, like after i removed the power cable, it just turns off, and wont turn on until plugged in again. I just don't want bb to shaft me.

---

### Post by Distro Jockey on 2008-03-06
After you re-seated the battery, when you plug in your AC adapter, do you get the usual battery charging light that I presume you used to get?
In Ubuntu, if you go to /proc/acpi/battery (by "cd /proc/acpi/battery" in terminal or by browsing), are there any files in that directory? (I must admit, that I do not have a laptop and can only assume that, if the battery is connected and detected by Ubuntu that there should be something in this directory. Same with /proc/acpi/ac_adapter .)
As I have never had a laptop with Ubuntu, someone else may wish to shed some light on the /proc/acpi entries. :)

---

