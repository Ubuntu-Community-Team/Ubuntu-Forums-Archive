---
title: "VM Windows to Ubuntu server rsync transfer scheduled every day, how can I pull it off"
date: 2015-09-23
forum: General Help
---

### Post by vperaino on 2015-09-23
So, here in Le Office there are two Ubuntu machines with VBox Windows on them. I routinely need to access data off of them that the running programs won't allow me to put in a shared folder, and upload that data to a respective Ubuntu server. 

I'd like to be able to automate this process so that a daemon runs it every day at whatever time, since I don't want to have to constantly interrupt the people working on the machines to plug a USB key into their box (which isn't recognized half the time by VBox anyway) and get it manually. 

I assume this has to be accomplished with Cygwin somehow, but I'm not too familiar on its use. Anyone got any bright ideas?

---

### Post by TheFu on 2015-09-23
Pull the data from the Windows machines, use cron to schedule it in Ubuntu.

I wouldn't use cygwin - too bloated.  I have automated some tasks on windows by using strawberry perl - it "feels" like unix perl, so I don't have to deal with most Windows things. Plus it doesn't need cygwin.  On Windows, the "schedule" utility is much heavier and it isn't aways clear which userid it runs stuff as.  You could check the running processes with perl and only try the data copy when it is NOT running .... or swap out the icon they click to run the program so that when it is shut down, another script or robocopy or rsync or .... copies the latest data file changes to the Linux storage.  Or you could move the data files so they are actually stored on the Linux storage, always, then you don't have to worry about client disk failures.  This is what I do for Quicken/Quickbooks data. Much easier, plus I don't have to worry much about the users taking proprietary financial data on their laptops on travel.

---

### Post by vperaino on 2015-09-23
So it'd just be easier to have a Windows batch file move everything via the Windows Scheduler to a shared folder, and then have a cronjob transfer things from there? I guess I could do that.

---

### Post by SeijiSensei on 2015-09-23
If you share the folders where the files are written and mount them on the Ubuntu host, you can do everything from Ubuntu and not need Windows Scheduler at all.  Just run a cron job to copy the shared folder(s) with rsync.  If you can also mount the folder on the machine where the uploaded data is written, you can do everything in one task.  If the upload target cannot share its directory with the Ubuntu host but has an SSH server, you can access it directly with rsync.

---

