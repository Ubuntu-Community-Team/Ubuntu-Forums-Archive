---
title: "Disk space low on /"
date: 2016-12-25
forum: General Help
---

### Post by brendonwp on 2016-12-25
[IMG]https://www.dropbox.com/s/indx3wxg2psdw8s/Screenshot%20from%202016-12-25%2018%3A14%3A21.png?dl=0[/IMG]
My disk space is suddenly low on /.  I've purged old headers with apt-get autoremove, cleared out the trash and rebooted, but still have only 240MB of 6GB.  Have separate partitions for /boot, /tmp, /var and /usr.  User file systems are /home, /data, /fastdata.  Have added screenshot of file systems.

Read that sudo du -hs /* is useful for diagnosing possible issues.  Please have a look below and suggest where to look next.  Thanks!
  
Output is: 
12M    /bin
617M    /boot
4,0K    /cdrom
96G    /data
4,0K    /dev
16M    /etc
60G    /fastdata
201G    /home
0    /initrd.img
0    /initrd.img.old
4,0K    /install.sh
4,1G    /lib
3,5M    /lib32
4,0K    /lib64
16K    /lost+found
12K    /media
4,0K    /mnt
771M    /opt
du: cannot access &#8216;/proc/5403/task/5403/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/5403/task/5403/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/5403/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/5403/fdinfo/4&#8217;: No such file or directory
0    /proc
740K    /root
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
1,6M    /run
12M    /sbin
4,0K    /srv
0    /sys
90M    /tmp
4,0K    /uninstall.sh
9,6G    /usr
1,5G    /var
0    /vmlinuz
0    /vmlinuz.old

---

### Post by oldos2er on 2016-12-25
Moved to General Help.

What is the output of ```
df -h
```?

---

### Post by brendonwp on 2016-12-25
Output is:

```
Filesystem      Size  Used Avail Use% Mounted on
udev            2,9G  4,0K  2,9G   1% /dev
tmpfs           586M  1,4M  585M   1% /run
/dev/sda6       5,4G  4,9G  229M  96% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none            2,9G  4,2M  2,9G   1% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sda10       72G   60G  8,5G  88% /fastdata
/dev/sda7       1,9G  3,0M  1,8G   1% /tmp
/dev/sda8        15G  9,7G  4,2G  70% /usr
/dev/sda9       5,4G  1,5G  3,7G  29% /var
/dev/sda5       945M  618M  263M  71% /boot
/dev/sdb6       199G   96G   93G  51% /data
/dev/sdb5       235G  201G   23G  91% /home
```

---

### Post by deadflowr on 2016-12-25
It's your /lib directory.
 look in there.
probably kernel modules in /lib/modules.
perhaps look at kernels that are still installed
```
dpkg -l | grep linux-image | awk '{print $1,$2}'
```
lib/modules files are part of the linux-image package, they install a new per kernel upgrade.

---

### Post by brendonwp on 2016-12-26
Thanks deadflowr, I see a whole bunch when I use your command under terminal.  At the moment I'm using synaptic to get rid of the 3.19 series kernels.  Why does "apt-get autoremove" not get rid of them?  Is there a better way than using synaptic?

```
dpkg -l | grep linux-image | awk '{print $1,$2}'rc linux-image-3.19.0-25-generic
ii linux-image-3.19.0-32-generic
ii linux-image-3.19.0-33-generic
ii linux-image-3.19.0-37-generic
rc linux-image-3.19.0-39-generic
ii linux-image-3.19.0-41-generic
ii linux-image-3.19.0-42-generic
ii linux-image-3.19.0-43-generic
ii linux-image-3.19.0-47-generic
ii linux-image-3.19.0-49-generic
ii linux-image-3.19.0-51-generic
rc linux-image-3.19.0-56-generic
ii linux-image-3.19.0-58-generic
rc linux-image-3.19.0-59-generic
ii linux-image-3.19.0-61-generic
ii linux-image-3.19.0-65-generic
ii linux-image-3.19.0-66-generic
ii linux-image-3.19.0-69-generic
rc linux-image-3.19.0-73-generic
ii linux-image-3.19.0-74-generic
rc linux-image-3.19.0-77-generic
ii linux-image-3.19.0-78-generic
rc linux-image-4.4.0-34-generic
ii linux-image-4.4.0-38-generic
rc linux-image-4.4.0-45-generic
ii linux-image-4.4.0-47-generic
ii linux-image-4.4.0-53-generic
ii linux-image-4.4.0-57-generic
rc linux-image-extra-3.19.0-25-generic
ii linux-image-extra-3.19.0-32-generic
ii linux-image-extra-3.19.0-33-generic
ii linux-image-extra-3.19.0-37-generic
rc linux-image-extra-3.19.0-39-generic
ii linux-image-extra-3.19.0-41-generic
ii linux-image-extra-3.19.0-42-generic
ii linux-image-extra-3.19.0-43-generic
ii linux-image-extra-3.19.0-47-generic
ii linux-image-extra-3.19.0-49-generic
ii linux-image-extra-3.19.0-51-generic
rc linux-image-extra-3.19.0-56-generic
ii linux-image-extra-3.19.0-58-generic
rc linux-image-extra-3.19.0-59-generic
ii linux-image-extra-3.19.0-61-generic
ii linux-image-extra-3.19.0-65-generic
ii linux-image-extra-3.19.0-66-generic
ii linux-image-extra-3.19.0-69-generic
rc linux-image-extra-3.19.0-73-generic
ii linux-image-extra-3.19.0-74-generic
rc linux-image-extra-3.19.0-77-generic
ii linux-image-extra-3.19.0-78-generic
rc linux-image-extra-4.4.0-34-generic
ii linux-image-extra-4.4.0-38-generic
rc linux-image-extra-4.4.0-45-generic
ii linux-image-extra-4.4.0-47-generic
ii linux-image-extra-4.4.0-53-generic
ii linux-image-extra-4.4.0-57-generic
ii linux-image-generic-lts-vivid
ii linux-image-generic-lts-xenial
```

---

### Post by eezacque on 2016-12-26
> **brendonwp said:**
> Thanks deadflowr, I see a whole bunch when I use your command under terminal.  At the moment I'm using synaptic to get rid of the 3.19 series kernels.  Why does "apt-get autoremove" not get rid of them?  Is there a better way than using synaptic?


Your 'apt-get autoremove' removes packages that are no longer needed, which does not cover old kernels.
Try [http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

---

### Post by ian-weisser on 2016-12-26
There may be several reasons why 'autoremove' fails.
It could be a dependency, apt-marking, apt-hold, and several more complex causes.

Autoremove is designed to do something potentially very dangerous (uninstall important system components without asking you), so it's also designed to be fragile. Better to fail safe.

---

### Post by Keith_Helms on 2016-12-27
I use the purge-old-kernels script which by default keeps the 3 latest versions.  How to get it is described here:
[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

---

