---
title: "Applications won't start"
date: 2006-12-31
forum: General Help
---

### Post by joth on 2006-12-31
Hey everyone :)

Just installed the Edgy Eft version of Ubuntu; I was using Kubuntu before, but accidentally wiped my hard drive (long story), so thought I'd try going back to Ubuntu.
Everything works great, except occassionally my applications just stop opening. I click on them, and it says 'Starting XXX...', and then nothing. Everything else is working fine, but they refuse to open until I restart my laptop. 
I can't find out what would happen if they were opened through a command line either, as my terminal won't open.
Apologies for the vagueness of the problem - any help would be much appreciated.

---

### Post by moma on 2006-12-31
Start the terminal program immediately after you login. It should start then.  

1) 
How much memory your box has?  Report
$ [COLOR="SeaGreen"]cat /proc/meminfo [/COLOR]

What about disk space? Report 
$ [COLOR="SeaGreen"]df -h [/COLOR]

Report also mounted partitions (interested to know where's /home and /tmp if they have own partitions)
$ [COLOR="SeaGreen"]mount[/COLOR]
------------------------------------------------------------

2) The programs that do not start, are they "sudo" (super user) programs or just ordninary ones ? 

3) Create a new user and login with that. Can you see the same problem then?

---

### Post by joth on 2006-12-31
Thanks for your quick reply.

OK, this is interesting - I tried to logout and login again to see if my terminal would open, and when I tried to logout, a very ugly screen came talking about a display or GDM error. I restarted my computer, and a console screen came up talking about fatal errors. It told me to do a manual fsck from t.he maintenance console, which I did, and loads of disk errors came up that I didn't really understand - I typed yes to all the requests to fix the errors, restarted again, and everything's running smoothly so far.
Unfortunately, previous times when my apps didn't open, everything ran smoothly for ages before that anyway, so I can't tell whether the problem has been fixed by this.
All the programs are ordinary, and here's the information you asked for:

Memory: 
MemTotal:       904288 kB
MemFree:        601792 kB
Buffers:          8352 kB
Cached:         169944 kB
SwapCached:          0 kB
Active:         165496 kB
Inactive:       115652 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       904288 kB
LowFree:        601792 kB
SwapTotal:     1622524 kB
SwapFree:      1622524 kB
Dirty:             620 kB
Writeback:           0 kB
Mapped:         146728 kB
Slab:            13132 kB
CommitLimit:   2074668 kB
Committed_AS:   353872 kB
PageTables:       1484 kB
VmallocTotal:   114680 kB
VmallocUsed:      4232 kB
VmallocChunk:   110324 kB

Disk space:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.4G   32G   7% /
varrun                442M   80K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
procbususb             10M   96K   10M   1% /proc/bus/usb
udev                   10M   96K   10M   1% /dev
devshm                442M     0  442M   0% /dev/shm
lrm                   442M   18M  425M   4% /lib/modules/2.6.17-10-generic/volatile

Mount:
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by moma on 2006-12-31
fsck reported disk errors.  It may indicate that the /dev/hda drive is going to fail. A sign of beginning malfunction.

Take a good backup of your private data on $HOME.

The memory and disk space values values are OK. You have plenty of free (available) memory (Available memory = Freemem + Cached memory). 

And you have only used 7% of your root filesystem (/,  36GB) which contains both /tmp and /home directories.'

Keep monitoring the systemlog. Possible disk errors will be reported there.
$ [COLOR="SeaGreen"] tail -20 /var/log/messages[/COLOR]
or 
$ [COLOR="SeaGreen"]dmesg [/COLOR]

---

### Post by joth on 2007-01-01
Thanks for your help.

By beginning malfunction, do  you mean something serious? i.e. Is my laptop itself starting to break down, I should check my warranty, or is it fixable?

---

