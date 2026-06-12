---
title: "Automatic backup to Ubuntu server"
date: 2008-06-11
forum: General Help
---

### Post by Super J on 2008-06-11
I have a file server set up running ubuntu server edition, with ssh and samba installed. My main pc is a windows xp box. I want to be able to automatically backup my music directory to the file server. Ideally I would like to run a script (from the windows or ubuntu side) that would take any changes made to the music directory on the windows box, and copy them to the server.

I think rsync would work but I don't know how to set it up on the windows side.

Any help would be greatly appreciated.

---

### Post by qpieus on 2008-06-11
You could use cygwin on the windows pc. [http://www.cygwin.com/](http://www.cygwin.com/)

Cygwin is pretty sool - it has lots of unix/linux apps that will run on windows. rsync is there too, so you could use rsync to sync between the windows pc and the server.

---

### Post by molotov00 on 2008-06-11
You'll find rsync-based backups useful. Rsync checks for updates and only backs-up the modified parts of files. If you want a complete backup then a simple "cp -R file destination" will work (R is for copying all files in directory)

[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979) is probably overkill but is worth a read to get you familiar.

If I were you, because this is a simple backup request, I'd install samba client so that you can view a shared folder on the Windows machine. Then, I'd 'mount' (it's a command) the shared folder. Then, you can copy the files every night using rsync. In /etc/cron.d/ there are scripts that run daily. /etc/crontab allows you to specify times and scripts that should be executed.

An alternative would be to share a folder on the linux machine and set a scheduled task on the Windows box. Microsoft has Synctoy, an app that is pretty good at copying syncing shared files. If you go this route I'll look up the command to automate the sync. It's on the web but took a while for me a find a few years ago when I did a backup in this fashion.

---

### Post by p_quarles on 2008-06-11
> **molotov00 said:**
>  Rsync checks for updates and only backs-up the modified parts of files. If you want a complete backup then a simple "cp -R file destination" will work (R is for copying all files in directory)
Of course, rsync is also a "complete" backup. I know you realize that, but the way you worded that might have confused someone new these tools.

> If I were you, because this is a simple backup request, I'd install samba client so that you can view a shared folder on the Windows machine. Then, I'd 'mount' (it's a command) the shared folder. Then, you can copy the files every night using rsync. In /etc/cron.d/ there are scripts that run daily. /etc/crontab allows you to specify times and scripts that should be executed.
+1. This gets rid of the need to install any extra software, as these tools are built into the respective computers. Running rsync from the server (but using the Windows client as the source directory, and the backup file-server as the target directory) seems like the simplest way to set this up.

---

### Post by Super J on 2008-06-11
Thanks guys. I'll give cygwin a shot.

---

### Post by molotov00 on 2008-06-11
> **Super J said:**
> Thanks guys. I'll give cygwin a shot.

Please don't.

Edit: let me clarify, cygwin is a wierd way of doing it. If you want the sync initiated by the windows box, you can use windows apps. This is identical to my 'alternative' method, where samba server must be installed on the server and a folder shared. Initiating the backup from the server makes more sense to me.

Thanks p for the note about 'complete'

---

### Post by Super J on 2008-06-12
Ok, now I'm getting confused. I have rsync installed on the server. I have the destination folder on the server mapped as a network drive in Windows. Its located at /multimedia on the server. I want to copy from the c:\music folder.

If I initiate rsync from the server I think the command should look like this:

```
rsync **192.168.1.100:c:\music** /multimedia
```

The bolded part is where I'm confused. I don't know how to tell it to find the c:\music folder on my windows box.

---

### Post by p_quarles on 2008-06-12
You would need to find out the name of the Windows drive as it is seen by the Samba client. If that is "c," then so be it, but if I recall correctly Samba gives the shared folder a new name when it mounts it onto another computer.

---

### Post by Super J on 2008-06-12
Alright, I can mount the windows shared folder from the server with 
```
mount -t smbfs //192.168.1.100/music /multimedia
```

I'm getting closer I just need to figure out how to get rsync to see the files. When I run this:
```
rsync //192.168.1.100/music /multimedia
```
I get the following error:
```
rsync: link_stat "//192.168.1.100/music/." failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(791)

```

I guess I have some reading to do...

---

### Post by p_quarles on 2008-06-12
If you mounted the shared folder as /multimedia on the server, then /multimedia will be the source directory (as rsync sees things).

---

### Post by Super J on 2008-06-12
That worked. I mounted my Windows music folder in /mnt/smb and rsynced from there to the /multimedia folder. 

Thanks for the help guys.

---

### Post by molotov00 on 2008-06-12
You're welcome. I'm glad you went with this solution rather than cygwin.

The reason you were getting confused is because rsync CAN connect to the client to get the files. Now since you've mounted it, you don't need that functionality. But let's say you had a linux client, rsync would (behind the scenes) login via ssh and browse to the folder you want to copy, then copy the files over. It can also do the same via FTP, so, it is a little more comprehensive than you need.

---

