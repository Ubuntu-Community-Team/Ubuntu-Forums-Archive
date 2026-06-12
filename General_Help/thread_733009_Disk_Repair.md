---
title: "Disk Repair"
date: 2008-03-23
forum: General Help
---

### Post by teeleef on 2008-03-23
Ladies & Gents,


I have had two drives fail on me in the last month.

I am running Gutsy and have 4 drives in my tower pc.  One for / and swap on for /home and two remaining for data and backup.

I was copying some files when the copy process became really slow!  I cancelled the copy process and that's when it all went wrong:confused   The drive icon disappeared from the desktop.  On a reboot I got file check errors.  I tried using GParted to delete the partition and create a new one........no joy there.:(

I don't think the failure is down to overheating but you never know...

My question is can the 320gb drive be repaired or low level formatted under Linux?   If not it seems that having 4 drives on my pc could be a costly business!


Teeleef

---

### Post by HermanAB on 2008-03-23
Depends on what failed. If you have multiple identical failed drives, then you can try swapping the controller cards and see whether you can revive some of them.  however, I would never trust such a drive again.

---

### Post by teeleef on 2008-03-23
Thanks HermanAB ,     yes I did swap the connectors so it wasn't the problem.  

Anyway good news...... I searched the forums and came up with a link to the Testdisk program.  I ran that from a terminal (that is amazing in itself as I tend to shy away from the command line), anyway I ran the program and repaired the mbr.

GParted repartitioned  the drive and my data (80gb's worth) was transferred from my external backup drive.

It really makes you realise that a backup drive is essential nowadays and that a drive can fail with little warning.  I must admit though I think the drive failure was initially of my doing.

Thanks for your help! :)



Teeleef

---

### Post by smoker on 2008-03-23
just a suggestion, a straining power supply can cause problems with drives and such when maxed out for long periods, or failing. may be a good idea to have it checked out just in case it has any bearing on the drives failing, especially with running four drives in the tower,

---

### Post by teeleef on 2008-03-23
One more thing folks....

What sort of temperatures are your hard drives running at?   I have 3 running around 40degs and one at 60.  Are these normal?


Teeleef

---

### Post by smoker on 2008-03-23
i'd say anything over 50 is maybe too hot, but obviously different makes have different tolerances, best way is to check at the particular hard drive manufacturers support sites for guidance.

DFT is a good tester of the integrity of hard drives, including the smart attributes which take into account temperatures:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

---

