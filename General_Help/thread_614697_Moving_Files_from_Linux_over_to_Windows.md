---
title: "Moving Files from Linux over to Windows"
date: 2007-11-16
forum: General Help
---

### Post by twistedbydesign on 2007-11-16
OK....My Ubuntu won't boot because of something I did last night 
I posted a thread about it [[COLOR="Red"][COLOR="Red"][COLOR="SandyBrown"][COLOR="DarkOrange"]Here[/COLOR][/COLOR][/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=614473")
Any way...I think i'm just going to do a fresh install...But i have a lot of stuff on my linux partition i'd rather not use. I Dual boot with XP (which is what i'm using right now)
I know you can get easily get files from the windows partition while using Ubuntu, But i was wondering if there was any way to get to my Linux Files while i'm on windows. So far I haven't been able to.
I searched around a bit for other threads on this but they all seemed to be about Moving files around WHILE using linux. I was just wondering if anyone knew of a way to do the same while on windows.
Thanks!

---

### Post by PentaxFollower on 2007-11-16
For ext2/ext3 partitions you could use explore2fs ([link]("http://www.chrysocome.net/explore2fs")). It worked great for me (a little slow though).
I've found also [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by Martje_001 on 2007-11-16
This works excellent:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Also works for ext3.

---

### Post by twistedbydesign on 2007-11-16
I will give them a shot.
Thank you very much!

---

### Post by geirha on 2007-11-16
Alternatively, boot the liveCD and do it from there.

---

### Post by twistedbydesign on 2007-11-18
Downloaded program from above link. It mounted the linux partition but wouldnt let me simply Copy/paste everything. So i used Windows nifty backup tool and just backed up everything into one of those crazy Backup files, then unpacked it into my windows Drive. So it was a long process but i got what i needed. Thanks a million!

---

