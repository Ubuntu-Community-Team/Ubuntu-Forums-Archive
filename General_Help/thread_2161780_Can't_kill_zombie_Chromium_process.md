---
title: "Can't kill zombie Chromium process?"
date: 2013-07-11
forum: General Help
---

### Post by JohnJD on 2013-07-11
When I'm browsing the internet, sometimes my browser will stop working.  I'll get a loading circle icon spinning, but nothing will every load.  When I check my system monitor, I notice I have these zombie processes that I can't kill.  I'll right click on them and click kill process, but nothing will happen.  I restart my computer and then everything is fine for a while.  It also seems to happen no matter what browser I use.  I have no idea how to go about fixing this or what could be causing it. [IMG]http://i.imgur.com/kZ9Me7n.jpg?1[/IMG]

---

### Post by newbie-user on 2013-07-12
Try killing it as superuser in terminal:
```
sudo kill -9 [pid]
```

---

### Post by coldcritter64 on 2013-07-12
If newbie-user's command doesn't kill the zombies directly, you should set the view in the system monitor to show dependencies from within the view menu then find which process is spawning them and kill it off (the parent process needs to be killed off to stop a zombie). A zombie, as far as I understand them, is only an entry in the process table, it uses no resources as such, usually it can't be killed off till the process that launched it is ended.

---

### Post by Impavidus on 2013-07-12
A zombie process has terminated (it may even have been killed), but it remains in the process list until its parent process performs the wait() call to read its exit status. Because the parent process has frozen, this doesn't happen. To get rid of the zombies you have to terminate the parent process. They will be adopted by init, which will perform the wait() call. You can find the process ID (PID) of the parent using the command```
cut -f4 -d' ' /proc/2114/stat
```where 2114 is the PID of your zombie. The system monitor can show you as well, it just reads /proc to get its information. In the system monitor (or in /proc) you can find out which program this is and you can terminate it using kill. My bet is it's your browser, that has forked in some way to show multiple tabs/run plugins/whatever.

---

### Post by slickymaster on 2013-07-12
> **Impavidus said:**
> A zombie process has terminated (it may even have been killed), but it remains in the process list until its parent process performs the wait() call to read its exit status. Because the parent process has frozen, this doesn't happen. To get rid of the zombies you have to terminate the parent process. They will be adopted by init, which will perform the wait() call. You can find the process ID (PID) of the parent using the command```
cut -f4 -d' ' /proc/2114/stat
```where 2114 is the PID of your zombie. The system monitor can show you as well, it just reads /proc to get its information. In the system monitor (or in /proc) you can find out which program this is and you can terminate it using kill. My bet is it's your browser, that has forked in some way to show multiple tabs/run plugins/whatever.

+1

Another way to find the process's Parent ID could be:```
cat /proc/2114/status | grep -i ppid
```If, for any reason, the output is something like```
PPid: 1
```you are out of luck. Process Id 1 belongs to init, without which your system cannot run.

---

### Post by vasa1 on 2013-07-12
> **JohnJD said:**
> When I'm browsing the internet, sometimes my browser will stop working.  I'll get a loading circle icon spinning, but nothing will every load.  When I check my system monitor, I notice I have these zombie processes that I can't kill.  I'll right click on them and click kill process, but nothing will happen.  I restart my computer and then everything is fine for a while.  It also seems to happen no matter what browser I use.  I have no idea how to go about fixing this or what could be causing it. ...
As others have explained, the zombies, *per se*, don't consume resources. But the fact that whichever browser you use stops working is a concern. Which are these browsers (in addition to Chromium)? Do you have a lot of extensions installed? Do you have problems when you run the browsers in "safe" mode, with all extensions disabled?

---

