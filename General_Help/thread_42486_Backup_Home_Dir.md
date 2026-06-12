---
title: "Backup Home Dir"
date: 2005-06-17
forum: General Help
---

### Post by electroglas on 2005-06-17
I am trying to backup my home directory to an SMB file server using Nautilus, but the copy dialog goes away after several minutes with only part of the files copied.

Should I switch to the command line? How do I specify a path to a server?

Maybe something like this?
cp -r /home/username \\192.168.2.10\UbuntuBackup

---

### Post by intangible on 2005-06-17
Try this

open a terminal, and then
**sudo mkdir /remote**
**sudo apt-get install smbfs**
**sudo mount -t smbfs -o username=tridge,password=foobar,uid=1000,gid=1000 //server/share /remote**
Replace 1000 with your uid and gid (it is 1000 if you are the first user of the system)

Now you can copy files too and from using standard console commands or nautilus.

---

### Post by electroglas on 2005-06-19
Thanks, I will give it a try.

---

