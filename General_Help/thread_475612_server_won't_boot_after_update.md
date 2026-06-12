---
title: "server won't boot after update"
date: 2007-06-16
forum: General Help
---

### Post by kb7skb on 2007-06-16
Please help a newbie:

There were several updates available so I installed them. We had a power outage and the UPS I was using was about to shut down so I shutdown the server. When I rebooted, memtest starts and that's it.

I've rebooted several times, opened the grub menu and all that is listed is ubuntu, memtest186.

The server is an HP LP 1000 with two scsi 18 gb hdds. During boot up they seem to be detected ok by the bios. 

I dont't know much about grub. Can someone give me an idea of what to try?

I believe the server version is 6.06 lts??

Thanks for any thing you can do!

Jim

---

### Post by llamakc on 2007-06-16
So it is defaulting to memtest, right? When booting hit the escape key and get back into that GRUB menu. Use the arrow up|down keys to select Ubuntu, and possibly the 'safe-mode' version.

Have you removed anything manually from /boot lately?

---

### Post by kb7skb on 2007-06-16
That's correct. It defaults to memtest. 

When I hit the ESC key the menu only displays "ubuntu, memtest186" without any other options. 

I have not removed anything maunally. 

Jim

---

