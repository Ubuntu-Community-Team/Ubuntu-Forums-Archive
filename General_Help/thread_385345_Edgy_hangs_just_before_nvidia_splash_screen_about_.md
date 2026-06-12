---
title: "Edgy hangs just before nvidia splash screen about 50% of the time"
date: 2007-03-15
forum: General Help
---

### Post by liegerm on 2007-03-15
Hi guys,

I have had a problem with Edgy since it was installed. I have nvidia drivers installed (non-free, beta) but I'm 99.9% positive that this problem existed prior to installing these drivers. I have Suse 10 installed as well as Windows 2k and never get this problem with either of those. 

The symptoms are as follows: the machine boots fine and the screen goes blank as it does just before displaying the nvidia splash screen. Some of the time it will then continues as normal and displays the login manager (kde) but about 50% of the time the screen stays blank apart from an unblinking cursor in the top-left of the screen. When this happens, the machine is frozen and will not respond to any key presses. I have left it like this a few times to see if it will continue, but it doesn't. My only alternative is to reset or turn off. The machine will always boot properly the next time.

My first thought is that X is to blame but cannot see anything obvious (to me) in the logs.

Does anyone have any ideas of what could be causing this or where I can look for errors?

Thanks in advance.

---

### Post by liegerm on 2007-03-23
Sorry I've been away so long. I've had ISP problems.

It does seem to be the video driver: when I change the driver in xorg.conf from 'nvidia' to 'nv', it's fine; when I change it back to 'nvidia', it give me problems again. I think I'll post a query/bug report with nvidia if I can.

Thanks for all your help.

---

### Post by liegerm on 2007-03-30
No joy on the nvidia forum yet. Has anyone else seen this behaviour?

---

