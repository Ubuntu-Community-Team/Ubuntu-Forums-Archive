---
title: "BUG: Unable to kernel paging request at ffffffffb02a50d8"
date: 2019-09-02
forum: General Help
---

### Post by sms3h2 on 2019-09-02
I'm trying to bring back my old desktop and turn it into a server. Its running a x99 chipset with 32 gigs of ram and has a Nvidia GTX 960. I pulled the power to the GTX 960 and got the same error log. Sorry I couldn't upload the file. Ubuntu said they weren't valid...

EDIT:
I've run memory test for 2 days with 0 errors on all 32 Gigs of ram.
I'm also running with acpi=off in the boot args otherwise the system won't boot at all. 

uname-a
Linux aang 4.15.0-58-generic #64~16.04.1-Ubuntu SMP Wed Aug 7 14:10:35 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

version.log
Ubuntu 4.15.0-58.64~16.04.1-generic 4.15.18




Here are the long logs
[https://paste.ubuntu.com/p/Zm8wS4pfD2/](https://paste.ubuntu.com/p/Zm8wS4pfD2/)

---

### Post by sms3h2 on 2019-09-08
I simplified down the system considerable and it was still happening, removed graphics card, raid, all the memory and tested each section. The problem still continued. The one thing I noticed was that it always happened on CPU 5, I have a 6 core i7. I disabled core 5 and its been stable ever since. I'm really surprised by this, but now that I've disabled it in the bios everything seems pretty happy.

---

