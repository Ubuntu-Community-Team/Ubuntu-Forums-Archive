---
title: "Tar compression freezes Ubuntu 12.04"
date: 2012-12-26
forum: General Help
---

### Post by Clucky on 2012-12-26
For some reason, when I am running a script to backup some of my Minecraft server files using tar, it causes my desktop enviornment, my Minecraft server, and even my MySQL servers to all lock up for approx 5 to 10 seconds. Could someone please help me to either lessen or preferrably prevent this from happening? Thanks.

Here is the script I am using for compression:
```

echo "-------------- `date '+%B-%d-%Y-%H:%M'` --------------" >> /home/clucky/MinecraftServers/backup.log
echo "[`date '+%B-%d-%Y-%H:%M'`] Starting Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
tar -zcpf /home/clucky/MinecraftServers/.backups/Backup-`date '+%d-%B-%Y-%H:%M'`.tar.gz \
    --directory /home/clucky/MinecraftServers/ --exclude=Mortuus/plugins/dynmap/web --exclude=Mortuus/plugins/AutoSaveWorld/backups --exclude=backup.log --exclude=Mortuus/server.log --exclude=Frisnuk/plugins/dynmap/web --exclude=Frisnuk/plugins/AutoSaveWorld/backups --exclude=Frisnuk/server.log --exclude=Tekkit/plugins/AutoSaveWorld/backups --exclude=Tekkit/server.log --exclude=Tekkit2 --exclude=.backups --exclude=SkyBlokkit --exclude=backups.log --exclude=backupscript.sh --exclude dailybackup.sh .;
echo "[`date '+%B-%d-%Y-%H:%M'`] Finishing Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
#Purge files 3 days old
echo "[`date '+%B-%d-%Y-%H:%M'`] Purging Old Backups" >> /home/clucky/MinecraftServers/backup.log
find /home/clucky/MinecraftServers/.backups* -mmin +4320 -exec rm {} \;
echo "[`date '+%B-%d-%Y-%H:%M'`] Purging Complete" >> /home/clucky/MinecraftServers/backup.log
echo "\n" >> /home/clucky/MinecraftServers/backup.log

```**Computer specs:**
16gb DDR-3 1333mhz RAM
3.6ghz Quadcore Processor, AMD Phenom II
1.5TB 7200RPM HDD

---

### Post by Kirk Schnable on 2012-12-26
Depends what we are maxing out to cause the freezing.

It might be a good idea to use tools like **top** and **iotop -o** to look at CPU And disk utilization while the backup is running. 

If CPU usage is a problem, I have seen **cpulimit** help out enormously in other use cases. 

[http://www.ubuntugeek.com/cpulimit-limit-the-cpu-usage-of-a-process.html](http://www.ubuntugeek.com/cpulimit-limit-the-cpu-usage-of-a-process.html)

---

### Post by rnerwein on 2012-12-26
> **Clucky said:**
> For some reason, when I am running a script to backup some of my Minecraft server files using tar, it causes my desktop enviornment, my Minecraft server, and even my MySQL servers to all lock up for approx 5 to 10 seconds. Could someone please help me to either lessen or preferrably prevent this from happening? Thanks.

Here is the script I am using for compression:
```

echo "-------------- `date '+%B-%d-%Y-%H:%M'` --------------" >> /home/clucky/MinecraftServers/backup.log
echo "[`date '+%B-%d-%Y-%H:%M'`] Starting Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
tar -zcpf /home/clucky/MinecraftServers/.backups/Backup-`date '+%d-%B-%Y-%H:%M'`.tar.gz \
    --directory /home/clucky/MinecraftServers/ --exclude=Mortuus/plugins/dynmap/web --exclude=Mortuus/plugins/AutoSaveWorld/backups --exclude=backup.log --exclude=Mortuus/server.log --exclude=Frisnuk/plugins/dynmap/web --exclude=Frisnuk/plugins/AutoSaveWorld/backups --exclude=Frisnuk/server.log --exclude=Tekkit/plugins/AutoSaveWorld/backups --exclude=Tekkit/server.log --exclude=Tekkit2 --exclude=.backups --exclude=SkyBlokkit --exclude=backups.log --exclude=backupscript.sh --exclude dailybackup.sh .;
echo "[`date '+%B-%d-%Y-%H:%M'`] Finishing Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
#Purge files 3 days old
echo "[`date '+%B-%d-%Y-%H:%M'`] Purging Old Backups" >> /home/clucky/MinecraftServers/backup.log
find /home/clucky/MinecraftServers/.backups* -mmin +4320 -exec rm {} \;
echo "[`date '+%B-%d-%Y-%H:%M'`] Purging Complete" >> /home/clucky/MinecraftServers/backup.log
echo "\n" >> /home/clucky/MinecraftServers/backup.log

```**Computer specs:**
16gb DDR-3 1333mhz RAM
3.6ghz Quadcore Processor, AMD Phenom II
1.5TB 7200RPM HDD
hi
i think you toch a huge amount of data. start top in a terminal and watch the values of memory, swap, buffers and cache.
i guess in the lock-up time there is a lot of busy in this parts (system is reorginzeing)

cheers

---

### Post by Clucky on 2012-12-26
I did notice that Gzip was running anywhere from 60 to 80 cpu usage. And that along side firefox which uses 80% (cuz i have 320 internet tabs open) and my two minecraft servers, which use about 40% each, nearly maxes out my CPU. So is this why I am locking up? How can I lower the cpu usage of the task? I already tried lowering the priority of the tast, but it actually made the issue worse for some reason. Thanks.

---

### Post by Kirk Schnable on 2012-12-26
> **Clucky said:**
> I did notice that Gzip was running anywhere from 60 to 80 cpu usage. And that along side firefox which uses 80% (cuz i have 320 internet tabs open) and my two minecraft servers, which use about 40% each, nearly maxes out my CPU. So is this why I am locking up? How can I lower the cpu usage of the task? I already tried lowering the priority of the tast, but it actually made the issue worse for some reason. Thanks.

I think it's entirely possible that the CPU usage is the problem.

Did you take a look at the cpulimit program I posted earlier?  It should be able to do what you're asking for.

---

### Post by Clucky on 2012-12-26
> **Kirk Schnable said:**
> I think it's entirely possible that the CPU usage is the problem.

Did you take a look at the cpulimit program I posted earlier?  It should be able to do what you're asking for.

How exactly would I enter the cpulimit into the code that I posted above?

---

### Post by pardalet on 2012-12-26
Haven't tried it, but maybe you'd be OK by modifying the niceness of the tar command:

```
echo "-------------- `date '+%B-%d-%Y-%H:%M'` --------------" >> /home/clucky/MinecraftServers/backup.log
echo "[`date '+%B-%d-%Y-%H:%M'`] Starting Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
**nice 10 **tar -zcpf /home/clucky/MinecraftServers/.backups/Backup-`date '+%d-%B-%Y-%H:%M'`.tar.gz \
    --directory /home/clucky/MinecraftServers/ --exclude=Mortuus/plugins/dynmap/web --exclude=Mortuus/plugins/AutoSaveWorld/backups --exclude=backup.log --exclude=Mortuus/server.log --exclude=Frisnuk/plugins/dynmap/web --exclude=Frisnuk/plugins/AutoSaveWorld/backups --exclude=Frisnuk/server.log --exclude=Tekkit/plugins/AutoSaveWorld/backups --exclude=Tekkit/server.log --exclude=Tekkit2 --exclude=.backups --exclude=SkyBlokkit --exclude=backups.log --exclude=backupscript.sh --exclude dailybackup.sh .;

[...]

```


You could try tweaking the nice parameter (from 1 to 19) to get the optimum CPU performance without compromising execution time.

---

### Post by Kirk Schnable on 2012-12-26
> **pardalet said:**
> Haven't tried it, but maybe you'd be OK by modifying the niceness of the tar command:

```
echo "-------------- `date '+%B-%d-%Y-%H:%M'` --------------" >> /home/clucky/MinecraftServers/backup.log
echo "[`date '+%B-%d-%Y-%H:%M'`] Starting Minecraft Backup" >> /home/clucky/MinecraftServers/backup.log
**nice 10 **tar -zcpf /home/clucky/MinecraftServers/.backups/Backup-`date '+%d-%B-%Y-%H:%M'`.tar.gz \
    --directory /home/clucky/MinecraftServers/ --exclude=Mortuus/plugins/dynmap/web --exclude=Mortuus/plugins/AutoSaveWorld/backups --exclude=backup.log --exclude=Mortuus/server.log --exclude=Frisnuk/plugins/dynmap/web --exclude=Frisnuk/plugins/AutoSaveWorld/backups --exclude=Frisnuk/server.log --exclude=Tekkit/plugins/AutoSaveWorld/backups --exclude=Tekkit/server.log --exclude=Tekkit2 --exclude=.backups --exclude=SkyBlokkit --exclude=backups.log --exclude=backupscript.sh --exclude dailybackup.sh .;

[...]

```


You could try tweaking the nice parameter (from 1 to 19) to get the optimum CPU performance without compromising execution time.

I never noticed that parameter... That's worth a try, might work better than my cpulimit suggestion.

---

### Post by rnerwein on 2012-12-27
> **Clucky said:**
> I did notice that Gzip was running anywhere from 60 to 80 cpu usage. And that along side firefox which uses 80% (cuz i have 320 internet tabs open) and my two minecraft servers, which use about 40% each, nearly maxes out my CPU. So is this why I am locking up? How can I lower the cpu usage of the task? I already tried lowering the priority of the tast, but it actually made the issue worse for some reason. Thanks.
hi
again: start top and watch the values. my stomage told me there will be a high value in
wa (line two - field 5).
the cpu values looks ok. even a cpu-usage of 100% must not  be a reasom for a slow system.
you can try in a shell:  while : ; do :  ;done (open a second terminal before that you can kill
this procedure if desired - normaly CTRL c ).
as you see one cpu will go to 100% user-mode  (if you get 4 cores 25% is shown) and the system performs good.
you can start this procedure once for each cpu you get (we have a scheduler on the system !)
at last i think it is the io-wait
io is mostely the bottleneck - e.g. create a 2GB file - thats fast - oh no it's the cache.
type "sync" (this will flush the caches) and trink a cup of coffee till the command prompt comes back.
that is now all the processes with io have to wait !
cheers ;-)

cheers

---

### Post by Clucky on 2012-12-27
The strange thing that keeps happening is, when my comptuer does freeze, the cpu drops below the point where it would normally be if the Gzip task wasn't running. Is this normal? Here is an example, my cpu generally runs at 40-80% of maximum cpu (4 cores, 25% each) according to graph included in the image below. Below I am posting two images, one is a monitor of the freeze, the other is a monitor of my computer normally. Also, this is using **nice 10**, so it does not seem to help much, unless I need to change it to 1 or 19... Idk which uses less cpu and which uses more.

**Freeze**
[IMG]http://worldofclucky.net/errors/ServerLag/freeze.png[/IMG]

**Normal**
[IMG]http://worldofclucky.net/errors/ServerLag/normal.png[/IMG]

---

### Post by pardalet on 2012-12-27
When you launch any process, by default it gets a niceness of 0. If you want to give it more priority, you'd go with a negative parameter: the lower, the more priority. So, if you want to minimize the CPU usage you must launch the tar command with ***nice 19***.

However I don't think this will help much, seeing the CPU usage captures you have uploaded... :(

---

### Post by rnerwein on 2012-12-27
> **Clucky said:**
> The strange thing that keeps happening is, when my comptuer does freeze, the cpu drops below the point where it would normally be if the Gzip task wasn't running. Is this normal? Here is an example, my cpu generally runs at 40-80% of maximum cpu (4 cores, 25% each) according to graph included in the image below. Below I am posting two images, one is a monitor of the freeze, the other is a monitor of my computer normally. Also, this is using **nice 10**, so it does not seem to help much, unless I need to change it to 1 or 19... Idk which uses less cpu and which uses more.

**Freeze**
[IMG]http://worldofclucky.net/errors/ServerLag/freeze.png[/IMG]

**Normal**
[IMG]http://worldofclucky.net/errors/ServerLag/normal.png[/IMG]
hi
you haven't read my post before yours. 
i told you that i think it's io-wait and network is io too.
start "top" in a terminal and watch the value of wa (wait io).
best is post a screenshot of top when the lack hapens. be sure priority woudn't help you.
cheers

---

### Post by Clucky on 2012-12-27
I went ahead and closed Firefox, and it seems to have fixed most of the computer freezes during backups, however, is there any long-term solution other than having to restart firefox once every 4 days? Remember, I do have nearly 400 internet tabs open at once... I would provide a top, but my screenshots aren't fast enough, but the CPU for gzip is around 85-100%, gnome-system-mo is around 27%, tar is around 22%, Xorg is around 16%, Java is around 15%, other java is around 7%.

---

### Post by rnerwein on 2012-12-28
> **Clucky said:**
> I went ahead and closed Firefox, and it seems to have fixed most of the computer freezes during backups, however, is there any long-term solution other than having to restart firefox once every 4 days? Remember, I do have nearly 400 internet tabs open at once... I would provide a top, but my screenshots aren't fast enough, but the CPU for gzip is around 85-100%, gnome-system-mo is around 27%, tar is around 22%, Xorg is around 16%, Java is around 15%, other java is around 7%.

hi
see the attachment
cheers

---

### Post by Clucky on 2012-12-28
I read your freeze.txt file, and it kinda made sense to me. It seems that I still have at least 150% of my CPU remaining for extra tasks though while the backup is running, and it still lags though. I keep Firefox windows open because I get lazy or forget to close them or go back to them at a later date for references, however, I often kill the firefox task and reopen the pages, that way the pages content unloads until I visit the tab once again (saves CPU and RAM). But even with firefox running at 4-20% CPU (of 400% CPU) and only 638MB RAM, my computer still lags during backups. You mentioned something about RAID, what exactly is this, how much does it cost, and would it help me. I was considering getting a SSD to use for my servers (MySQL, HTTP, Minecraft), do you think this would help, or would the lag caused by backups still occur?

---

