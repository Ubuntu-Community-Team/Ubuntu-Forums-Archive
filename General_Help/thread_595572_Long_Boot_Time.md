---
title: "Long Boot Time"
date: 2007-10-28
forum: General Help
---

### Post by johanbach on 2007-10-28
I finally got Grub to work (I had to do it manually) and now I have an extremely long boot time.  I saw other posts with people having four to six minute boot times, but I let mine go for forty-five minutes before I gave up.  As it is trying to detect hardware and load various drivers, the majority of this output says:

[xxxx.xxxxxx] ata3: soft resetting port
[xxxx.xxxxxx] ata3. 00: configured for udma/33
[xxxx.xxxxxx] ata3: EH Complete

where x=some number.  When I stopped the machine, I was up to 2872.709246.  I haven't found any other posts on an this, so I thought I would give it a try.  Any suggestions would be helpful.

This is a triple boot machine with Fedora and Windows XP.  Both of the other OS boot with no problem.

Thanks

---

### Post by johanbach on 2007-11-01
Is there a way for me to capture the output of dmesg from Fedora even though Ubuntu fails to boot?  If so, I will gladly post the whole thing here if someone could help out!

---

