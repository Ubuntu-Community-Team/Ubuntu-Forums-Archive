---
title: "File transfer between partitions extremely slow Kubuntu 18.04"
date: 2018-09-15
forum: General Help
---

### Post by joshua-m-salazar on 2018-09-15
I have a problem when transferring data from one **ext4** (*/dev/sda2*, mounted on */*) partition to another **ntfs** (*/dev/sda4*, mounted on */data*) inside the same physical disk (*/dev/sda*).

It does not matter the size of the files, always is very slow, for example:

[IMG]https://i.stack.imgur.com/LUnJ9.png[/IMG]


But when transferring from an external drive to the root partition **ext4** (*/dev/sda2*, mounted on */*) it has normal speed:

[IMG]https://i.stack.imgur.com/Lk1GX.png[/IMG]

I have my disks configured in this way:

[IMG]https://i.stack.imgur.com/ZxAqA.png[/IMG]

It only happens when using the **ntfs** (*/dev/sda4*) partition.
Any suggestion? I don't want to have this problem, it is very annoying.

---

### Post by TheFu on 2018-09-15
First, don't use a GUI to move files.  Do it from a shell to avoid any funky overhead that different GUI tools add.  Stay as close to the core OS as possible.  That means using the shell.

Don't use GVFS. Use a real mount.  Something either from the shell or in the fstab.  It is likely you are doing this already.

NTFS is implemented as a FUSE file system.  FUSE is slow.  Also, the driver has a default cache that seems really small.  Increase it to 4K for better performance.

Ensure the NTFS partition isn't misaligned. If you used a recent gparted or parted then that happens automatically. **sudo parted -l **should complain if they aren't aligned.

Moving data on the same physical disk is like moving 2x the data because it has to be read and written on the same control channel, same SATA cable, to the same physical disk.

It is possible to tune the HDD access using **hdparm**. There isn't any way to know the best values other than trial and error.    

```
$ sudo mount -o noatime,async,big_writes -t ntfs-3g /dev/sda4 /data
```

I tested this and it wasn't any faster, but all my NTFS partitions are on USB2 connections and those are very slow already.  I just don't use NTFS unless absolutely required.  For an internal disk, if you don't dual boot, I don't see the point to use NTFS.

That's all I got. Sorry.

---

### Post by joshua-m-salazar on 2018-09-16
> **TheFu said:**
> First, don't use a GUI to move files. Do it from a shell to avoid any funky overhead that different GUI tools add. Stay as close to the core OS as possible. That means using the shell.

Don't use GVFS. Use a real mount. Something either from the shell or in the fstab. It is likely you are doing this already.

NTFS is implemented as a FUSE file system. FUSE is slow. Also, the driver has a default cache that seems really small. Increase it to 4K for better performance.

Ensure the NTFS partition isn't misaligned. If you used a recent gparted or parted then that happens automatically. **sudo parted -l **should complain if they aren't aligned.

Moving data on the same physical disk is like moving 2x the data because it has to be read and written on the same control channel, same SATA cable, to the same physical disk.

It is possible to tune the HDD access using **hdparm**. There isn't any way to know the best values other than trial and error. 

```
$ sudo mount -o noatime,async,big_writes -t ntfs-3g /dev/sda4 /data
```

I tested this and it wasn't any faster, but all my NTFS partitions are on USB2 connections and those are very slow already. I just don't use NTFS unless absolutely required. For an internal disk, if you don't dual boot, I don't see the point to use NTFS.

That's all I got. Sorry.



Yeah, you helped me to solve it!

So if it helps to anyone:

Here is my output of **sudo parted -l**:


```
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  200MB  199MB   fat32                 boot, esp
 2      200MB   250GB  250GB   ext4
 3      250GB   256GB  6000MB  linux-swap(v1)
 4      256GB   780GB  524GB   ntfs                  msftdata
```

I had this configuration for the automounting process of my ntfs in the **/etc/fstab**:

```
UUID=3D8D3102208D0C33 /data ntfs uid=1000,gid=1000,umask=0022,sync,auto,rw 0 0
```


So, I unmounted my slow ntfs partiton with **sudo umount /dev/sda4 **and by commenting my last line and using your suggestion with **sudo mount**: ...

```
sudo mount -o noatime,async,big_writes -t ntfs-3g /dev/sda4 /data
```

[B]...I achieved better (Way better!) velocity!
[/B] Even using the GUI of dolphin.


[IMG]https://i.imgur.com/sVZ7Yfm.png[/IMG]



Finally, I added your suggestion in a script under the **/etc/init.d** folder gave it execute permissions and updated the startup scripts of the system, *do you have any other suggestion*?, I don't know if its the best way to do it then.

```
 
# cat "sudo mount -o noatime,async,big_writes -t ntfs-3g /dev/sda4 /data" > "/etc/init.d/automountNTFS.sh"
# chmod +x /etc/init.d/automountNTFS.sh
# cd /etc/init.d
# update-rc.d automountNTFS.sh defaults

```




Thanks!

---

### Post by TheFu on 2018-09-16
I would just use the same options inside the fstab, assuming changing from NTFS isn't an option.  I'd still make that my priority.
async,big_writes and the driver are the most important.   Whether you run the mount command or use it in the fstab or in an autofs config doesn't matter. They all work with the same underlying stuff. 

I most definitely would NOT put it into the init.d/ directory.

---

### Post by joshua-m-salazar on 2018-09-16
Perfect.

Thank you very much! You've saved me a lot of time! 

I will soon have a dual boot.

---

### Post by TheFu on 2018-09-17
If you plan to have a dual boot setup, there is much more necessary.  Whatever you do, make a full, complete, 100% backup before you begin.  It is very easy to have everything wiped.  Plus Windows has a habit of wiping the boot record to prevent any other OS from working.  That happens a few times a year.  Be prepared with excellent backups.

---

### Post by HermanAB on 2018-09-17
Hmm, dual boot is so 20th century...

Rather install Linux, then install KVM or Virtualbox and make a Windows virtual machine.  Then, you can run Windows in a window, the way the computer gods intended.

---

### Post by joshua-m-salazar on 2018-09-19
> **HermanAB said:**
> Hmm, dual boot is so 20th century...

Rather install Linux, then install KVM or Virtualbox and make a Windows  virtual machine.  Then, you can run Windows in a window, the way the  computer gods intended.

I'd love to, but I have an slow PC

---

### Post by joshua-m-salazar on 2018-09-19
> **TheFu said:**
> If you plan to have a dual boot setup, there is  much more necessary.  Whatever you do, make a full, complete, 100%  backup before you begin.  It is very easy to have everything wiped.   Plus Windows has a habit of wiping the boot record to prevent any other  OS from working.  That happens a few times a year.  Be prepared with  excellent backups.

Thanks, I'll take the consideration. Does this happen even with win 7?

---

