---
title: "flash drive problem"
date: 2008-05-01
forum: General Help
---

### Post by retro89 on 2008-05-01
When i plug my flash drive in and try to copy a file it wont let me. It says in the permissions that it is read only . How do I change it to write & read to transfer files?

---

### Post by njparton on 2008-05-01
Does it have a pre-existing file system and/or data?

---

### Post by Lacent on 2008-05-02
I am having the same problem, and I have used this flash drive many times with this computer with no problems. It happens with all of my other flash drives as well. Any help?

---

### Post by timcredible on 2008-05-02
i had this problem with a flash drive once.  if it's fat16 or fat32 formatted (which is what they are when you buy them), then anything that's wrong with the filesystem will prevent you from writing to it in linux (for some reason, windows doesn't care, it goes ahead and writes to drives with problems, oblivious to the fact that it can cause data loss).  anyway, just do a "dosfsck -av" on the flash drive to see if there are any problems and fix them.  I also just added a how-to to my website about this, with some screenprints, [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=57&Itemid=27").

---

### Post by Lacent on 2008-05-03
I went through your tutorial, but I get stuck on the part where you say to "just fix your drive" I'm not sure how to do this, and when I tried your sample command, it didnt work. Any suggestions?

---

### Post by articpenguin on 2008-05-03
are you sure its fat16 or fat32? Fat dosent support permissions

---

