---
title: "folder .cache keeps filling my home partition at every reboot"
date: 2007-11-19
forum: General Help
---

### Post by duartemolha on 2007-11-19
Hi everyone 

I am having a strange problem with my home partition

I have a hidden folder called .cache/tracker in my home folder that keeps filling up with files until I have no more space available in that partition

I tried deleting all those files but when I reboot the files are regenerated and the partition starts to fill up again.

The files that are produced have the filenames: file-index.tmp.###

Those anyone know how to solve this?

Best regards, 

       Duarte


PS. My system is Ubuntu 7.10 and I also installed Kubuntu

---

### Post by atlfalcons866 on 2007-11-19
can you remove tracker and that should fix the problem.

---

### Post by duartemolha on 2007-11-19
Nope

That did not solve it.

do not know what is the problem with this!!!!!

Thank you for the sugestion.

Duarte

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-19
Hi duartemolha, (I don't mean to be harsh, but) what atlfalcons866 means is

```

sudo apt-get remove trackerd

```

have you tried that?

---

### Post by dholbert on 2007-11-30
Actually, the correct command is:
```
sudo apt-get remove tracker
```
(there is no package called "trackerd" -- trackerd is just the daemon for "tracker")

One other solution is:
 - Run "tracker-preferences"  in the terminal
 - Uncheck the boxes for "Enable Indexing" and "Enable watching".

---

