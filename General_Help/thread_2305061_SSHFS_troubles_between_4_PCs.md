---
title: "SSHFS troubles between 4 PCs"
date: 2015-12-02
forum: General Help
---

### Post by Berduchwal on 2015-12-02
Setup is as follows 4 PC on local network.

1 acting as a server with HDD containing all files other need to use. 3 connecting to it hopefully using SSHFS.

I reached the point that I can do the following:
```
X@Glowing-PC:/$ ssh -l hddserver 192.168.0.5
Enter passphrase for key '/home/X/.ssh/id_rsa': 
Last login: Wed Dec  2 14:10:58 2015 from 192.168.0.6
hddserver@HDD-server:~$ 

```

On server /etc/ssh/sshd_config:
```
PubkeyAuthentication yes
UsePAM no
PasswordAuthentication no

```

All PC are running 14.04 desktop fully updated.

Then:

```
X@Glowing-PC:/$ sudo sshfs hddserver@192.168.0.5:/ /media/Placement -o IdentityFile=/home/X/.ssh/id_rsa -o idmap=user
[sudo] password for X: 
Enter passphrase for key '/home/X/.ssh/id_rsa': 
X@Glowing-PC:/media$ ls -l
ls: cannot access Placement: Permission denied
total 12
d?????????? ? ?      ?       ?            ? Placement
drwxr-xr-x  2 X root 4096 Dec  2 14:14 UnCommon

```

I do not know why is this happening and I can find any info about this.
I would also like to set it that ```
Enter passphrase for key '/home/X/.ssh/id_rsa': 
``` is not required when logged in.

```
X@Glowing-PC:/media$ sudo umount /media/Placement 
X@Glowing-PC:/media$ ls -l
total 16
drwxr-xr-x  2 X root 4096 Dec  2 14:14 Placement

```

I am not sure what else can I try.

---

### Post by Berduchwal on 2015-12-03
I tried to change permissions to:
```
drwxrwxr-x 2 X X 4096 Nov 28 14:01 Placement

```

I tried to mount to a new directory in home folder but results were the same.


I remove sudo and it worked.
```
sshfs hddserver@192.168.0.5:/ /media/Placement -o IdentityFile=/home/X/.ssh/id_rsa -o idmap=user
```

Second issues was solved with:
```
ssh-add /home/X/.ssh/id_rsa
```

---

