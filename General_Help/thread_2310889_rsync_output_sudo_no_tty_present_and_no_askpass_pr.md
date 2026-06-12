---
title: "rsync output sudo: no tty present and no askpass program specified"
date: 2016-01-22
forum: General Help
---

### Post by nzdreamer55 on 2016-01-22
Hello everyone,

I am new to linux and have managed to on my raspberry pi get rsync running to move files from a server I rent to my home computer.  Currently I am getting files from the server to my home computer however I am getting this error and wanted to trouble shoot it and maybe fix it.

I am using cron to run a script that contains several other scripts including the one that I use for rsync

```
*/15 * * * * flock -xn /tmp/example.lock -c 'sudo -u pi /usr/bin/scripts/Script1 >> /home/pi/log/cron.log 2>&1'

```

This Script1 calls another script which contains the rsync command

I have it as sudo because there are a couple of scripts that need sudo to run

Here is what I am using for a rsync command

```
rsync -vsHAXxr --progress --numeric-ids -e --delete-before --force -e --igonre-existing --temp-dir=/home/pi/Target/rsynctmp --partial-dir=/home/pi/Target/rsynctmp -e "ssh -T -c arcfour -o Compress
ion=no -x -p XXXXX" user@XX.XX.XX.XX:/source /target --exclude-from=/home/pi/log/ignorefile.log > /home/pi/log/rsync.log 2>&1

```

When I inspect the log I see

> sudo: no tty present and no askpass program specified

Any help is greatly appreciated.

---

