---
title: "Are /home and /tmp the only places I can create new folders?"
date: 2007-01-13
forum: General Help
---

### Post by tc101 on 2007-01-13
I want to back up everything in /home to a folder so if I mess something up while trying to change a configuration I can just go to the command line and copy that backed up home folder back to itself.  

I am not clear about how long stuff stays in /tmp but I know it disappears eventually.  However I can't see anywhere else, other the /home and /tmp where I can create new folders.

---

### Post by llamakc on 2007-01-13
sudo mkdir /opt/backup

or anywhere you want to create it.

Or just tar it up:

sudo tar -cf /opt/myhomebackup.tar /home

---

### Post by Hossie on 2007-01-13
Per definition, /tmp gets cleaned on boot. You can a, store your files in /var/tmp (which, per definition, does not get cleaned on boot), or you use sudo to store your file anywhere.

---

### Post by tc101 on 2007-01-13
Great.  Thanks for the info.  I see how it works now.

I have some other questions about doing a quick restore after a crash, but I am going to start a new thread to ask about that.

---

