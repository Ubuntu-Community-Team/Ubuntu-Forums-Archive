---
title: "[SOLVED] Wubi - Startup keyboard dead + General Q"
date: 2008-04-13
forum: General Help
---

### Post by jhender on 2008-04-13
Hey Everyone,
I'm getting a ThinkPad r61 in the mail in a couple of weeks (yay!) and I wanted to use it as a way to get to know Linux. I found Wubi and thought I'd get a little familiar with Ubuntu first before I dedicated a partition to it.

Thus, I installed it (8.04 beta) on my desktop (Win XP, AMD Athlon 64 x2 dual core 5000+. 2 gigs ram, GeForece 7900 GS). It installed fine, first started up fine (could choose Ubuntu with my keyboard), and everything worked on the desktop but the network connection (Belkin Wireless card maybe a prob? plus i have a kind of gatekeeper program i have to install to login to my university wireless).

[B]Anyways, problem:
* After restarting back to XP to check my email, rebooting and trying to get back into Ubuntu - it did not work! My Keyboard does not function at the countdown screen, no the arrows, enter key or F8. I can get into my BIOS beforehand fine and when it counts me down into XP it works fine after that. Arg![/B]


My general adjunct question is why would anyone want to have a dedicated partition/dual boot etc when Wubi seems safer and less complicated? Whats the advantage?



Thanks for reading through this. I look forward to getting my hands into a Linux distro finally after about 5 years of daring myself to do it.

--Justin

---

### Post by ago on 2008-04-13
Keyboard: That might be some bios/ntldr issue I'd assume, can you select Items within ntldr (i.e. move between Windows and Ubuntu)?

Main advantages of an installation to dedicated partition:

1) You can hibernate
2) Slightly better hard disk I/O performance
3) More robust filesystem (wubi is more vulnerable to power failures / hard reboots)

---

### Post by jhender on 2008-04-13
Alright, good on the advantages, thanks.

The keyboard: I cannot select items within 'ntldr' (i cannot move between Windows and Ubuntu). I could the very first time I installed Wubi and restarted into Ubuntu, but no time afterwards. I've since tried uninstall/reinstalling Wubi to no avail.

---

### Post by ago on 2008-04-13
> **jhender said:**
> 
The keyboard: I cannot select items within 'ntldr' (i cannot move between Windows and Ubuntu). 

That is not a wubi issue then, it is ntldr (windows) that cannot use your keyboard... You would have the same issue if you had to select items in a windows-only multiboot menu (say with xp and win98 )...

Not much I can do (you'll have to use a new keyboard).

---

### Post by jhender on 2008-04-13
> **ago said:**
> That is not a wubi issue then, it is ntldr (windows) that cannot use your keyboard... You would have the same issue if you had to select items in a windows-only multiboot menu (say with xp and win98 )...

Not much I can do (you'll have to use a new keyboard).

The thing is it worked once before perfectly (could move via keyboard), and then suddenly it didn't the next time. The only change was the first time Ubuntu started it did it's whole first time ever starting up through Wubi thing....

---

### Post by jhender on 2008-04-15
still no ideas? im getting my new computer in less than a week, and right now i can't even get ubuntu to INSTALL with wubi let alone figure out how to dual boot...

---

### Post by ago on 2008-04-16
jhender when you are at the screen where you have to select between Windows and Ubuntu, that is ntldr, and it is writtien by MS, none of my code (or grub4dos devs' code) has been executed at the point. If the keyboard does not work in ntldr it is a MS issue, not much I can do I am afraid. Did you try with a different keyboard by any chance?

---

### Post by jhender on 2008-04-16
fixed! with a thorough googling, i found this link:

[http://aumha.net/viewtopic.php?f=62&t=26754](http://aumha.net/viewtopic.php?f=62&t=26754)

...which pretty much said 'check the BIOS stupid'. somehow the peripheral option for USB Keyboard was switched to disabled. don't know why it worked the first time around before, but switching this to enabled fixed my problem.

off to dabble in ubuntu! thanks for your help! :)

---

### Post by siyudz@yahoo.com on 2010-05-14
> **jhender said:**
> fixed! with a thorough googling, i found this link:

[http://aumha.net/viewtopic.php?f=62&t=26754](http://aumha.net/viewtopic.php?f=62&t=26754)

...which pretty much said 'check the BIOS stupid'. somehow the peripheral option for USB Keyboard was switched to disabled. don't know why it worked the first time around before, but switching this to enabled fixed my problem.

off to dabble in ubuntu! thanks for your help! :)

[http://aumha.net/viewtopic.php?f=62&t=26754](http://aumha.net/viewtopic.php?f=62&t=26754) "The requested topic does not exist" I have same problem with you, My Keyboard does not function at the countdown screen, no the arrows, enter key or F8. I installed ubuntu inside windows on my macbook, can you help me???

---

