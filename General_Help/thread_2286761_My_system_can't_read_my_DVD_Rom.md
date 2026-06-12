---
title: "My system can't read my DVD Rom?"
date: 2015-07-14
forum: General Help
---

### Post by Adrian_Oneasca on 2015-07-14
Hello everyone, seems like this is my first post on ubuntuforums.org, been using Ubuntu and linux in general for over 5 years now, and this is the first time Google and my common knowledge couldn't help me.
So I'm running Ubuntu 15.04, and I have a CD/DVD-Rom that I haven't been using for about 2 years (I preffer using USB storage systems rather than DVD/CDs) and I noticied my system doesn't read my drive (or atleast this is what I think it happens).
As seen here, [url=http://i.imgur.com/dLgswgR.png]
  [img]http://imgur.com/dLgswgRl.png[/img]
[/url] ubuntu sees the dvdroam, the only problem is that once I insert my disk into it, it will spin for 2 seconds (makeing the classic noise) and then stop.
I am not sure if the problem comes from my device or from the system.
Some notable facts are that this happens for any CD/DVDs, and that if I try to put a bootable disk (such as a ubuntu installation) and try to boot it at PC start it will read it and open the installation setup.

---

### Post by Vladlenin5000 on 2015-07-14
Hi and welcome.

I would say it's software (OS or "something else") in this case, considering it works booting a bootable disk.
Here's an interesting test you could do:

- Boot a live session from USB and then try with the same CDs/DVDs you tried in your installed system.


[EDIT]
OTOH, your drive is very old. I wouldn't expect to work acceptably.

---

### Post by spbach1234 on 2015-07-15
Have you tried to mount it manually by finding its /dev file? Mount it:
```
mount /dev/cdrom0 /mnt
```
Let me know if this helped.
-spbach1234

---

