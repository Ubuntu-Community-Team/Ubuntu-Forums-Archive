---
title: "Best backups method for multiple users."
date: 2019-04-20
forum: General Help
---

### Post by Tadaen_Sylvermane on 2019-04-20
I like Deja Dup's simplicity. However it seems to only run when logged in. We have simplified our computer life down to a single main computer in the house. Just the wife and I. We each have a user account on this main computer. I need to backup with ease both of our data automatically. But it must run on it's own regardless of logged in status. What should I be looking for? I would prefer not to go with manual rsync backups if possible. This will be backed up over the network to the main server in the living room.

---

### Post by Tadaen_Sylvermane on 2019-04-20
Solved with a simple script I hacked together using Duplicity from the command line. Created a specific user to hold backups on my server. This is the script. Installing duplicity didn't pull in the proper dependencies. For this to work I also had to manually install python-paramiko I think it's called.

```
if [[ "$USER" == root ]] ; then    
    for user in /home/* ; do
        BACKUPUSER=$(basename "$user")
        TARGETDIR="$POOLLOC"/backups/.googledrive/homebackups/"$BACKUPUSER"
        if ssh backups@"$SERVERFQDN" "[[ ! -d ${TARGETDIR} ]]" ; then
            ssh backups@"$SERVERFQDN" "mkdir -p ${TARGETDIR}"
        fi
        duplicity \
        --exclude-if-present .nobackup \
        --no-encryption \
        /data/"$BACKUPUSER" scp://backups@"$SERVERFQDN"/"$TARGETDIR"
    done
fi
```

---

