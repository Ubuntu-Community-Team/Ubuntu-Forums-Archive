---
title: "The volume &quot;Filesystem root&quot; has only 533.9 MB disk space remaining"
date: 2013-10-18
forum: General Help
---

### Post by Vesnog on 2013-10-18
Greetings,

After full installation of TeX Live 2013 I am coming across this problem pretty often. I think I need a different mount point for my /usr directory, but I do not know how to proceed. Can you aid me in the process or suggest an alternative remedy?

Many thanks
The output of df -i and df -h are as follows:
ongun@Vesnog:~$ df -i




```
ongun@Vesnog:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda6       915712 658845  256867   72% /
udev            206346    568  205778    1% /dev
tmpfs           210048    506  209542    1% /run
none            210048      3  210045    1% /run/lock
none            210048     10  210038    1% /run/shm
/dev/sda8      2138112  33705 2104407    2% /home
ongun@Vesnog:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        14G   13G  451M  97% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           784M  916K  783M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  424K  2.0G   1% /run/shm
/dev/sda8        33G  4.2G   27G  14% /home

```




OS: Ubuntu 12.04 LTS 32-bit

---

### Post by varunendra on 2013-10-19
> **Vesnog said:**
> I think I need a different mount point for my /usr directory, but I do not know how to proceed.
**[COLOR="#FF0000"]Disclaimer[/COLOR]** - *I have never done it myself, so try it at your own risk.*

In general - prepare a partition (ext3 or ext4) you want to use as /usr, and copy all the data from your current /usr directory to that new partition. To preserve the properties (permissions, owner/group etc.) of the files, use "rsync -ah" instead of "cp" or copying via GUI. Finally, add a mount-point entry for it in /etc/fstab.

For example, if you want to use sda7 as /usr, then format it as ext4 and copy the entire /usr directory to it with -
```
sudo rsync -aH /usr/ *<mount point where sda7 is currently mounted>*
```
Verify afterwards that the destination now contains the contents of /usr, not the "usr" directory itself (with the contents being inside it).

Then add the following entry in /etc/fstab -
```
/dev/sda7 /usr               ext4    defaults 0       2
```
It is recommended to use the UUID of sda7 instead of "/dev/sda7".

To be extra safe you should do it all from a Live session (in which case, the above commands and addresses will change relatively), and after having done the above, rename the original /usr directory to, say, "oldusr" and create a fresh, empty "usr" with sudo (because the mount point must exist). Then reboot and if anything goes wrong, just boot into live mode again > delete the empty "usr" > rename the "oldusr" back to "usr" and delete (or comment out) the /etc/fstab entry.

Having explained that, it recommended for new users to just keep the root (/) partition large enough to accommodate all these parts. Depending upon your partition layout, it may be easier too. If you consider this option, please show us your partition layout with -
```
sudo parted -l
```

Or, if parted is not installed -
```
sudo fdisk -l
```

---

