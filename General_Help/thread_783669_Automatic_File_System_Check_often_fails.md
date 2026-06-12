---
title: "Automatic File System Check often fails"
date: 2008-05-05
forum: General Help
---

### Post by TransplantedCanuck on 2008-05-05
The Automatic File system check seems to fail more often than not (/dev/sdb1 Unexpected inconsistency, run fsck manually).

Its easy enough to fix (thanks to google) with 

fsck -y /dev/sdb1


What I want to know, is WHY DOES THIS HAPPEN!? we shut the computer down properly and don't do anything strange. Any ideas at least where I can start looking to solve this problem? I'm running Hardy.

---

### Post by Monicker on 2008-05-05
Do the logs in /var/log/fsck/ show that any problem are being repaired?  Might be something starting to go bad with the drive itself.  You might check the site of the drive maker for a diag tool.

---

### Post by TransplantedCanuck on 2008-05-06
> **Monicker said:**
> Do the logs in /var/log/fsck/ show that any problem are being repaired?  Might be something starting to go bad with the drive itself.  You might check the site of the drive maker for a diag tool.

Thats all there is, so  I'm gonna assume there isn't anything.

Log of fsck -C3 -a -t ext3 /dev/sdb1
Tue May  6 06:10:14 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sdb1: clean, 196473/60293120 files, 13339793/120575849 blocks

Tue May  6 06:10:14 2008
----------------

Log of fsck -C3 -R -A -a
Tue May  6 06:10:15 2008

fsck 1.40.8 (13-Mar-2008)

Tue May  6 06:10:15 2008
----------------

---

### Post by CaptainCanuck on 2008-05-06
Well, I'm at work now, so I'll run a check with the seagate tools tonight, but I'm seriously doubting its the harddrive, seeing as how its only about a month and a half old.

---

### Post by CaptainCanuck on 2008-06-26
It still happens every 2nd or 3rd filesystem check (of the automatic variety).

Steps I've done over the last while:
- Seagate tools - everything healthy
- Hooked it up to my windows box, copied some raw video data back and forth a few dozen times, checked error logs: empty
- same thing but with multiple tiny files: no errors
- waited for the error, put in a ubuntu live CD: No errors


Ideas? This is annoying since everytime it happens (often at 5am when the wife wakes up to get ready for school), I have to get up and fix it. Or other times when she comes home from school and I have to walk her through it by phone.

---

