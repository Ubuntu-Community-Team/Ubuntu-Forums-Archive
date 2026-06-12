---
title: "Sleep Error Loud Beeps"
date: 2008-05-19
forum: General Help
---

### Post by MattressVon on 2008-05-19
I upgraded to Hardy Heron a few weeks ago and am digging it. Everything has worked great out of the box except sleep, hibernate, and suspend. When i attempt to hibernate my machine it goes to a black screen with a flashing cursor and will not respond to my keyboard or power buttons at all. i have to do a hard reboot to get my system back. When i put my display to sleep it does not wake back up no matter what i do, and there is no response to my keyboard. 


When i do S3 suspend it suspends just fine occasionally display a series of vertically striped gray bars before going to sleep. but when it resumes it issues a series of very loud beeps that are random and usually occur in 4-5 beep burst. It only does this when it's suspended for several hours. After i log back in, everything works fine except i get a message in the lower right hand corner telling me that sleep failed and to consult a help page that has no useful information on it.

I have spent the last week searching and have found nothing on any of this. there are some similar errors on launchpad and in the ACPI kernal bug archives but nothing that matches any of it explicitly. my system is an intel core 2 duo 2.66ghz conroe processor with 4gb ddr2 800 ram, 1 tb hard drive space, Ati radeon 1650 extreme graphics card pci-e 16, gigabyte G33m-DS2 mother borad and atheros dlink wireless card. I have a usb keyboard if that matters. my bios are current and support suspend to RAM and i have an intel ich9 sata achi controller.

Any thoughts, tips, or info I overlooked?:confused:

---

### Post by MattressVon on 2008-05-22
i fixed the beeping part.  

Re: System beeps on return from suspend
If suspend/resume is working but beeping at you, try System->Preferences->Power Management->General and uncheck, "Use sound to notify of an error".
__________________


Thanks VOR!

Now i just want it to not issue the error. I know I can just make it not show the message again, but i would really like to address the issue it self that is originating the error.

---

### Post by Gauvenator on 2008-05-22
hehe, I really freaked my dad out when I tried to sleep with the live cd...his laptop started wigging out and beeping really loud.

---

### Post by chronos00 on 2008-09-01
Thanks for posting back the solution MatressVon.

I would like to use that nice star under each post to thank you, but for a reason I dont understand, I cant find these stars in this thread. Any idea why?

Anyway, thanks!

---

### Post by cszikszoy on 2008-09-01
Best thing to do would be to respond to this Launchpad bug.

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250865](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250865)

One of the posts describes which files to include with the bug report.  This will help developers find and fix the problem.

---

