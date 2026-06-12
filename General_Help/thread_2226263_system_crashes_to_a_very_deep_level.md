---
title: "system crashes to a very deep level"
date: 2014-05-26
forum: General Help
---

### Post by DrScum on 2014-05-26
I am running ubuntu 12.04 LTS on a Dell Latitude E5420. When trying to copy larger files (approx. 500MB) the system crashes frequently to a level where not even the sysrq key combination works. The only way to get back into business (I found so far) is to cut the power.

How can I diagnose and preferably fix this problem?

---

### Post by SeijiSensei on 2014-05-26
Let me ask a more basic question. Are any Windows machines involved in these file copying tasks, or are they all between *nix machines?  If there are no Windows machines involved, you have many better options than Samba.  For full-time file sharing, you should use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") in an all *nix environment.  For one-off file copying over the network, use rsync or scp.

---

### Post by DrScum on 2014-05-26
I know, I know, but unfortunately there are windoze machines involved.

---

### Post by DrScum on 2014-05-28
Today the crash happened during writing an e-mail with Thunderbird. Maybe the file copying isn't the only trigger.

Here my questions again:
how do I diagnose a problem like this?
how can I fix it?

---

### Post by DrScum on 2014-06-12
After about 2 weeks of observing I come to the conclusion that the system crashes are linked to samba, thunderbird and Xournal. Alternatively it could be caused by the X11 software which, of course, is always involved. 
I have about 1 system crash of the kind described about every 3 days which I think is too much. I am also afraid that at some point I might loose important data.

My question: how do I go about diagnosing something like this?

---

### Post by DrScum on 2014-07-13
Since I moved on to Lubuntu 14.04 LTS I'll just mark this thread 'solved'

---

