---
title: "Sbackup finished - how to know?"
date: 2007-08-08
forum: General Help
---

### Post by candtalan on 2007-08-08
I am using sbackup for a 40 GB directory and this may take a few hours maybe. However, I have no idea how I can tell when it is finished. And I started it going a few hours ago. I am happy to use CL.

When beginning it gave a message
A backup run is initiated in the background. The process id is: 6582.

I use the terminal command 
top
but I do not see 6582 anywhere.
I look in the destination drive (a USB drive) and I see the target directory as locked.

I notice that the destination drive is warm, suggesting it is still busy.
There is only occasional drive activity in the source drive, this could be some other process.

I look in System Monitor and I do not see sbackup. However, CPU looks very busy.

Any suggestions about how to find out more positively if sbackup is really still active please?

---

### Post by apetresc on 2007-08-08
Does ```
ps aux | grep -v grep | grep 6582
``` return anything?

---

### Post by candtalan on 2007-08-08
yes:

user@my-pc:~$ ps aux | grep -v grep | grep 6582
root      6582  1.3  1.8  25300 19180 ?        SN   14:15   4:17 /usr/bin/python                                /usr/sbin/sbackupd

What does this mean?

---

### Post by apetresc on 2007-08-08
> **candtalan said:**
> yes:

user@my-pc:~$ ps aux | grep -v grep | grep 6582
root      6582  1.3  1.8  25300 19180 ?        SN   14:15   4:17 /usr/bin/python                                /usr/sbin/sbackupd

What does this mean?

This means that sbackup is still running :) "ps" is a utility that lists all the processes that are currently running. "grep" simply took that large list and filtered out the one with process id 6582. It is indeed "/usr/sbin/sbackupd", so everything is working according to plan.

When sbackup is done, that command will stop returning anything. That's how you'll know!

---

### Post by candtalan on 2007-08-08
> **AdrianP said:**
> This means that sbackup is still running :) "ps" is a utility that lists all the processes that are currently running. "grep" simply took that large list and filtered out the one with process id 6582. It is indeed "/usr/sbin/sbackupd", so everything is working according to plan.

When sbackup is done, that command will stop returning anything. That's how you'll know!

Thanks!
:-)

---

### Post by psusi on 2007-08-08
I usually use tar to do backups automatically in a cron job set to run at midnight.  Whenever the job is finished, cron sends its output to me via email so I know it finished correctly.  Alternatively you can use the batch command to start the job in the background and when it finishes, it emails you the output.

---

### Post by Cariboo1938 on 2007-11-24
> **AdrianP said:**
> This means that sbackup is still running :) "ps" is a utility that lists all the processes that are currently running. "grep" simply took that large list and filtered out the one with process id 6582. It is indeed "/usr/sbin/sbackupd", so everything is working according to plan.
[COLOR="Red"]*When sbackup is done, that command will stop returning **anything**. That's how you'll know!*[/COLOR]
I still get this return after about 2 hours:
> root@karibu-desktop:/# ps aux | grep -v grep | grep 22904
root     22904  0.0  0.0      0     0 ?        ZN   08:06   0:00 [sbackupd] <defunct>
root@karibu-desktop:/#
Is SBackup still running after such a "long" time? 
Is there another way to know SBackup has finished?:confused:
[COLOR="DarkOrchid"]
EDIT: Case closed for me.
I got a private message from AdrianP---The process is running as long as command 'ps aux...' gives any output.
Why it is still running is not clear!
you can terminate the process, if you like, with command 'kill <process ID>'[/COLOR]

---

### Post by psusi on 2007-11-26
Hrm... looks like something is wrong with sbackup.  You normally don't see zombie processes like that because they should be reaped by their parent quickly.  That process has finished but for some reason, it's parent isn't reaping it.

---

