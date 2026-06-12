---
title: "Problem with Sylpheed 3.5.0 RC2"
date: 2021-08-01
forum: General Help
---

### Post by yellowhousejake on 2021-08-01
Good day,

A quick background story. I have been running Lubuntu on my laptop since 14 LTS, upgraded through 16 LTS and then 18 LTS. With an update last week my laptop began freezing up after just a few minutes of use, generally. Sometimes it would freeze up immediately after reboot.

I simply did not have time to monkey with it or troubleshoot the issue. So, I pulled out a Lubuntu 16.04 disk I had and overwrote my hard drive re-installing Lubuntu 16. Once complete, I installed my packages from Synaptic, which was not much I pretty much use the internet for nothing but email a a few forums these days. Once the packages were installed I recovered my home folder Using "Back in Time". All seemed well, Libreoffice is up, my bookmarks and settings for Brave browser are there as well. I started Sylpheed and it sees my mail folders. Checking my email I see Sylpheed connects, pulls down the mail, and lets me select and read a message.

The problem, I cannot delete or move a message in Sylpheed. I get the error "Error occurred while processing messages." I have checked the permissions on the mail folders and it seems correct to me. Only relevant folders displayed.

dave@dave-HP-ProBook-650-G1:~$ ls -la
total 2480
drwxr-xr-x 35 dave dave    4096 Jul 30 16:39 .
drwxr-xr-x  3 root root    4096 Jul 29 19:22 ..
drwx------  4 dave dave    4096 Jul 29 22:28 Mail
drwx------  9 dave dave   12288 Aug  1 11:18 .sylpheed-2.0



dave@dave-HP-ProBook-650-G1:~/Mail$ ls -la
total 16
drwx------  4 dave dave 4096 Jul 29 22:28 .
drwxr-xr-x 35 dave dave 4096 Jul 30 16:39 ..
drwx------ 19 dave dave 4096 Jul 29 22:32 yellowhousejake


dave@dave-HP-ProBook-650-G1:~/Mail/yellowhousejake$ ls -la
total 208
drwx------ 19 dave dave  4096 Jul 29 22:32 .
drwx------  4 dave dave  4096 Jul 29 22:28 ..
drwx------  2 dave dave  4096 Jul 29 22:32 draft
drwx------  2 dave dave  4096 Aug  1 11:10 inbox
drwx------  2 dave dave  4096 Jul 29 22:32 junk
drwx------  2 dave dave  4096 Jul 29 22:32 queue
drwx------  2 dave dave 36864 Jul 29 22:33 sent

Seems like a perms issue to me, but I can find no log to investigate and no setting to flip for debugging. I have used Back in Time before and it has always restored my files and folders properly with correct ownership and permissions. Anyone have a clue what this issue could be?

Thank you,

DAve

---

### Post by yellowhousejake on 2021-08-01
Oddly, I simply rebuilt the folder tree and everything returned to normal.

Hopefully, if someone else has this problem they will find this solution works for them.

DAve

---

