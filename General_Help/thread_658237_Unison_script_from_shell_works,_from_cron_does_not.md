---
title: "Unison script from shell works, from cron does not"
date: 2008-01-04
forum: General Help
---

### Post by JeremyLaurenson on 2008-01-04
Hi all,

I have set up a shellscript to use unison to sync 3 computers. The script runs fine normally, but when run from cron as the same user (root), unison does nothing. The script runs fine but Unison does not seem to do anything

I have mucked around with some environment variables but am getting nowhere... can someone help?

---

### Post by drs305 on 2008-01-04
Posting the script would probably be the first step in helping to resolve your issue. That will probably answer questions that would have to be asked before definitive suggestions can be offered.

---

### Post by JeremyLaurenson on 2008-01-04
Here it is:


set UNISON=/root/.unison
set USER=root
set HOME=/root

if mount | grep "//jlaurens-xp/home" > /dev/null
then
echo >> synclog.log "Jeremy Documents: Already connected"
else
echo >> synclog.log "Jeremy Documents: Trying to connect"
smbmount //jlaurens-xp/home /mnt/jeremy_documents/ -o username=jlaurens,password=*****,rw
fi



echo >> synclog.log "Syncing Jeremy Documents"
if mount | grep "//jlaurens-xp/home" > /dev/null
then
unison  /data/documents /mnt/jeremy_documents/Documents -auto -prefer /data/documents -batch -fastcheck true -log -logfile /usr/scripts/sync_jeremy.log -perms 0 -ignorecase true -pretendwin
else
echo >> synclog.log "Syncing can not continue: not mounted."
fi

---

### Post by JeremyLaurenson on 2008-01-04
I figured out the issue. I found another thread that said cron has an issue with commands that put out too much to standard out. When I redirected that to /dev/null, it worked!

> /dev/null 2>&1

---

### Post by dcstar on 2008-01-05
> **JeremyLaurenson said:**
> Hi all,

I have set up a shellscript to use unison to sync 3 computers. The script runs fine normally, but when run from cron as the same user (root), unison does nothing. The script runs fine but Unison does not seem to do anything

I have mucked around with some environment variables but am getting nowhere... can someone help?

Cron runs with its own environment and shell settings, your script should also be in a standard format (look at the other ones in your system for examples of how it should be) to ensure it has a better chance of success outside of your user terminal.

---

