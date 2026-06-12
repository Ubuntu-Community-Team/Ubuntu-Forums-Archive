---
title: "KmyMoney backup problem"
date: 2014-06-24
forum: General Help
---

### Post by joebee49 on 2014-06-24
I am running Ubuntu 14.04 LTS(Dual boot with Win 7)and Kmymoney 4.6.6 (both installed today) and when I try to use the "Backup" command from the File Menu I get a message saying "Error Copying File to Device" and no file for that day's work would show up in the backup folder.  The Device in this case is a backup folder inside the Documents folder inside my Home Folder.  Before the upgrade I had the same problem with Ubuntu 12.04LTS (also Dual boot/Win7) from May 21 2014 onward ("Backup" worked fine up until that date  then quit).  I'd like to either (1) get the Backup function working properly again or (2) find the location where Kmymoney keeps its data files and do the copying manually myself.  The trouble with option (2) is that I have no idea where to start looking for those data files.

---

### Post by oldfred on 2014-06-24
I use kmymoney in 12.04 and have not converted fully to 14.04, but happen to be in 14.04 right now. I will install it.
I already moved my kmymoney folder to a data partition, so I do not use standard default location and it refinds it correctly. 
I expect to see the new default in a hidden folder in my /home as .kymymoney or something close. Click on down arrow on right side in Nautilus and turn on hidden files & folders, and /home you should see the .kmymoney folder.

I also save as a database, but immediately reopen the standard copy. Then I can run some queries with sql on the database.

---

