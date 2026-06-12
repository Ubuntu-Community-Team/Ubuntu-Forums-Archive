---
title: "Why is GRSync failing transfers for permission errors?"
date: 2021-05-06
forum: General Help
---

### Post by sofasurfer on 2021-05-06
Why is GRSync failing transfers for permission errors?
I am the only user on the system and when I do a backup on /Home I get a ton of fails.
Examples follow. There are a 4 times as many as I gave listed. It seems that every folder in /Home was saved but still is listed as failed failed. Does this mean that there are some files that failed and thus it is shown that the folder failed? If so, the question remains, why? Am I simply required the run from terminal as root?

```
 rsync: opendir "/home/daryl/daryl/.synaptic" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/.thunderbird" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/BRF" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/Desktop" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/Documents" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/Downloads" failed: Permission denied (13)
rsync: opendir "/home/daryl/daryl/Music" failed: Permission denied (13)  
```

---

### Post by TheFu on 2021-05-07
Show the permissions for the source and the target, so someone might be able to help.
Also need to know the id, userid, group for the userid running the process.

```
id
ls -la /home/daryl/daryl
ls -al {the other path - can't tell if this is the source or target}
```

---

