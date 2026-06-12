---
title: "openoffice writer document recovery - please help ASAP"
date: 2008-03-07
forum: General Help
---

### Post by VCSkier on 2008-03-07
I was almost done with a lenghty research paper and OpenOffice writer crashed...  When I restarted it the document recovery window came up, but it restored a very old copy of the paper, at a point when I had only started writing.  Is there *any* way to recover the rest of it.  The paper was the final project for this course.  It's due in 2 hours (midnight US Eastern Standard Time), and I had put maybe 15 hours into it already.

I had OOo setup to automatically save the document every 15 minutes...

---

### Post by davarino on 2008-03-08
I hope this is not too late for you, and that it is helpful.

Assuming you are using Gnome:

Click on Places in the top Gnome menu. Then click on Home Folder.

On the menu of the home folder window that pops up, click View > Show Hidden Files.

Look for the folder /.openoffice.org.2 (remember the dot at the front of the folder name, and that the name of the folder may be slightly different deppnding on which version of OO.o that you are using). Click on it. Then click on the subfolder /user. Then on /backup.

In /backup you will find the latest backup of your file. Perhaps you changed a file name partway through your composition. In any case, I hope that the backup file you find is more recent than the one you were presented with by the backup recovery screen.

Good luck.

---

### Post by VCSkier on 2008-03-08
Thanks for the advice.  It was the same old version, but that's good to know for the future, although I think from now on I'm going to be saving my papers religiously.  :)

---

### Post by Hagar Delest on 2008-03-08
Had you manually saved while writing your document? In such case, save the recovered file under a different name from the original one and check the original file on your HD. Sometimes, OOo recovers an older temporary version even if the real file is newer.

---

### Post by VCSkier on 2008-03-08
The last time I had manually saved the file was about 10 mins after starting, which I believe is what OOo had restored.  The nearly finished copy of the paper (which I hadn't saved) is nowhere to be found.  Oh well.

---

### Post by NCLI on 2008-03-08
You may want to tell OOo to save your documents automatically at regular intervals. There should be an option for it in Preferences.

---

### Post by boeing777 on 2008-03-08
> **VCSkier said:**
> The last time I had manually saved the file was about 10 mins after starting, which I believe is what OOo had restored.  The nearly finished copy of the paper (which I hadn't saved) is nowhere to be found.  Oh well.

that means you wrote a lot of stuff in ten minutes if what you wrote is nowhere to be found.

---

### Post by davarino on 2008-03-09
> **NCLI said:**
> You may want to tell OOo to save your documents automatically at regular intervals. There should be an option for it in Preferences.

There is:

Tools > Options > Load/Save > General ... and then check boxes for Always create backup copy and for Save autorecovery copy every || minutes.

---

