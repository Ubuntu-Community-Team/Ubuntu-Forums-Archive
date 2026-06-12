---
title: "Black screen on reboot, drive full?"
date: 2017-02-13
forum: General Help
---

### Post by Jnetty99 on 2017-02-13
Ubuntu 14.04.3

Testing an analog TV tuner with VLC and left it running overnight. When I checked on it in the morning It had a warning on the screen. The warning was about less than 1gb of space left in the hard drive. 

I made the system reboot and since then it never comes back up to GUI desktop. 

I can connect using SSH. 

Any ideas on how to get it back up and running?

---

### Post by ajgreeny on 2017-02-13
Boot to a live system, or if you can, the command line of your installed system by using Ctrl+Alt+F1, and run command ```
df -h
```
That will show us exactly how much space there is on your disk(s).

It sounds as if running a recording overnight has produced an enormous file that has used all the free space available, so you may have to copy that huge file, if you really need it, to an external disk or similar, and then figure out where you go from there with your installed OS; perhaps delete the file from your main disk?

---

### Post by Jnetty99 on 2017-02-13
I can connect to ssh using putty and this is what i get when i run the command. I don't need the file. It was VLC running live analog TV as a test overnight. 

```
tsupport@Ubuntu14:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        70G   66G     0 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           396M  1.3M  394M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M  8.0K  100M   1% /run/user
overflow        1.0M  4.0K 1020K   1% /tmp
```

---

### Post by Jnetty99 on 2017-02-13
I have narrowed it down to the /var location having 50GB out of the 70GB drive.

---

### Post by howefield on 2017-02-13
> **Jnetty99 said:**
> I have narrowed it down to the /var location having 50GB out of the 70GB drive.

Keep digging, probably something spamming a log file, which you will be able to delete but not before investigating the detail.

---

### Post by Jnetty99 on 2017-02-13
/var/log/ 

kern.log.1 & syslog.1 both 26gb. 

I deleted them out and system back up and running. 

Thanks for suggestions.

---

