---
title: "60GB hdd FULL!  wifes laptop!,  help!"
date: 2008-05-27
forum: General Help
---

### Post by mfaust731 on 2008-05-27
hey guys,
K, here what i got. I converted my wife to ubuntu about a year ago, she loves it. Ive used linux of some form since 98, however I claim to me no master. She has a hp notebook with 8.04, got wifi an all that working fine. i have a ubuntu sever downstairs to store all her pictures and stuff on.
she came home today, and the 60gb drive is complete full!
I checked /var & /tmp and see nothing huge there, also looked in the /home folders and cant see where all the space is being used.

what is the next step?

---

### Post by Woody1987 on 2008-05-27
Go to Applications->Accessories->Disk Usage Analyser

From here you can scan your harddrive and you will be able to see which files are taking up your space.

---

### Post by PadreSol on 2008-05-27
Run du -sh /*
Then find the directory that's the largest consumer of disk space.

cd /tolargestconsumer
du -sh *

Until you find the disk hog.

---

### Post by mfaust731 on 2008-05-27
Sweet!, you guys rock!
I had a backup program saving to /home/server/backup instead of /server/backup which is a samba share on my box downstairs.
Dont know how I missed that!

Thanks!

---

### Post by alguin2 on 2008-05-27
The first place that I'd check is your wife's home directory, /tmp and /var/tmp.  The following will show the total size of these directories in **megabytes**:

Open a terminal screen (Applications->Accessories->Terminal) and type the following du (disk usage) command:

[INDENT][/INDENT][SIZE="3"]**du -sm $HOME  /tmp  /var/tmp**[/SIZE]  
 

Note that if you get any "Permission denied" advisories, it just means that du can't examine subdirectories you don't have privs for.  

If any of these directory trees show tens of thousands of megabytes in disk space, then that's your culprit.


To drill down and find the subdirectory in a particular directory tree that's hogging up all the disk, type in the command below -- substitute the directory tree to investigate (in this case $HOME is used as an example).  Command below recursively checks the directory (eg $HOME) and prints disk usage but limiting the top 20 hogs in decreasing hog size:

[INDENT][/INDENT][SIZE="3"]** find $HOME -type d -exec du -sm '{}' ';' | sort -nr | head -20**[/SIZE]

Good luck

---

