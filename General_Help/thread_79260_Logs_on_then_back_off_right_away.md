---
title: "Logs on then back off right away"
date: 2005-10-19
forum: General Help
---

### Post by generallee5686 on 2005-10-19
I just recently did a kernel update to the most recent one that is on the autoupdater deal.  I had some problems downloading stuff in firefox so i decided to log off then back on, but when i went to log back on, it would act like its logging on and sit there for about 10 seconds, then the screen would go blank for another few seconds then it would go right back to the login screen.

Are there any logs that i should check out?
Any other suggestions?

I am on a laptop with a Athlon 64 3400+
ATI Mobility Radeon 9700
1GB of pc3200 ddr

---

### Post by reidi on 2005-10-20
Check to see if your login partition (/home/[your.login]) is full.  You may be able to log in as  root and make some space on /home if it is at 100%.
IR

---

### Post by paul2005 on 2005-10-20
[QUOTE=generallee5686]...when i went to log back on, it would act like its logging on and sit there for about 10 seconds, then the screen would go blank for another few seconds then it would go right back to the login screen.[/QUOTE]

I have exactly the same problem (see [http://ubuntuforums.org/showthread.php?t=77947)](http://ubuntuforums.org/showthread.php?t=77947)). How do i check the size of my login partition? I installed everything onto one 6Gb partition on my second hard drive, and if I do a 'df' it says there's still 3Gb free.

---

