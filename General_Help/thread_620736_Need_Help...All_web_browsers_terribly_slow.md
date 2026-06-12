---
title: "Need Help...All web browsers terribly slow"
date: 2007-11-22
forum: General Help
---

### Post by justinclark on 2007-11-22
Ok I have a Dell Latitude D600 laptop, 20Gb hard drive, 512Mb ram, and 1600 Mghz Pentium M.  It ran XP just fine.  I recently switched to Ubuntu 7.10 and since have been experiencing the following issues.  I noticed when using firefox for a little while it would dramaticly slow down.  The scrolling would slow down terribly and it would load everything very slow.  Certain flash sites would just freeze it up.  Now just fyi my internet connection and speed are great(7-10Mbps) so I know that is not the issue.  I did some research and thought I would give swift weasel a try.  Same thing, it will work fine for a few minutes and then it will just slow down greatly.  Even tried Opera, same problem.  Other than that the OS seems to run fine the visual effects and all that jazz run well but Im on line often so this is becoming an issue.  ANY help would be much appreciated, thanks in advance.
-justin

---

### Post by justinclark on 2007-11-22
Also if its any help I have a cpu monitor running in my dock and just opening a browser sends it to 100%.

---

### Post by LaRoza on 2007-11-23
Are you using a router?

---

### Post by LaRoza on 2007-11-23
It sounds like an internet problem not a browser issue.

---

### Post by justinclark on 2007-11-23
No router, straight to my modem.  Im a cable tech for the company I get my internet service from and Im telling you its NOT an internet problem.  It works fine for a few minutes and then it just slows down.  When I was running Windows XP I had no issues so that leads me to believe that its probably not a hardware issue.  Keep in mind that I am very new to Linux so any help for me would be great.

---

### Post by LaRoza on 2007-11-23
Using a router might solve this, it is similar to other posts on this forum.

It isn't the service per se, but the issue of connecting a modem directly to a PC.

---

### Post by taurus on 2007-11-23
Post the output of this command from a terminal.

```
free
```
Also, you might want to run **top** at the terminal to see which program is eating up all the memory, causing the machine to slow down.

p.s.  What graphic card do you have on that laptop and have you installed any driver for it?

---

### Post by justinclark on 2007-11-23
> **taurus said:**
> Post the output of this command from a terminal.

```
free
```
Also, you might want to run **top** at the terminal to see which program is eating up all the memory, causing the machine to slow down.

p.s.  What graphic card do you have on that laptop and have you installed any driver for it?

justin@justin-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515572     500876      14696          0      15392     234928
-/+ buffers/cache:     250556     265016
Swap:       859436          0     859436
justin@justin-laptop:~$ 

Ok thats what I get with the free command.  I believe I have a ATI  Radeon graphics card and I think I have the drivers installed.  My buddy did the install for me so Im guessing at the moment but Im pretty sure he did.  Also could you explain how a router would help?  I cant quite make sense of that.  Thanks

---

### Post by LaRoza on 2007-11-23
> **justinclark said:**
> Also could you explain how a router would help?  I cant quite make sense of that.  Thanks


I am no expert, but I think the security of the router would prevent a DOS issue. The modem doesn't have a firewall, routers do.

---

### Post by justinclark on 2007-11-23
Hmmm.  Well can anyone make anything of that pasted terminal output?

---

### Post by justinclark on 2007-11-23
Ok well Im off to bed but if anyone can post some helpful tips please do so.  I will check back tomorrow.  Thanks.
-Justin

---

### Post by justinclark on 2007-11-23
bump...

---

### Post by t1n0m3n on 2007-12-01
515MB ram total, 500MB used, 15MB free
Not using swap

---

