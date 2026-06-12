---
title: "File Sharing Question"
date: 2008-02-24
forum: General Help
---

### Post by uberlube on 2008-02-24
Is there a simple way to make a shared folder on my desktop PC that my laptop can grab from? I was just looking as samba and ssh, and havent gotten my head wrapped around them yet. Are they the only 2 options or is there an easier way?

---

### Post by uberlube on 2008-02-24
Bump

---

### Post by uberlube on 2008-02-24
Bumpity bump bump :)

---

### Post by motoperpetuo on 2008-02-24
are you sharing files between two linux computers, or linux and windows? if that latter, i've had good luck with samba. try this how to:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

as far as sharing files between two linux computers, i've used filezilla. it gets the job done, but frankly, i'd like something that works more like samba. that is, i'd like to be able to have a mount point or link on computer A that's really a directory on computer B. haven't figured out how to do this yet, though.

---

### Post by uberlube on 2008-02-25
Ya its linux to linux.

---

### Post by Iowan on 2008-02-25
You can setup NFS file sharing - but it's probably no (or not much) easier than Samba or SSH.(I usually use SSH and it's component SCP to move files between the linux boxes on my network)

---

### Post by motoperpetuo on 2008-02-28
> **Iowan said:**
> You can setup NFS file sharing - but it's probably no (or not much) easier than Samba or SSH.(I usually use SSH and it's component SCP to move files between the linux boxes on my network)

is there a way you use SSH and SCP to set up something similar to a drive mapping in windows? that is, could i have a link on my desktop (or elsewhere) on a computer running ubuntu that would link directly to a specific directory on a windows computer on my network?

---

### Post by motoperpetuo on 2008-02-29
> **motoperpetuo said:**
> is there a way you use SSH and SCP to set up something similar to a drive mapping in windows? that is, could i have a link on my desktop (or elsewhere) on a computer running ubuntu that would link directly to a specific directory on a windows computer on my network?

i found what i was looking for here:

[http://ubuntuforums.org/showthread.php?t=710610&highlight=open+ssh](http://ubuntuforums.org/showthread.php?t=710610&highlight=open+ssh)

---

