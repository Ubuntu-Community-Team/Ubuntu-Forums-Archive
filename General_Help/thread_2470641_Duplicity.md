---
title: "Duplicity"
date: 2022-01-06
forum: General Help
---

### Post by yegnal on 2022-01-06
Greetings;

I have a dual boot Windows / Ubuntu Linux machine with:
One SSD for WindowsOS / One SSD for UbuntuOS

Drive 1. One GPT 4TB NTFS drive for all Windows files
Drive 2. One 500GB ext4 drive for Linux Home

Drive 3. One GPT 4TB NTFS drive for BACKUP

My version of fault tolerance right now is to run duplicity to create backups of Drive 1 and Drive 2 which I put on Drive 3.  Then yearly I image Drive 3 and move it offsite.
I realize this is not optimal, but what I really am curious about is:

Does the file system of BACKUP drive 3: matter ?   I know NTFS has it's issues, would I be better off running those duplicity backups to Drive C if it was formatted ext4 ?, exFat ? or does it simply not make any difference ?

---

### Post by HermanAB on 2022-01-06
NTFS is a good and reliable filesystem, but it doesn’t save all the attributes of Linux files, so you are better off with a Linux filesystem.

---

