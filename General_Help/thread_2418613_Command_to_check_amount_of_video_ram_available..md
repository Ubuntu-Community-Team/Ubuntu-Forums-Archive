---
title: "Command to check amount of video ram available."
date: 2019-05-08
forum: General Help
---

### Post by zacmitche11 on 2019-05-08
I installed 4gb of ram, but Lubuntu only sees 2999mb while the bios sees all 4gb. It is a 64 bit version of Lubuntu btw. This Mobo I have isn't really supposed to support more then 2gb so it's not a huge surprise.  But I have seen others with the same have 4 showing and some not, while others suggest on board video is taking a chunk out.

Long story short, I want to see if onboard video is using it, or if it's lost in the Mobo void :)

---

### Post by TheFu on 2019-05-08
[https://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/](https://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/) has some answers. The method that works depends on the system.

---

### Post by zacmitche11 on 2019-05-09
Thanks, the ram is indeed lost to the void. Even though it's a 64 bit capable processor, physical address is only 32 bit.

---

### Post by TheFu on 2019-05-09
> **zacmitche11 said:**
> Thanks, the ram is indeed lost to the void. Even though it's a 64 bit capable processor, physical address is only 32 bit.

32-bits fully addresses 4GB of addresses.

---

### Post by zacmitche11 on 2019-05-10
I know, I can only see 3gb available though.

---

### Post by TheFu on 2019-05-12
> **zacmitche11 said:**
> I know, I can only see 3gb available though.

What does the BIOS show?  4GB or 3GB?  If the BIOS doesn't see it, then the OS won't.

Besides the already provided answer, I got nothing more.

---

