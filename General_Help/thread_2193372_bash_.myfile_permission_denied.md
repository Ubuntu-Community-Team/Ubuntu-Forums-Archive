---
title: "bash: ./myfile: permission denied"
date: 2013-12-12
forum: General Help
---

### Post by maxmzkr on 2013-12-12
I've been trying to get this to work for quite a while now. I have a fstab file with the entry 
```
user@server.com: /home/max/WEBBACKUP fuse.sshfs IdentityFile="/home/max/.ssh/id_rsa",noauto,user,gid=100,umask=0022,exec 0 0
```
I've tried many others as well but when ever I run a file like this
```
./file
```
I get back an error
```
bash: ./myfile: permission denied 
```
I have looked at my mount output and I have this
```
user@server.com: on /home/max/WEBBACKUP type fuse.sshfs (rw,nosuid,nodev)

```
so it seems I have executing permisions, also for the file I have this as the permissions
```
-rwxr--r-- 1 max max 93 Nov 22 05:52 caen.sh

```
which also leads me to believe I have executing permissions, but I just can't get it to run.

Any help is much appreciated!

---

### Post by nerdtron on 2013-12-13
Try adding execute permissions to group or others. And see if you still have permission issues.
Also, maybe there are commands in the script that you are not allowed to execute.

Try "bash -x caen.sh" to see each line of the script executed. You'll also see output errors if the script encounters problems.

---

