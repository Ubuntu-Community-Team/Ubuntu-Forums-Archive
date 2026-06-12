---
title: "Problem with FAT32 partition"
date: 2007-05-19
forum: General Help
---

### Post by Zdravko on 2007-05-19
Hi there!
When I installed Ubuntu, I set additional 5GB of FAT32, just for exchange between Win. But I think I forgot to auto mount it. Now neither Ubuntu, nor Win sees this partition. How can I fix this?

---

### Post by taurus on 2007-05-19
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Zdravko on 2007-05-19
It produces:
> zdravko@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834        9049     9767520    5  Extended
/dev/sda5            7834        8927     8787523+  83  Linux
/dev/sda6            8928        9049      979933+  82  Linux swap / Solaris
zdravko@ubuntu:~$ 


---

### Post by taurus on 2007-05-19
Are you sure you connect it right?  Get into the BIOS and see if the BIOS even detects your second harddrive.  If it doesn't detect it, open the box and look at the cable/power again to make sure they are securely tight.

---

### Post by Zdravko on 2007-05-19
What second hard drive? I have only one hard drive.

---

### Post by taurus on 2007-05-19
And I don't see any 5GB fat32 partition on /dev/sda, either.

---

### Post by Zdravko on 2007-05-19
The whole HDD is 80GB. 60GB are for Win. For Ubuntu I must have set about 10GB. The rest must be set FAT32 - from the Ubuntu's installer.

---

### Post by taurus on 2007-05-19
Post

```
df -h
free
```

---

### Post by Zdravko on 2007-05-19
Okay:
> zdravko@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             8.3G  3.0G  4.9G  38% /
varrun                248M  100K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb            248M  116K  248M   1% /proc/bus/usb
udev                  248M  116K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1              61G   23G   38G  38% /media/sda1
zdravko@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        506392     497988       8404          0      32376      88648
-/+ buffers/cache:     376964     129428
Swap:       979924      33868     946056


---

### Post by Zdravko on 2007-05-19
Anyone?

---

### Post by Slim Odds on 2007-05-19
> **Zdravko said:**
> Anyone?

From the list you showed earlier, there is no fat32 partition.

If there is still space left on the drive, create one. Otherwise, start over.

---

### Post by Zdravko on 2007-05-19
Okay. How do I partition the rest space?

---

### Post by strabes on 2007-05-19
Install gparted. I believe that you won't have to use the live CD because that portion of your hard disk isn't currently mounted.

---

### Post by TriggerHappyChewie on 2007-05-19
EDIT: nevermind

---

### Post by Zdravko on 2007-05-19
Well, it seems that I haven't set properly the partition during the installation.
Look at the screenshot. What do I do next to format it as fat32?

---

### Post by Zdravko on 2007-05-20
I managed it alone! :)

---

### Post by Zdravko on 2007-05-20
Maybe not. Now every time I want to open it with Nautilus, I am asked about my password. Why? How do I avoid this???
Help!

---

### Post by Zdravko on 2007-05-23
Anyone? It seems that the partition is not mounted.

---

### Post by Zdravko on 2007-05-31
Anyone?! It gets pretty annoying.

---

### Post by Zdravko on 2007-06-01
Ignoring my question makes things even worse...

---

### Post by Zdravko on 2007-06-02
Bump!

---

### Post by Zdravko on 2007-06-03
Bump 2.

---

### Post by vanadium on 2007-06-03
If sudo fdisk -l does not list your FAT32 partition, then it isn't there. Even if that partition were not formatted, it should show up using the command. Thus, my conclusion is that you did not really created the partition although you think you did.

You will need to use the gparted disk partitioning utility to see the current state of your disk. Chances are that there is indeed some free space left on your drive where you will be able to create a partition that you can format as fa32. If there is no space left, then you will need to resize an existing partition. This can be done without destroying the date using gparted.

Any partitioning utility will only work on unmounted volumes. You therefore need to run gparted after bootng from the live CD, but a better approach might be to download the dedicated gparted live CD.

Playing with partitions always involves the chance that you screw up, especially when less experienced. Thus, before proceeding, BACK UP ALL YOUR USER DATA.

---

### Post by Zdravko on 2007-06-03
> **vanadium said:**
> If sudo fdisk -l does not list your FAT32 partition, then it isn't there. Even if that partition were not formatted, it should show up using the command. Thus, my conclusion is that you did not really created the partition although you think you did.

You will need to use the gparted disk partitioning utility to see the current state of your disk. Chances are that there is indeed some free space left on your drive where you will be able to create a partition that you can format as fa32. If there is no space left, then you will need to resize an existing partition. This can be done without destroying the date using gparted.

Any partitioning utility will only work on unmounted volumes. You therefore need to run gparted after bootng from the live CD, but a better approach might be to download the dedicated gparted live CD.

Playing with partitions always involves the chance that you screw up, especially when less experienced. Thus, before proceeding, BACK UP ALL YOUR USER DATA.
I think you misunderstood my question. I managed to create the partition with gparted. But the problem is that IT IS NOT AUTO MOUNTED!

---

### Post by vanadium on 2007-06-03
Then you are almost set: it is a matter of having a correct fstab entry. See

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

---

