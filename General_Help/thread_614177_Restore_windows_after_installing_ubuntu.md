---
title: "Restore windows after installing ubuntu??"
date: 2007-11-15
forum: General Help
---

### Post by td00174 on 2007-11-15
Here's the deal. 

So, I really wanted to have dual boot of vista and ubuntu. 

I called myself downloading and installing Ubuntu...thinking it would automatically choose the correct partion options for us not so computer literate people.

Well...I backed up my vista OS/files on my secondary hard drive and proceeded to install Ubuntu on the primary hard drive with vista.

I'm pretty sure I did a clean install of Ubuntu...but that's not what I wanted to do. I wanted to dual-boot as I already stated.

From the main OS selection screen, there is no instance of windows that i can choose from. :(

When I try to access my secondary hard drive from Ubuntu, it doesn't even show in the system window. [[[scared]]]

Someone please tell me that I can recover windows somehow......please.

I have no access to a VISTA cd as it came with my new system. Of course, this is a classic case of all my important school/course work being lost forever if I can't restore windows.

Help...please...

I doubt I use partioning, because looking at screen shots now...I never realized the option of being able to assign certain amount of diskspace to each OS.

---

### Post by taurus on 2007-11-15
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
cat /etc/fstab
df -h
```

---

### Post by td00174 on 2007-11-15
XXXXXX@t:~$ sudo fdisk -l
[sudo] password for XXXXX:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x309fbd63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
XXXXXXX@t:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
XXXXXX@t:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  2.1G  132G   2% /
varrun               1009M  100K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   64K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
XXXXXX@t:~$

---

### Post by taurus on 2007-11-15
> **td00174 said:**
> XXXXXX@t:~$ sudo fdisk -l
[sudo] password for XXXXX:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x309fbd63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
XXXXXXX@t:~$ cat/etc/fstab
bash: cat/etc/fstab: No such file or directory
XXXXXX@t:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  2.1G  132G   2% /
varrun               1009M  100K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   64K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
XXXXXX@t:~$

Sorry dude BUT you told the installer to use the whole harddrive so it did.

---

### Post by td00174 on 2007-11-15
Alright. I figured. Not mad, just a little disappointed. Learning experience :D

So my next question would be...

Since I did a backup of my system prior to installing Ubuntu and saved that on my second hard drive...is there a way that I can access that and do a *restore?*

Or, if I would happen to get my hands on a recovery disk or even the vista cd itself, would I be able to restore my old system from the secondary hard drive??

---

