---
title: "Shutdown Takes Several Minutes"
date: 2017-10-20
forum: General Help
---

### Post by sasafrass452 on 2017-10-20
For several months now, Ubuntu tends to take around 7-10 min to shut down, though it didn't happen every time. Since upgrading to 17.10 this morning, it has occured during all 3 attempts made thus far. Once during reboot right after the upgrade, & twice during a full shutdown. What's causing it to hang? Any help is appreciated!

---

### Post by kurt18947 on 2017-10-21
There is a bug in gnome (I think) that delays shutdown though 7-10 minutes seems like a lot. I've seen it occasionally but I don't think the delay has been over 2 minutes. I've not seen a work around for the bug.

---

### Post by sasafrass452 on 2017-10-26
I'm still having this issue. It has consistently occured every time I reboot or shut down. If anyone can help ID the culpret, please clue me in!

---

### Post by westie457 on 2017-10-26
I too have had this issue occasionally, a work around I use when this happens is press the 'Esc' key which brings up a text screen. The last line explains the problem. If it says a job is running press 'Ctrl' + C. Sometimes have to use X or Z.
If that does not work try holding down the 'Print Screen' key + 'Alt' and slowly type 'R-E-I-S-U-O' to shut down or use B at the end to reboot.

---

### Post by sasafrass452 on 2017-10-26
Thanx for the suggestion, it was very enlightening! After pressing Esc, I saw that THREE jobs were running which took the extra time to shut down:

WPA supplicant
Network manager
Raise network interfaces

What should I do? Can anyone help? Thanx!

---

### Post by sasafrass452 on 2017-10-26
Ok, after disabling my wifi connection(ie- "automatically connect"), my computer shuts down/reboots immediately! This is an obvious flaw that the devs need to investigate & fix, so until then, I won't mark this thread as "solved". Luckily, I can use my ethernet connection for the time being.... Fingers crossed!

---

### Post by sasafrass452 on 2017-11-03
I'm bumping this topic, in the hopes that this issue will be addressed. Until I turned off the wifi, the problem occured EVERY time I shut down or reboot. Although turning off the wifi helps, it's not the "solution" that I, or anyone else for that matter, would expect. What's the point of having wifi if I can't use it? And no, I'd rather not have to remember to turn it on & off every time I use my computer. Does anyone? To the developers, I hope you are reading this thread. It's clearly a long-standing issue that was only made worse upon upgrading to 17.10. Please fix it asap! Thanx.

---

### Post by oldos2er on 2017-11-03
Developers rarely if ever read the forums. If you haven't filed a bug on launchpad.net or searched for an existing bug report, please do so. 

See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by ian-weisser on 2017-11-03
> **sasafrass452 said:**
> To the developers, I hope you are reading this thread. It's clearly a long-standing issue that was only made worse upon upgrading to 17.10. Please fix it asap! Thanx.

When you actually report the bug to the developers, please include enough information for them to reproduce it.
The shutdown delay is _not_ affecting everyone. If it affected a developer's system, they would have already fixed it.

If you want it fixed, you must make it *easy* for the developers.

---

### Post by sasafrass452 on 2017-11-04
Well, I filed a bug report, though I don't expect anything to come of it. I'll see how it goes....

---

### Post by vasa1 on 2017-11-04
Is there a reason for not providing a link to the bug report :???:

---

### Post by jeremy31 on 2017-11-04
[https://bugs.launchpad.net/ubuntu/+bug/1730082](https://bugs.launchpad.net/ubuntu/+bug/1730082)
sasafrass452 you will likely be asked for more info

---

### Post by ian-weisser on 2017-11-04
Oh, dear.

You're right, nothing will come of that bug report...without much more information.
I cannot duplicate the problem on my test system, so I cannot triage the bug nor refer it to a developer.
How can I experience the problem?

---

### Post by sasafrass452 on 2017-11-05
Unfortunately, I don't think I can offer any more info. I have no clue about the specific files that are affected. What other info is needed? Perhaps I can try to obtain it with detailed instructions for doing so. I could try to record a video with my camera during a reboot, to show how I determined the wifi was causing the delay, but I doubt that would answer any questions since there really wasn't much info there. What I put in the bug report is all I know for now....

> **ian-weisser said:**
> Oh, dear.

You're right, nothing will come of that bug report...without much more information.
I cannot duplicate the problem on my test system, so I cannot triage the bug nor refer it to a developer.
How can I experience the problem?

---

### Post by oldos2er on 2017-11-05
Have you read the reply? There's a pointer there.

---

### Post by Ice-Tea on 2017-11-08
Don't know if anyone else has had this message but i've had this random shutdown hang on 3 different computers and a couple of times while hitting <esc> or <ctrl c> there has been a message about running a firmware update daemon?

Why would ubuntu be going anywhere near the firmware , is this something do with UEFI as 2 of the computers had old legacy Bios?

---

### Post by sasafrass452 on 2018-05-10
After upgrading to 18.04 last week, this issue appeared to be fixed. Now, 8 days later, it's happening again. After turning on "automatically connect" for wifi, my system takes several minutes to shut down. I sincerely hope the devs can resolve this once & for all! Altering a file on my own is NOT a solution, as it will only be replaced again by a faulty one via an update, as long as the devs don't recognize this issue..... What good is having wifi if I can't use it?

---

### Post by sasafrass452 on 2018-07-01
STILL having this issue. PLEASE fix it asap!!!

---

### Post by oldos2er on 2018-07-01
Please reread post #8. Coming here to demand bug fixes won't help, since devs rarely if ever read/post.

---

### Post by mc4man on 2018-07-01
Could be an issue with the kernel & your hardware. At the grub screen choose advanced, there may be some older kernels presented. If so try them & see how they work.
If not maybe try a newer kernel from the mainline kernel ppa (ask how) or try an older one (ask how)
Here on 18.04 I generally use the 4.4.x from mainline ppa as it's better suited to my 5 year old laptop (i.e the xenial 4.4.x

(- or install 16.04 and see how it works.

---

