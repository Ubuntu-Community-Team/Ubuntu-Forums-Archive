---
title: "Problem with partition"
date: 2015-11-17
forum: General Help
---

### Post by Tobiahao on 2015-11-17
Hi guys! I have Ubuntu for one week, so i'm new in it. Yesterday one notification have shown, that system have too little disc space. I tried to increase it in GParted, but it shows, that it's maximum for this partition. Bellow I'm posting screens from GParted:

[IMG]http://s8.postimg.org/v7fwgfig5/image.png[/IMG]
[IMG]http://s8.postimg.org/7hqgrqk2t/image.png[/IMG]


Anybody will help me? Thank you in advice ;)

---

### Post by flemur13013 on 2015-11-17
Two issues:
1 - sda6 contains your Ubuntu system, and it is mounted at "/" 
To resize it, it need to be unmounted, which you can't do while the system is booted.  
You can do that from the LiveDVD.

2 - You'll need to shrink sda5 by the amount you want to add to sda5.
It's not mounted in your picture, so you should be able to do that before using the LiveDVD, above.
Shrink it from the right side...so that sda6 can be moved into that free space.
Edit: It'd probably be best to shrink this NTFS partition using windows software; IOW, boot windows to shrink it, then boot the LiveDVD to make sda6 bigger.

---

### Post by buzzingrobot on 2015-11-17
Since you have 387.17 gigs of data on /dev/sda5, you ought to back that data up elsewhere before you resize.

---

### Post by grahammechanical on 2015-11-17
A temporary solution would be to delete stuff from Ubuntu. In one week you have installed a lot of stuff. Or is it large data files that you collect? If so, move them into sda5, the ntfs data partition. Which may need a clear out. Use Windows utilities to defrag the Windows partitions before resizing them. How much free space is there in sda3? Is it where Windows resides?

You have a hard disk that is a little under 700 GB in size with not much more than 82 GB unused. We do not know how much free space is in sda3. Ubuntu (system + swap) is using just under 20 GB. Perhaps a house-keeping rethink is needed?

You might also want to think about archiving (compressing) large data files to create space.

Regards

---

### Post by Tobiahao on 2015-11-17
It's worked, i fixed this. I have to clean up this mess with my disc, but i dont have time right now. By the way i have one more little problem, from a few days my ubuntu is turning on in 4-5 minutes (it's stuck on loading screen for few minutes), i think it's a little bit too long, any solution of this?

---

### Post by ajgreeny on 2015-11-17
> **Tobiahao said:**
> It's worked, i fixed this. I have to clean up this mess with my disc, but i dont have time right now. By the way i have one more little problem, from a few days my ubuntu is turning on in 4-5 minutes (it's stuck on loading screen for few minutes), i think it's a little bit too long, any solution of this?
Impossible to say what is causing the delay without more information.

If you hit Esc when the boot is halted you may get to a text boot screen and that may show what is causing the problem; sometimes a bad network configuration will cause this sort of thing, but let's see what is what before trying to solve it for you.

---

### Post by Tobiahao on 2015-11-18
When i'm clicking Esc black screen appears and nothing more. There is no text.

---

### Post by ajgreeny on 2015-11-18
OK, instead of **Esc** try **Ctrl+Alt+F1**; that may show you the text boot.
Alternatlvely, just hit "E" at the grub menu, if you see it, navigate to to the words "quiet splash" in the kernel line and delete them, then hit Ctrl+X to boot; that will certainly show you a text boot for this one time only.

---

### Post by Tobiahao on 2015-11-18
I don't have idea why, but problem disappear today. Anyway, thank you all for help, By the way I'm new in Ubuntu's community and i'm very amazed how fast people try to help you. Thanks again. :)

---

### Post by ajgreeny on 2015-11-18
Great!

Please mark as SOLVED  from the Thread Tools menu at the top.

Marked SOLVED on your behalf.

---

