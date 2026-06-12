---
title: "Folder permissions"
date: 2008-02-27
forum: General Help
---

### Post by TaoBoogie on 2008-02-27
I had Gutsy and Feisty installed on the same drive. I have just deleted Feisty and converted the space using Gnome Partition Editor to ext3. I want to keep all my none system files on this partition.  tI I have tried moving folders over to this new partition but get the message that i do not have permission.
How can I change this so I can read and write to this new partition?
Thank you
Tao

---

### Post by Front187 on 2008-02-27
> **TaoBoogie said:**
> I had Gutsy and Feisty installed on the same drive. I have just deleted Feisty and converted the space using Gnome Partition Editor to ext3. I want to keep all my none system files on this partition.  tI I have tried moving folders over to this new partition but get the message that i do not have permission.
How can I change this so I can read and write to this new partition?
Thank you
Tao

GET A SECOND OPINION BEFORE RUNNING THIS COMMAND.  I AM NOT SURE IF IT WILL WORK PROPERLY, THIS IS JUST A PROPOSED SOLUTION.

chown yourusername:yourgroup /*


That should give you ownership of all files in /

Obviously change "/" to the filesystem where the files you want to move are stored.

Edit: chown not chgroup

---

### Post by taurus on 2008-02-27
You need to change the ownership of the mount point for that partition from root to your login name.  

_Assuming_ that it is mounted to /media/storage and your login name is **tao**.  You could try

```
sudo chown -R **tao**:**tao** /media/storage
ls -la /media
```

---

### Post by taurus on 2008-02-27
> **Front187 said:**
> GET A SECOND OPINION BEFORE RUNNING THIS COMMAND.  I AM NOT SURE IF IT WILL WORK PROPERLY, THIS IS JUST A PROPOSED SOLUTION.

chgroup yourusername:yourgroup /*


[B][COLOR="Blue"]That should give you ownership of all files in /
[/COLOR][/B]
Obviously change "/" to the filesystem where the files you want to move are stored.

That is a _real bad idea_, monkeying around with ownership of root filesystem.

---

### Post by Front187 on 2008-02-27
> **taurus said:**
> That is a _real bad idea_, monkeying around with ownership of root filesystem.

He's not going to change the owner ship of files in the root system though.

At the bottom I made sure to note that he must change "/" to the location of the non-system files that he wishes to move.

---

