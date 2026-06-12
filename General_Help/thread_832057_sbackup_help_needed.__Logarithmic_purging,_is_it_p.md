---
title: "sbackup help needed.  Logarithmic purging, is it practical ?  too much space ?"
date: 2008-06-17
forum: General Help
---

### Post by kraymore on 2008-06-17
I am using sbackup and am wondering if i should use Logarithmic purging.  or if i should have it erase backups more than 2 days old ?  i can't seem to tell it to erase backups that are 1 day old, so i figured 2 would work.  the thing is -- i have a 750GB backup drive, and 800GB of potential data to backup, so with it backing up and not removing old backups so often, i'm guessing it wont just update the backup files but actually create separate .tgz tarballs which could easily exceed my backup storage space.  i hope i am wrong about that, can anyone say ?

thank you

---

### Post by bufsabre666 on 2008-06-17
sbackup only really backs up the important files of the operating system, it passes over most if not all multimedia and only does the important places like home. you can also add other files and locations to back up, but to the topic logarithmic is the best method i can see just incase you accidentally delete a file a now but dont notice it till next week, it will maintian a bunch for time time period but not all so it doesnt take up too much space while still maintaining alot of data

---

### Post by kraymore on 2008-06-17
i told sbackup to only backup my /home directory, specificing it in the inclusions.  in the exclusions i removed the entries of the filenames it would not normally backup (like .mp3 .mpeg mpg etc) as well as unchecked a option that would make it ignore files that are too big.  i think with these changes it will essentially backup what you tell it to.  

if i read you right, sbackup only backs up files that have changed when it goes to backup things again.  

thanks

---

