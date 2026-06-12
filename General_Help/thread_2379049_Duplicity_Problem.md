---
title: "Duplicity Problem"
date: 2017-11-30
forum: General Help
---

### Post by georgia-linux on 2017-11-30
I am running Ubuntu 16.04 on my desktop.  I have set up a backup program using **rsync** commands in **crontab**, and it is working fine.  However, I have noticed that I have been running **duplicity** also since September 11, 2017.
[LIST]
[*]I have not run **duplicity** manually 
[*]I have not set up **duplicity** in **crontab** 
[*]I have not set up a shell script that runs **duplicity** in it 
[*]**duplicity** is not set up to run on startup 
[*]I do not know how to look in the log files to see how / when it is running 
[/LIST]

I have searched my system for files specifying **duplicity** and some of the files reference **deja-dup**; example--

/home/george/.cache/deja-dup/0560d5c8429733bd73f16e11ca81a8b7/duplicity-new-signatures.20171117T124714Z.to.20171118T123930Z.sigtar.gz

The dotted statements above referring to **duplicity** are also true for deja-dup. I would appreciate any suggestions to help me find out how / when this programming is running, so that I may stop it.  Thanks.

---

### Post by speartip on 2017-11-30
If you are using rsync to backup, then you do not need deja-dup or duplicty, so what does the command:
```
sudo apt remove --purge deja-dup duplicity
```
return with?

---

### Post by untrustytahr on 2017-11-30
> **georgia-linux said:**
> I am running Ubuntu 16.04 on my desktop.  I have set up a backup program using **rsync** commands in **crontab**, and it is working fine.  However, I have noticed that I have been running **duplicity** also since September 11, 2017.
[LIST]
[*]I have not run **duplicity** manually
[*]I have not set up **duplicity** in **crontab**
[*]I have not set up a shell script that runs **duplicity** in it
[*]**duplicity** is not set up to run on startup...
[/LIST]

I would appreciate any suggestions to help me find out how / when this programming is running, so that I may stop it.  Thanks.

Deja-dup is just a front end for duplicity, so the files on the back-end are in 'duplicity' format.  It does not launch via cron, but uses its own timer mechanism.  You may have turned it on at sometime in the past.  You can just open deja-dup and switch it off via the button along the top menu.  Alternatively, you can remove it if so desired as previously mentioned.

---

