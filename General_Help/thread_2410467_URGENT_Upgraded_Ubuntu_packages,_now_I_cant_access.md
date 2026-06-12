---
title: "URGENT: Upgraded Ubuntu packages, now I cant access other partitioned Ubuntu OS"
date: 2019-01-16
forum: General Help
---

### Post by daniel-pierce-iv on 2019-01-16
I have three OSes installed to 2 drives;

Drive A
- Windows 10
- Ubuntu 18.04

Drive B
- Ubuntu 18.04 (encrypted)

I need Drive B Ubuntu for work, hence the urgency.

I upgraded Drive A Ubuntu, and now I can no longer access Drive B Ubuntu. Before the upgrade, all OSes were available in the Grub menu. Now, only the Drive A OSes are shown.

The following command didn't fix the issue;
[COLOR=#FF006D][FONT=Noto Mono]sudo update-grub[/FONT][/COLOR]

I tried installing boot-repair. After running it, I no longer have access to the boot menu at all. It boots directly into Drive A Ubuntu, with no options presented.
It spit out a file that may be helpful for troubleshooting: [http://paste.ubuntu.com/p/px5YwJjbHV/](http://paste.ubuntu.com/p/px5YwJjbHV/)

Notice line 31. Thats the encrypted Drive B Ubuntu.

---

