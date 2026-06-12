---
title: "Need to take ownership of a new drive formatted in ext4"
date: 2014-05-03
forum: General Help
---

### Post by cptrohn on 2014-05-03
But can't figure out what I am doing wrong?


I am using ```
chwon -R users:user /media/label
```

LOL I think I have this all screwed up.

---

### Post by LastDino on 2014-05-03
Out put of..
> df -hT
and

> sudo blkid

Please? 
Also, indicate which drive exactly you want to change permissions for.

---

### Post by Elfy on 2014-05-03
> **cptrohn said:**
> But can't figure out what I am doing wrong?


I am using ```
chwon -R users:user /media/label
```

LOL I think I have this all screwed up.

try chown ;)

---

### Post by Elfy on 2014-05-03
> **Goten0007 said:**
> Out put of..

and



Please? 
Also, indicate which drive exactly you want to change permissions for.

Read the question - none of this is necessary if the OP is actually using a typo ;)

---

### Post by LastDino on 2014-05-03
> **Elfy said:**
> Read the question - none of this is necessary if the OP is actually using a typo ;)

My bad, It seems I need to have one more cup of coffee :p

---

### Post by ajgreeny on 2014-05-03
You will need to use sudo for that chown command as it must be done with root permissions, and make sure you type **chown** this time, not **chwon**.  Is the drive internal or external and do you mount it manually or in fstab?

I also think that 13.10 mounts removable drives in **/media/*username*/mountpoint** not just **/media/mountpoint** so you may need to amend the pathway in the command accordingly if it's a USB external drive.

---

### Post by cptrohn on 2014-05-03
> **Elfy said:**
> try chown ;)
Nah, the typo was here not in the terminal.

---

### Post by Elfy on 2014-05-03
> **cptrohn said:**
> Nah, the typo was here not in the terminal.

I'd do as ajgreeny says then :)

---

### Post by cptrohn on 2014-05-03
Thanks, got it kept playing around what I needed was 

```
sudo chown -R /media/USER/partition
```


I forgot that /USER/ in the file path.


Working now, thanks for looking,

---

### Post by ajgreeny on 2014-05-05
Great!  Glad to be of help.

---

