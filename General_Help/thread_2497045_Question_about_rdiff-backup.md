---
title: "Question about rdiff-backup"
date: 2024-04-21
forum: General Help
---

### Post by jwoodruff on 2024-04-21
I have made use of the script published by TheFu in the how-to here <https://lpi.jdpfu.com/2023-Backups/2023-Backup-How-To.html>, -Thank-you to TheFu!
My script reads:
/usr/bin/rdiff-backup -v5 backup \
        --exclude-sockets --exclude-device-files --exclude-fifos \
        --exclude '**/cache'  --exclude "$TGT" \
        --include /usr/local  --include /etc \
        --include /root       --include /home \
        --exclude '**'  /      "$TGT"
My question is:
Should not the "--exclude '**/cache'" statement prevent backing up my cache files?
I ask, as I have 38,096 lines of /cache... recorded in the backup
eg.

Processing file home/joe/.cache/mozilla/firefox/yezx7u17.default-release/cache2/entr   6152 ies/04654E72EA0E9E33...

I'm not sure, but I thought backing up these files was unnecessary and would waste space and resources?
I would appreciate some clarification on this and assurance if I have things optimised.
Thanks in advance for any help offered

---

### Post by TheFu on 2024-04-22
Details matter.

```
--exclude '**/cache' 
```
and
```
home/joe/[COLOR="#FF0000"].[/COLOR]cache/
```

Look closely.  

If you don't want ~/.cache backed up, which I think is sensible, you should have 
```
--exclude '**/.cache' 
```
Right?

---

### Post by jwoodruff on 2024-04-22
Of course.
Thank-you again

---

