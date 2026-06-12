---
title: "Copy files from a directory from one system to another system"
date: 2017-08-23
forum: General Help
---

### Post by shajiuddinsegmail on 2017-08-23
Hi,

I have below 2 systems having IPs on same network

A: 192.168.0.20
B: 192.168.0.21

From A system I need to copy files from a directory/folder to B system

Also I need to schedule it using crontab so either all files should copy or only latest files should copy

Any help will be highly appreciable


Regards

---

### Post by aromo2 on 2017-08-23
from A, you'd run:
```
scp -p /path/to/files/* user@192.168.0.21:/destination/path/
```

This will prompt for user's password. To prevent that, you need to create a SSH-key pair for user on system B (ssh-keygen) and copy the public key to the user who's running scp on system A (ssh-copy-id).

Once you are able to run it from command line without prompting for password, you want to add an entry in system A user's crontab (crontab -e).

Give it a try and remember that man and Google are your friends.

---

### Post by Habitual on 2017-08-23
```
ssh-keygen -f /path/to/file_rsa -t rsa -N '' -b **4096** -q
``` which was pieced together using [https://www.ssh.com/ssh/keygen/](https://www.ssh.com/ssh/keygen/)

---

### Post by deadflowr on 2017-08-23
You'd also need to install the ssh server package.
(On at least one of the machines.)
```
sudo apt install openssh-server
```

---

### Post by untrustytahr on 2017-08-23
'scp' would certainly work, but since you are going to run it repetitively as a cron job you may want to use 'rsync' instead.  Rsync will only transfer the delta in files as opposed to transferring everything each time.  Depends on how much data you are transferring I suppose.

---

### Post by HermanAB on 2017-08-24
Hmm, there are umpteen ways to do it: SSH, FTP and Rsync are obvious, but netcat is much more fun!

On the destination machine:
# nc -l 1234 > filename

On the source machine:
# nc destinationipaddress -p 1234 < filename

Instead of doing one file at a time, you can pipe tar and nc together to compress a directory and uncompress it on the other side.

---

### Post by Habitual on 2017-08-24
[Simple, Secure Backups for Linux with rsync]("http://rsync.net/resources/howto/rsync.html")

---

