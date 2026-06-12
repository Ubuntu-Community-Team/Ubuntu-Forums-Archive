---
title: "Best way to run LT Spice?"
date: 2016-01-21
forum: General Help
---

### Post by ilRagazzo on 2016-01-21
My professor wants us to work in LT Spice, which is only available in Windows and Mac flavors. 
I googled it, then read this: [http://ubuntuforums.org/showthread.php?t=1824277](http://ubuntuforums.org/showthread.php?t=1824277)

Is this still the best way of running LT spice? My professor has said that the course will utilize LT spice to evaluate Very Large circuits and may bog down a computer that is running it via an emulator. 

Now I've been using Ubuntu for 2.5 years now. A year of dual booting, then switched over completely. So I have a basic idea of what I'm doing but I've never understood things like WINE or Virtual box . So I was hesitant in it's use, but it is time to learn I guess.

running Ubuntu 15.10 with I7 3632qm 2.2ghz*8
AMD radeon HD 7700
and 7.7 Gigs of memory 

Thank you. 

P.S. I'm highly impressed with the response time of the admin, thank you.

---

### Post by Vladlenin5000 on 2016-01-21
Hi and welcome.

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=2000](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2000) suggests LTSpice is well supported under Wine so yes, the simple method outlined in your link should be valid. I suggest you try it, you have nothing to loose. 

I also suggest you to learn about WINE, which is a compatibility layer (for the sake of simplicity let's call it an emulator) that allows some Windows software to run in Linux. It isn't and has nothing to do with virtual machines - an entire OS (guest) running virtually inside the host OS - for which Virtualbox is used, among dozens of others.

---

### Post by ilRagazzo on 2016-01-25
Thank you, I did try it, and it seems to run really well on my machine. 
Solving thread now, thanks again.

---

### Post by Vladlenin5000 on 2016-01-25
You're welcome :-)
Please use the thread tools to mark it as solved if you don't need further help with this issue.

---

