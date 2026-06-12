---
title: "amd-config.log taking up all my disk space"
date: 2014-02-05
forum: General Help
---

### Post by yvin on 2014-02-05
I'm running Xubuntu through Wubi on my laptop, and I recently encountered the problem of suddenly running out of disk space.
Going through the recommended steps, I discovered a 14GB log file being the reason (*/var/log/amd-config.log*), and deleted the file. This was however only a temporary solution, as the log file reappears and continues to grow at an incredible speed.

Inspecting the file, it seems to only be filled with uncountable lines of a single *y*.

I don't know which process is logging to this file, or what could be wrong, but the only amd-related process running seems to be */usr/bin/amd-xconfig* . It seems likely this might be the culprit, but I have no idea how to find out what's wrong.


Does anyone know what the problem might be, or how I can find out more? Any help is appreciated!

---

### Post by ravi4 on 2014-02-05
I am having the same problem as well. Seems like a recent update is causing this problem. Any suggestions?

---

### Post by will_b on 2014-02-06
I have the same issue: /var/log/upstart/amd-config.log grows at an alarming rate, and is just a file full of a single character 'y' on each new line...
It started last evening after I updated, as well as re-installed mysql. Running 12.04 and Windows 8.1 on separate partitions.

---

### Post by jeanjd63 on 2014-02-06
> **will_b said:**
> I have the same issue: /var/log/upstart/amd-config.log grows at an alarming rate, and is just a file full of a single character 'y' on each new line...
It started last evening after I updated, as well as re-installed mysql. Running 12.04 and Windows 8.1 on separate partitions.


Hello 
What contain directory  logrotate.d :
**ls -l  /etc/logrotate.d**

I have inside a file named upstart :
and :
```

jean@Chez-Moi:~$** ls -l  /etc/logrotate.d/upstart **
 -rw-r--r-- 1 root root 122 avril 26  2012 /etc/logrotate.d/upstart


jean@Chez-Moi:~$ **cat  /etc/logrotate.d/upstart **
/var/log/upstart/*.log {
        daily
        missingok
        rotate 7
        compress
        notifempty
    nocreate
}
```

an the directory /var/log/upstart contains file compressed named from 1.gz to 7.gz

---

### Post by yvin on 2014-02-06
The problem seems to have disappeared on its own now, though I have no idea why. I have not made any changes to my system, it has not even been active since yesterday.
Rebooting the system did not help earlier, so I doubt that's what did the trick now. Will update if the problem returns.

---

### Post by sandyd on 2014-02-06
being fixed [https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1277058](https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1277058)

---

### Post by ravi4 on 2014-02-08
> **sandyd said:**
> being fixed [https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1277058](https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1277058)

Thanks! Installing this package solved the problem for me: 
sudo apt-get install fglrx-pxpress

---

