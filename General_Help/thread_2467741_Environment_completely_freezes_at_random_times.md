---
title: "Environment completely freezes at random times"
date: 2021-10-06
forum: General Help
---

### Post by trent65 on 2021-10-06
Hello all!

I'm hoping some of you will have some ideas for debugging. For as long as I have used ubuntu, it has frozen at random times. There is no rhyme or reason from my perspective as to what causes it. I can play a game that eats up practically all my RAM and its fine, but if I browse the internet, it freezes. I can go months and months without this happening but eventually it will always happen. I'm on my third LTS version and still it persists.

And when I say frozen, I mean completely. I can't even get to the tty view. I have no option but to just power off manually, which hurts my soul every time.

It just happened five minutes ago and my computer is currently off. What would you do the next time you booted up to get more information on this problem?

Thank you!

---

### Post by TheFu on 2021-10-06
I would look at the system logs using **journalctl -b -1** to see what was happening just before the lock up.  Hardware issues are almost always the problem.  Check temperatures throughout the system. Look for loose cables, cables that need to be replaced, a failing GPU, PSU, and dust.

Does it only die under load or have you returned after 4 hrs away from the system left running and found it locked up?

Frozen can mean many things.
The GUI can be frozen, but changing to a different TTY (cntl-alt-F1, F2, F3, F4 ... ) will switch and then you can login to a text-only session and look around.
The TTY and GUI can be frozen, but you can ssh into the system from another computer and look around.

Each of these tells us different things.  It could be a GPU-only issue or a GPU driver issue.  It could be only the network stack or everything except the network stack.  It could be a loose data or power cable.

The one that gets lots of people, especially if they have pets, is lots of dust inside the case causing shorts on the motherboard.

And one other thing ... try figuring out a repeatable cause for the issue.  Once you have that, boot from a Try Ubuntu flash drive and try to cause the issue.  If you cannot, it could be your settings, not the hardware at all.

About 15 yrs ago, I had a system that would crash with a kernel panic from time to time.  I did all these things, but got a hint that the GPU was starting to fail - during reboot, the screen would throw up garbage for a second between the motherboard BIOS and the GPU BIOS screens.  $40 replacement GPU installed and it was fixed.  Never had the issue again for the next 8 yrs that system worked here.  Just need to pay attention to little details, take notes, and definitely track the exact time when the lockup happens so you can use journalctl to only look at logs within 1-2 minutes before that time.  You'll want to look up all the options that journalctl provides - it really is an amazing tool for looking at the most important stuff.

It wouldn't hurt to leave the system on running a memcheck from the boot disk for 24+ hrs.  If that doesn't find anything, you can put a load on the system by having it calculate pi to 1+ million places for another 24+ hours. Run these things from Try-Ubuntu environments - want to avoid using the disk system inside the computer and really want to use the minimal GPU drivers, nothing added on or proprietary.

Debugging comes down to simplify and test, repeat.  Over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over until you've narrowed down the cause.

---

### Post by trent65 on 2021-10-07
@thefu Really appreciate your reply! As I mentioned. Keyboard functionality is locked so I can't get into TTY, but I like the idea of SSLing into it. At least then I can try to poweroff from the command line. It's something I'll need to learn how to do but hopefully it won't be too bad.

And your comment about pet hair is important. I'm overdue for a good cleaning. I try to do it once a year at around this time.

When I looked at journalctl I didn't see anything out of the ordinary. I'm not really sure what I was looking for but didn't see any kind of fatal error or hardware failure.

---

### Post by tea for one on 2021-10-07
> **trent65 said:**
> And when I say frozen, I mean completely. I can't even get to the tty view. I have no option but to just power off manually, which hurts my soul every time.

It's not really a good idea to power off when everything is frozen because you can potentially damage the file system.
You could enable the REISUB function by editing a system configuration file:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244
I found the details at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) section 3
By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by trent65 on 2021-10-08
> **tea for one said:**
> It's not really a good idea to power off when everything is frozen because you can potentially damage the file system.

Yeah. I know it's a bad idea but not really sure what else to do. As far as I can tell simply won't accept keystrokes at all. So I can't get to tty, I can't open a terminal, I can't do anything. 

Thank you for the link though, I'll make sure to give it a try next time this happens.

---

### Post by aug7744 on 2021-10-08
What is youur GPU and browser ?
Try disable in browser "use hardware acceleration".

---

