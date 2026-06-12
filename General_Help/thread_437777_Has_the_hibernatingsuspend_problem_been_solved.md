---
title: "Has the hibernating/suspend problem been solved?"
date: 2007-05-09
forum: General Help
---

### Post by joy83 on 2007-05-09
I think lots of people are having the same problem as mine. When I suspend or hibernate feisty for a certain time and then when I return back the computer hangs and nothing happens, I have to reboot it again. I have seen lots of topics on this problem, but has this problem been solved yet?

---

### Post by aysiu on 2007-05-09
It depends on the computer.

It's been solved on my laptop... was solved even before Feisty was in beta.

But a lot of other people (depending on what model laptop... or desktop they have) will continue to have problems.

---

### Post by joy83 on 2007-05-09
I am using a dell dimension E521, I dont know what I have to do to get rid of the problem.

---

### Post by ronb on 2007-05-09
I don't know if this is the same issue, but here's what happens to my machine: First, my screensaver starts when it's supposed to. Then, when it's time for the monitor and computer to go to sleep, it goes back to the desktop instead.

Once I got a pop-up error message saying that I had a Suspend Failure. I looked it up in the Power Management help system and found this explanation: [INDENT]**When a suspend failure occurs you may get this following warning. **[B]The most common reason for this notification is that the current user does not have permission to suspend or hibernate the computer.
[/B][/INDENT]I'm the only user on this machine. It's my machine. It has an ASUS motherboard and an AMD Athlon XP chip.

I'm having other permissions problems, but they are probably more appropriate for another thread.

---

### Post by whayong on 2007-05-09
Yes, this was solved for my laptop as well, PCG-SRX77.  It wasn't working on Edgy but it works now in Feisty.  I too believe it is laptop dependent.

---

### Post by strabes on 2007-05-09
If you have an ATI card, edit /etc/default/acpi-support and change "POST_VIDEO=true" to "POST_VIDEO="

---

### Post by paincorp on 2007-06-07
i tried editing that file and the monitor still turns off

any other ideas?

---

