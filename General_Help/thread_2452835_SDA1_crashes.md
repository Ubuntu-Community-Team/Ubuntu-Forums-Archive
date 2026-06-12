---
title: "SDA1 crashes"
date: 2020-10-29
forum: General Help
---

### Post by stormfinger on 2020-10-29
hi 
i have two disks ..primary is SSD nvm2 and sata 1tb toshiba disk that is serving as home directory ..on elementary and now on kubuntu my sda1 toshiba crashes even that i properly shutdown system ..i must then start fsck on sda1 and it reports several garbage files and on one occasion i had to reinstall plasma. can somebody help  ? i have dell g7 computer if anyone wants to check computer configuration. plasma is 5.18 kernel 5.04 kubuntu 20.04 ..most of the times i see that chrome directories are the problem.

thank you

---

### Post by ActionParsnip on 2020-10-29
If you boot to a live CD / USB desktop and run a full fsck manually, does it help?
Are all cables seated OK?
Do you have the latest BIOS?

---

### Post by dinkidonk on 2020-10-29
The problem may be caused by a failing drive, have your tried to review the S.M.A.R.T. data for the drive?

---

### Post by stormfinger on 2020-12-26
1.i must check on latest BIOS..i did upgrade when bought laptop when disk falls apart it doesnt let me login until i run fsck manualy. 

2.i dont quite understand how to review S.M.A.R.T. data.
regards

sory for late reply i didnt get mail notification of your reply..

---

### Post by guiverc on 2020-12-26
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

S.M.A.R.T. is built into drives, Self-Monitoring, Analysis and Reporting Technology, which if monitored regularly, gives you (ideally) prior warning of a drive failing, so you can be prepared to replace it & avoid data loss.

It can be read many ways, via command line tool, GUI tool etc.

---

### Post by stormfinger on 2020-12-30
thank you very much ...ill check it :)

regards

---

### Post by stormfinger on 2020-12-31
Hi ive done SMART test on my drive ...screen says all is ok.. today disk chrashed and KDE Plasma was missing all sorts of application shortcuts and i had to reinstall intelij idea also.. i hope i wont start missing project files. ... i realy need advice.. is it problem that i have toshiba designated as my home directory? 
[ATTACH=CONFIG]287655[/ATTACH]

[ATTACH]287656[/ATTACH]

---

### Post by dinkidonk on 2021-01-02
The SMART data reports that the drive has suffered 3 hard shocks/knocks, and this could indicate that the computer may have been dropped a couple of times or something. The connector for the drive may have become unseated and a loose connector could very well be a probable cause for you problems, so I would check that.

---

### Post by stormfinger on 2021-01-03
thank you very much for reading it throu and explaining...i didnt know what to look for ..ill get it to service couse its still under waranty.

regards

---

### Post by stormfinger on 2021-01-18
update 

i went to service and they checked disk with tool "hard disk Sentinel" which didnt show any errors on disk. When i came back i disabled sleep on idle on laptop ..and disk hasnt crashed since then.

---

### Post by stormfinger on 2021-02-21
Now i can say it was Sleep on idle function that crashed my computer ...from previous post till today and not a single crash

---

### Post by TheFu on 2021-02-21
> **stormfinger said:**
> Now i can say it was Sleep on idle function that crashed my computer ...from previous post till today and not a single crash

It would be EXTREMELY helpful if you used the Thread Tools button near the top and marked this thread as SOLVED.  This lets us know it is solved so people looking for answers will find it and people looking to help won't bother.

---

