---
title: "Ubuntu 18.04 Screen Acts Up after Suspend"
date: 2020-03-23
forum: General Help
---

### Post by antisthenes2 on 2020-03-23
I'm running Ubuntu 18.04.4 LTS with Linux Kernel 5.3. My video card is the Radeon HD 2600 PRO, no proprietary drivers are installed.  After resuming from suspend, my screen acts up: it becomes grainy and there is no colour. Sometimes, I'm able to see (and access) the GUI, while other times, I can see only the cursor. In both cases, the computer is, of course, nonfunctional, and I have to (force) shut it down and reboot.

---

### Post by u666sa on 2020-03-23
A. Configure to use only one monitor. Make sure that works reboot couple times.
B. There is a monitor.css or monitors.css somewhere inside some dir within your home folder. You gotta copy it to your root folder into some other location. That other location is your gdm call fig folder.

I’m speaking code because I’m in mobile phone, ni way for me to say exactly from where to where.

Use locate monitor.css or locate monitors.css

And you will see from where to where.

After that reboot and check.

---

### Post by antisthenes2 on 2020-03-23
Thanks for your response.  I'm new to GNU/Linux, so I understood nothing from your instructions. Could you please explain them to me in simpler terms?

---

### Post by deadflowr on 2020-03-23
Seems like that graphics card is generally problematic when coming back from suspend,
see
[https://www.reddit.com/r/Kubuntu/comments/90lo71/screen_corruption_after_wake_from_suspend_ati/]("https://www.reddit.com/r/Kubuntu/comments/90lo71/screen_corruption_after_wake_from_suspend_ati/")
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1267150]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1267150")

I do not seen a clear method of resolution.
You might benefit by posting a bug report for it
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by antisthenes2 on 2020-03-23
> **deadflowr said:**
>  Seems like that graphics card is generally problematic when coming back from suspend  Yes, this is the issue! :)  > **deadflowr said:**
>  I do not seen a clear method of resolution.  Is there really nothing I could try? Thanks!

---

### Post by antisthenes2 on 2020-03-23
It seems that one possible solution, which emerges from the bug report you refer me to, is to "first set a GPT partition table on the hard disk before installing Ubuntu Gnome". What do you think of this?

---

### Post by antisthenes2 on 2020-03-25
Any ideas? Also, is there an analogous feature to Suspend that I may try instead?

---

### Post by him610 on 2020-03-25
> Is there really nothing I could try? 
Instead of letting it suspend, just turn it off.

---

