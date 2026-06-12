---
title: "no space left on disk?"
date: 2018-09-16
forum: General Help
---

### Post by RangerK on 2018-09-16
I'm getting really strange results on my computer, and I thought I'd ask for advice.  

- I can't even create a text file on the desktop.  It tells me there's no space left.  

- You can see the output of ```
df
``` below - 100% usage.

Three things which may be related:

1) The hard drive is encrypted.  Part of the boot process is decrypting it.
2) I have Virtual Box Installed, though I haven't used it lately.
3) There seemed to have been a hardware problem.  The laptop wouldn't boot, showing instead rapidly scrolling text and staying like that for as long as I left it on.  Amazingly, the computer started working again (sort of) without any intervention.

```
~$ df -h
```


```
Filesystem                       Size  Used Avail Use% Mounted on
udev                             3.9G     0  3.9G   0% /dev
tmpfs                            787M   78M  709M  10% /run
/dev/mapper/VivoSilver--vg-root  909G  863G     0 100% /
tmpfs                            3.9G  192K  3.9G   1% /dev/shm
tmpfs                            5.0M  4.0K  5.0M   1% /run/lock
tmpfs                            3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1                       181M  181M     0 100% /snap/vlc/190
/dev/loop2                        87M   87M     0 100% /snap/core/4571
/dev/loop5                        87M   87M     0 100% /snap/core/4650
/dev/loop0                       196M  196M     0 100% /snap/vlc/555
/dev/loop4                       199M  199M     0 100% /snap/brave/32
/dev/loop3                       199M  199M     0 100% /snap/brave/31
/dev/loop6                        88M   88M     0 100% /snap/core/5328
/dev/loop8                       198M  198M     0 100% /snap/vlc/365
/dev/loop7                       189M  189M     0 100% /snap/brave/25
/dev/sda1                        472M  116M  332M  26% /boot
tmpfs                            787M   32K  787M   1% /run/user/1000
/home/user/.Private              909G  863G     0 100% /home/user
```

---

### Post by TheFu on 2018-09-16
Please edit the original post to use code tags so things line up.

Output from **df -h** and **df -i** needed.
```
 /dev/mapper/VivoSilver--vg-root 909G 863G 0 100% /
```
is the important part.
909 x .95 = 864  ... so that explains why a normal userid cannot create any files or directories there.

Also, for most file systems, 5% is reserved only for root use.  This is a good idea for the OS and /var partitions, but can be frustrating for /home partitions.  And the larger an LV is (you are using LVM), the more space gets reserved for root. You can use the **tune2fs** command to see how much is reserved, but 5% is the default.  You can reduce that, but the better solution is to splce the LV for /var, /, and /home into 3 different LVs.  It will be complicated because you are using Home directory encryption. Sorry, I can't help with that.

In general, / should not be more than 25G.  /var/ should be whatever you need depending on the uses.  5G should be plenty, unless you use virtual machines and put them into /var/lib/libvirt somewhere (the default).  Then you'll want sufficient storage to hold all the VMs.  I limit /home/ to be 20G or less too, because I place media files elsewhere.  All of these steps help manage storage easier and makes for easier backups.  For me, all storage decisions come back to backup and recovery needs.

So, the short answer is to use this command to reduce the root reserved storage to be 2%.
```
sudo tune2fs -m 2 /dev/mapper/VivoSilver--vg-root
```

From the tune2fs manpage:```

       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by  privileged  processes.   Reserving some number of filesystem
              blocks for use by privileged processes is done to avoid filesysâ
              tem  fragmentation,  and  to  allow system daemons, such as sysâ
              logd(8), to continue to function correctly after  non-privileged
              processes  are  prevented  from writing to the filesystem.  Norâ
              mally, the default percentage of reserved blocks is 5%.
```
I wouldn't leave the storage setup this way very long, but changing the reserved size will let you keep working for a day or so. There are dangers, so beware.

---

### Post by HermanAB on 2018-09-16
Check what is in /var/log

You can safely delete everything in /var/log.  The most important log files will be recreated when you reboot and the unimportant ones will stop logging, which, on a single user machine, is not bad either.

---

