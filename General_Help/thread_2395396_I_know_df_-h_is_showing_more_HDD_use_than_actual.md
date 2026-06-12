---
title: "I know df -h is showing more HDD use than actual"
date: 2018-07-01
forum: General Help
---

### Post by Robert_Boutin on 2018-07-01
Sorry if this has been asked but I can't find an answer.

I have Ubuntu 16.04 Desktop installed with VirtualBox on a 1TB HDD which is my OS disk.  My VMs reside on /dev/md126 which is a 2TB RAID1 array.

I want to migrate my OS to an SSD and as a first step, I'm trying to clean up my OS disk.  df -h says I've used 36G of my 1TB HDD, which I can't believe.  Besides 16.04 Desktop and Virtualbox, I installed another browser, K3b, and maybe one or two other programs.  My gut tells me I should have used perhaps 6G or 7G max.  I can't find a smoking gun that points to where the additional usage went to.  Any suggestions for where to check?  Next question, should I even care?  If I install an SSD and reinstall the OS and Vbox, will mdadm automatically find my RAID array?  Because that's really all I care about.  Thanks as always! 

```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.8G     0  7.8G   0% /dev
tmpfs                        1.6G  9.6M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  909G   36G  827G   5% /
tmpfs                        7.8G   17M  7.8G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/md126                   1.8T  695G  1.1T  40% /mnt/raid2tb
/dev/md127                   917G   72M  870G   1% /mnt/raid
tmpfs                        1.6G   68K  1.6G   1% /run/user/1000
tmpfs                        1.6G   24K  1.6G   1% /run/user/108
/dev/sdc1                    472M  111M  337M  25% /media/user1/5b9b7600-588f-4d8f-9417-dd01d35d4550
```

find / -printf '%s %p\n'| sort -nr | head -25 (I don't know how to exclude everything on /mnt/raid2tb)
```
140737477881856 /proc/kcore
273030447616 /mnt/raid2tb/03 - Share 192.168.1.112/Share 50.4.127.12 Clone-disk1_fixed.vhd
273030447616 /mnt/raid2tb/02 - Mail 192.168.1.111/Mail_copy_fixed.vhd
110468334080 /mnt/raid2tb/01 - WebHost 192.168.1.110/WebHost 172.2.236.19_copy_fixed.vhd
43965678080 /mnt/raid2tb/07 - Windows 7/Windows 7_fixed.vhd
21613380096 /mnt/raid2tb/05 - CRM 192.168.1.201/Tools2-disk1_fixed.vhd
8509112832 /mnt/raid2tb/04 - VPN 192.168.1.132/VPN 50.4.127.13 _ 192.168.1.132_fixed.vhd
5370806272 /mnt/raid2tb/08 - 16.04 Server 5GB/08 - 16.04 Server 5GB.vdi
5368709632 /mnt/raid2tb/08 - Ubuntu 16.04 Server 5GB/Ubuntu 16.04 Server 5GB.vhd
4341146112 /mnt/raid2tb/06 - Pi-Hole and DNS/Pi-Hole_copy.vhd
268435456 /sys/devices/pci0000:00/0000:00:02.0/resource2_wc
268435456 /sys/devices/pci0000:00/0000:00:02.0/resource2
197545018 /usr/lib/brave/resources/app.asar
110084136 /usr/lib/brave/brave
106146944 /usr/lib/firefox/libxul.so
75505664 /home/rboutin1/.config/brave/Cache/data_3
67108904 /dev/shm/pulse-shm-999081778
67108904 /dev/shm/pulse-shm-505907001
67108904 /dev/shm/pulse-shm-376892314
67108904 /dev/shm/pulse-shm-3379244915
67108904 /dev/shm/pulse-shm-3266130574
67108904 /dev/shm/pulse-shm-3162834614
67108904 /dev/shm/pulse-shm-2987038041
67108904 /dev/shm/pulse-shm-2750035406
67108904 /dev/shm/pulse-shm-2654463837
```

---

### Post by deadflowr on 2018-07-01
> Any suggestions for where to check?
Look in the program Disk Usage Analyzer for where the space is being used.

---

### Post by oldfred on 2018-07-01
From command line you can run this. It should total to same as df -h command.

       Shows just / 
sudo du -hx --max-depth=1 / 2> /dev/null

And then whichever folder is large, run du on it.

---

### Post by Robert_Boutin on 2018-07-01
I tried that but it doesn&#8217;t run as root. Is it possible to run the Disk Usage Analyzer as root?

---

### Post by #&amp;thj^% on 2018-07-01
Apologies for jumping in here, but to check in a more in depth look install "baobab"
```
sudo apt install baobab
```
EDIT: Warn using GUI's and using "sudo" not a good practice
and to run it with elevated privileges use:
```
sudo -H baobab
```
you can expand disk's and folders etc etc.

---

### Post by Robert_Boutin on 2018-07-01
> **oldfred said:**
> From command line you can run this. It should total to same as df -h command.

       Shows just / 
sudo du -hx --max-depth=1 / 2> /dev/null

And then whichever folder is large, run du on it.

Thanks, this is pretty much what I was expecting.  / shows 6.0 GB.  Am I wrong to assume / is the entire contents of the HDD?

sudo du -hx --max-depth=1 / 2> /dev/null

3.4G    /usr
4.0K    /opt
920M    /home
4.0K    /srv
172M    /var
16M    /sbin
887M    /lib
421M    /root
16K    /lost+found
8.0K    /snap
13M    /bin
88K    /tmp
4.0K    /mnt
4.0K    /lib64
8.0K    /media
140M    /boot
14M    /etc
4.0K    /cdrom
6.0G    /

---

### Post by oldfred on 2018-07-01
That should be all of / (root).
But do not know LVM.

It looks like you created a 36GB LVM volume for / using LVM. But then standard partition tools show the LVM which uses the entire LVM volume. And only the space actually used inside the LVM is what is used.

---

### Post by Robert_Boutin on 2018-07-05
That makes sense but actually it turns out the right question to answer was "Next question, should I even care?".  I bought an M.2 PCIe SSD and I found out I didn't need to migrate anything.  I just installed Ubuntu Desktop and Virtualbox, added my RAID arrays to mdadm.conf and fstab, and I was done.  Everything is working great.  Always learning...

---

