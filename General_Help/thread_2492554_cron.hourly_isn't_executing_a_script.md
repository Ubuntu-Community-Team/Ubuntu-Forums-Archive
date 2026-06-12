---
title: "cron.hourly isn't executing a script"
date: 2023-11-14
forum: General Help
---

### Post by helotbc-0 on 2023-11-14
I am attempting to run "duplicity" in a bash script daily called "backup.sh" to backup files on /storage to /backup. The disk /backup is a USB drive and is the same size as /storage. I have put it in cron.hourly to test it. The script runs when launched as "sudo ./backup.sh", but not under cron. Details of my situation are:

OS version: 
```
Operating System: Ubuntu 22.04.3 LTS              
          Kernel: Linux 5.15.0-86-generic
    Architecture: x86-64
```

Script:
```
#! /bin/bash
export PASSPHRASE=<password to encrypt backup>
/usr/bin/duplicity --full-if-older-than 1M --log-file /home/brendan/backup.log  --name media-backup /storage file:///backup
/usr/bin/duplicity remove-older-than 1Y --force file:///backup
unset PASSPHRASE

```

run-parts doesn't detect an executable script
```
brendan@hickory:~$ run-parts --test /etc/cron.hourly
brendan@hickory:~$ 

```

run-parts gives an error
```
brendan@hickory:~$ run-parts --debug /etc/cron.hourly
"..": classicalre fail
"backup.sh": classicalre fail
".": classicalre fail
".placeholder": classicalre fail
```

the script file is executable
```
-rwxr-xr-x   1 root root  525 Nov 13 21:19 backup.sh
```

cron.hourly is running at 17min after the hour, per journalctl
```
Nov 14 05:17:01 hickory CRON[104343]: pam_unix(cron:session): session opened for user root(uid=0>
Nov 14 05:17:01 hickory CRON[104344]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 14 05:17:01 hickory CRON[104343]: pam_unix(cron:session): session closed for user root
Nov 14 06:17:01 hickory CRON[104382]: pam_unix(cron:session): session opened for user root(uid=0>
Nov 14 06:17:01 hickory CRON[104383]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 14 06:17:01 hickory CRON[104382]: pam_unix(cron:session): session closed for user root

```

---

### Post by SeijiSensei on 2023-11-15
```
#! /bin/bash
```

Remove the space after the exclamation point and see if it works.

---

### Post by philhughes on 2023-11-15
From man cron:

"Additionally, the file names must conform to the filename requirements of run&#8208;parts: they must be entirely made up of letters, digits and can only contain the special signs underscores (&#8217;_&#8217;) and hyphens (&#8217;&#8208;&#8217;). Any file that does not conform  to  these  require&#8208;ments will not  be executed by run&#8208;parts. For example, any file containing dots will be ignored."

---

### Post by helotbc-0 on 2023-11-15
I've removed the space. I'll check on it later.

---

### Post by helotbc-0 on 2023-11-15
I did read the man page and missed the statement about using dot. -Thx

---

### Post by helotbc-0 on 2023-11-15
philhughes, Changing the name got me started. I ran the following and run-parts is recognizing the file:

```
brendan@hickory:~$ run-parts --test /etc/cron.hourly/
/etc/cron.hourly//backup-sh
```

Duplicity is running. I'm now getting a permission error. I'll work on it and report back. Thx again.

---

