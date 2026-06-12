---
title: "missing disk space"
date: 2007-04-26
forum: General Help
---

### Post by bturrie on 2007-04-26
I'm running a kubuntu edgy system with a 120 gig seagate drive. yesterday I got a disk full message. Looking in Konqueror it says i have only 4 gig of free space and I needed to delete some unused files to get that. 

On the other hand I can only see 30 gig or so of files when I add up the sizes of all the folders in the root directory. I installed and ran filelight and it reports 25.9 gig worth of files. The trash is empty. I ran fsck -p and it said all is well. 

I suspect I did this to myself when I created a backup file using tar in preparation for upgrading to feisty. I forgot that ext3 only allows files up to 4 gig. My backups (i can't believe i did this stupid thing twice) were 30 gig each. When I remembered the limit i deleted both files. They disappeared but didn't go to trash and I never got the space back either. 

Is there anything I can do short of a fresh install?

---

### Post by bturrie on 2007-04-26
I found the files. They were in /root/.local/share/Trash/files. ;D Now all I have to do is figure out how to get rid of them

---

