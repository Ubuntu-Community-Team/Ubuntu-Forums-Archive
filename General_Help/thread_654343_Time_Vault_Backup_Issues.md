---
title: "Time Vault Backup Issues:"
date: 2007-12-31
forum: General Help
---

### Post by klepto on 2007-12-31
I've used many back methods like Reoback, rdiff-backup, Boot It NG, Acronis, etc. 
I had heard that timevault backs up your data according to a schedule and also 
monitors changes in files and such for differential backups. Well I have configured time vault 
according to the ubuntu wiki and in 24 hours it has backed up 32meg in my 2gb home folder. 

Does anyone know why it hasn't made a full backup yet?

---

### Post by dlegend on 2007-12-31
1. Check your "Advanced" settings under the General tab. There should be an option that says "Maximum File Size to back up" which is default to 32 mb. Change this to a larger value if you have large files that you want to back up such as video / games / iso files / etc... 

2. Also ensure that you have a large enough value for the "Reserved Free Space" option located in the same area.

3. You already stated you have it setup to include your home folder so I'm assuming that is correct. 

Let me know if you have that setup correctly or not.

---

### Post by klepto on 2007-12-31
Thanks for the tip, 

I didn't have the free space in order to back up my home folder. 
Both values were changed so I hope i starts to backup everything. 

Is there a way to make it manually make a backup?

---

### Post by dlegend on 2007-12-31
I'm not aware of any manual method of backing up through TimeVault though you could check this page: [https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault) (I couldn't find anything).

Best thing to do is just wait and see. I have had mine running for a few weeks now with 1.6 GB in backups. I use mine mostly to backup small files and have it set to update every 5 minutes.

---

### Post by daengbo on 2007-12-31
I really wanted to like TimeVault. It looks nice and easy, but I found it wasn't backing up file which I knew had changed. I just couldn't accept that. HUBackup works well, but HURestore has been broken for 14 months without any sign that it will be fixed.

I finally settled on Flyback. I didn't have to install anything. I just downloaded the code from Google and ran it under python once. That created a config and cron job. I don't use the client for anything because the backup file system is so simple.

---

