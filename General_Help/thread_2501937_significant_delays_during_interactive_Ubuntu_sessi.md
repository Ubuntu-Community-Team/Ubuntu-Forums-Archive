---
title: "significant delays during interactive Ubuntu sessions"
date: 2024-10-26
forum: General Help
---

### Post by skypuppy2 on 2024-10-26
First, allow me to establish some bona fides: Been a Linux user since the mid 80's, and QNX user/developer since 1980.  If you don't believe that (because you think Linux/Ubuntu didn't start that early, consider that I was building and selling multi-user, networked PC's since 1981, esp with Zanthe Zim, at a nuclear power plant just outside of Phoenix, AZ.  If you don't believe THAT, you're welcome to hang up now and thank you for playing  Reseller (at cost) of Slackware (true) Linux since 1991 to the Huntsville (Alabama) computer club. HPCUG.  We all learned a great deal and had fun at meetings and dinners...

My current problem is driving me up that wall and is so frustrating that I'm about ready to throw my hardware into the river and retreat to the WORST operating system ever developed and sold.  

FOUR of my currently active home computers (I'm retired now) ALL have the same problem  It first showed itself in a cute but powerful mini-PC, an ARM-based unit from Khadas something-IV (it's mouse is down or I could get you the exact name.  Sorry.)  The other 3 are actual desktops, 1 is running Ubuntu 23 and is about 5 years old.  One is on Ubuntu 24.04 and about 3 years old.  The third unit is about a year old, booting from nvme drive, on 24.04.1.
They did not all start this stuttering at the same time.  The SBC started it upon first boot, within two operating days.  Next to fall was the dual-boot (horrible OS did not diaplay the problem, only when running Ubuntu), and the third desktop, the most modern that runs only Ubuntu.

All give an error, something like 'pause,', "wait for the system to come back" and if it does come back, it is a different amount of time for each.  Oddly, programs that are not running in the foreground are not affected!  Only the foreground interactive operations.  This is VERY frustrating and is very strange, only started with 24.0x versions.  I

I tried many types of diagnostics and just cannot figure out why these various systems (all on the home subnet, of course) are doing this.  Clam gives no virus indications.  Nothing is obvious from cockpit or from watching system monitors.  <heavy sigh>.  

I am totally at a loss here and seeking help.  (I'm usually the one providing help to others but I am stumped.)

Help, please.
David

---

### Post by TheFu on 2024-10-26
> **skypuppy2 said:**
> First, allow me to establish some bona fides: Been a Linux user since the mid 80's, and QNX user/developer since 1980. 

I stopped reading right there.  Linux didn't exist until 1991.  

When providing "facts", it is important they are actually true.
[https://en.wikipedia.org/wiki/History_of_Linux](https://en.wikipedia.org/wiki/History_of_Linux)
Linux started in April 1991 and was released in Sept 1991. The first upload of the code was actually called "Freax".

When you looked at the system logs, they told you what? 
Do you have any performance monitoring running? What does that say?

---

### Post by grahammechanical on 2024-10-27
What application are you using? I was not aware that Ubuntu had any interactive display sessions. Do you mean the desktop and the movement of application windows around the desktop?  Or video conferencing? 

Regards

---

### Post by skypuppy2 on 2024-10-28
Solitaire is a perfect example.

---

### Post by skypuppy2 on 2024-10-28
But QNX was out in the 80's and I did mention it.  In case you didnt know, QNX is a UNIX clone with much better real-time response and it had superb networking stacks even back then.  REREAD the post.  Slackware WAS a Linux distribution and as I said, mid-80's I was reselling the CD's (at cost) to our use group.  Your source is incorrect, I actually DID IT.

---

### Post by Norm24 on 2024-10-28
> **skypuppy2 said:**
> But QNX was out in the 80's and I did mention it.  In case you didnt know, QNX is a UNIX clone with much better real-time response and it had superb networking stacks even back then.  REREAD the post.  Slackware WAS a Linux distribution and as I said, mid-80's I was reselling the CD's (at cost) to our use group.  Your source is incorrect, I actually DID IT.

And you sir would be correct!

Basic internet search shows QNX being developed in the early 80s by then Canadian company Quantum Software Systems.

---

### Post by skypuppy2 on 2024-10-29
Thanks.

However, that does not help answer my original problem.  <sigh>

---

