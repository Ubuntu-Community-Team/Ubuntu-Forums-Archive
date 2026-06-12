---
title: "Server 12.04 - Command runs from command line but won't execute in CRON"
date: 2013-08-12
forum: General Help
---

### Post by joe_bloggs2 on 2013-08-12
I have the following CRON config.

```
# m h  dom mon dow   command
0 0 * * * /home/lusiphur/scp_sh.sh > /home/lusiphur/scplog

```

The script has the following -

```
#!/bin/bash
scp <server removed>:/home/lusiphur/files/The.Iceman*/* /mnt/md0/incoming/
scp <server removed>:/home/lusiphur/files/House.Of.Cards*/*.mkv  /mnt/md0/Video/TV/"House of Cards"
scp <server removed>:/home/lusiphur/Ultimate* /mnt/md0/incoming/
```

The first SCP command completed successfully. The second and third (but the third has an invalid path so lets ignore that) did not. The scplog file is empty. In /var/log/syslog* we have

```
Aug 12 00:00:01 Tenth CRON[28100]: (lusiphur) CMD (/home/lusiphur/scp_sh.sh > /home/lusiphur/scplog)
```

And no other relevant entries.

The command 

```
scp <server removed>:/home/lusiphur/files/House.Of.Cards*/*.mkv  /mnt/md0/Video/TV/"House of Cards"
```

executes fine from the command line.

Any help gratefully appreciated.

---

### Post by papibe on 2013-08-12
Hi joe_bloggs2.

A few ideas:

Escape the wild card:
```
scp server:/home/lusiphur/files/House.Of.Cards\*/\*.mkv
```
Quote the whole path:
```
scp ...  "/mnt/md0/Video/TV/House of Cards"
```
Use the verbose option so that you have a log:
```
scp -v ...
```
Let us know how it goes.
Regards.

---

### Post by joe_bloggs2 on 2013-08-12
> **papibe said:**
> Hi joe_bloggs2.

A few ideas:

Escape the wild card:
```
scp server:/home/lusiphur/files/House.Of.Cards\*/\*.mkv
```
Quote the whole path:
```
scp ...  "/mnt/md0/Video/TV/House of Cards"
```
Use the verbose option so that you have a log:
```
scp -v ...
```
Let us know how it goes.
Regards.

Can mark this solved.

```
scp ...  "/mnt/md0/Video/TV/House of Cards"
```

Did the trick. Thanks for the prompt assist :)

It's still weird how the previous version worked on the command line. Oh well.

---

### Post by papibe on 2013-08-12
Glad you worked it out :D

Please mark the thread as SOLVED when you have the chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

