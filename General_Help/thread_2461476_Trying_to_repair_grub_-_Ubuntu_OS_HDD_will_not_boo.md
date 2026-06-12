---
title: "Trying to repair grub - Ubuntu OS HDD will not boot after update"
date: 2021-05-01
forum: General Help
---

### Post by freeflyjohn on 2021-05-01
I use webmin to keep my Ubuntu (home) Server 16.04 up to date.  A few weeks ago an update required a reboot (I think it said a kernel update was required?) but since the update the OS will not boot.

I 'think' the fault might be software rather than hardware as I can access and read the OS HDD.

To be on the safe side I do plan to change the OS drive and upgrade to 20.04, but in the mean time I would like to try and get the OS to boot and have the server up and running until I upgrade the OS and drive (possibly to an SSD).

Someone suggested performing a grub update, so I ran Ubuntu 20.04 from a live USB and was able to access and read the OS HDD but I get the following error...

```

/run/lvm/lvmetad.socket: connect failed: No such file or directory


  WARNING: Failed to connect to lvmetad: No such file or directory. Falling back to internal scanning.


grub-probe error cannot find a grub drive for /dev/sdb1

```

The OS HDD (a WD Red 4TB) was partitioned as follows:

Partition #1: /boot, 1GB, ext4
Partition #2: swap, 16 GB , swap
Partition #3: /root, 128 GB , ext4
Partition #4: /home, rest of volume, ext4

From the live USB I ran the following commands:

I mounted the OS HDD:

```

sudo mount /dev/sda3 /mnt

``` 


Then I binded the /boot partition:
 
```

sudo mount --bind /media/ubuntu/9ed61d0e-8d1a-401d-834f-7f2b60eccacb /boot

```
 
Then I binded the other folders:

```
 
cd /mnt
sudo mount --bind /dev dev/
sudo mount --bind /sys sys/
sudo mount --bind /proc proc/
sudo mount --bind /dev/pts dev/pts

```
 
Then I changed root to mnt:

```
 
sudo chroot /mnt

``` 
 
Then I ran grub update:

```
 
sudo update-grub


```

[ATTACH=CONFIG]288402[/ATTACH]

I did a google search on the error and someone said to change the BIOS boot from LEGACY to UEFI, so I did that and tried again.


This time I also ran:


```
 


sudo grub-install


```  


But that gave me an error about blocklists...

[ATTACH=CONFIG]288403[/ATTACH]


How can I get my OS HDD up and running again ?

The server is a Dell T30 and is fitted with 4 x 4TB Red HDD, I mainly use it for Plex, Nextcloud, data storage and backups etc.

---

### Post by guiverc on 2021-05-01
Ubuntu 16.04 LTS has completed its *standard* support days and is only getting updates now if you've ESM enabled.  30th April 2021 was the first day of *extended* support.

Refer [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

which also has links should you wish to enable ESM.

Given 16.04 is out-of-support (*without ESM*), there aren't any more updates, so if your box is online I'd consider upgrading **asap** (*ideally before 1st May 2021 or now*).

---

### Post by freeflyjohn on 2021-05-01
> **guiverc said:**
> Ubuntu 16.04 LTS has completed its *standard* support days and is only getting updates now if you've ESM enabled.  30th April 2021 was the first day of *extended* support.

Refer [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

which also has links should you wish to enable ESM.

Given 16.04 is out-of-support (*without ESM*), there aren't any more updates, so if your box is online I'd consider upgrading **asap** (*ideally before 1st May 2021 or now*).

Thanks guiverc, I do intend to upgrade to 20.04 but I just want to get my existing OS HDD up and running if possible as a temporary measure.

Any idea's how to repair my OS HDD ?

---

### Post by oldfred on 2021-05-01
Many repairs require downloading grub again, but repository now is closed, so difficult to do.

Since 4TB drive, it should have been gpt partitioned.
And with gpt, you have to have either a bios_grub partition (1MB unformatted with bios_grub flag) for BIOS boot or an ESP - efi system partition (FAT32 300 to 500MB with esp, boot  flags) for UEFI. 
And you need to know for sure which boot mode your system is in.
And if LVM, you have to mount the volumes (/dev/mapperxx?), but I do not know LVM.

post this:
sudo parted -l

---

### Post by freeflyjohn on 2021-05-02
Thanks oldfred

Below are screenshots - it says the partition table is gpt...

[ATTACH=CONFIG]288410[/ATTACH]

[ATTACH=CONFIG]288411[/ATTACH]

---

### Post by oldfred on 2021-05-02
You are showing sda1 as ext4 but as esp,boot. That is not correct.

It is either ext2 (but could be ext4?) and just boot. This would then be a separate /boot partition which is often used with LVM or server type installs. If UEFI and separate /boot partition, you also need the ESP.
And since gpt, you need a bios_grub partition for grub to correctly install in BIOS mode to gpt drive.

Or it is the ESP and then it has to be FAT32 formatted.

---

### Post by freeflyjohn on 2021-05-02
> **oldfred said:**
> You are showing sda1 as ext4 but as esp,boot. That is not correct.

It is either ext2 (but could be ext4?) and just boot. This would then be a separate /boot partition which is often used with LVM or server type installs. If UEFI and separate /boot partition, you also need the ESP.
And since gpt, you need a bios_grub partition for grub to correctly install in BIOS mode to gpt drive.

Or it is the ESP and then it has to be FAT32 formatted.

The OS HDD (a WD Red 4TB) was partitioned as follows:


Partition #1: /boot, 1GB, ext4
Partition #2: swap, 16 GB , swap
Partition #3: /root, 128 GB , ext4
Partition #4: /home, rest of volume, ext4

A screenshot of the setup is shown below:

[ATTACH=CONFIG]288415[/ATTACH]

So sda1 should be 'ext4' and 'boot', but not 'esp' ?

When I mount the /boot partition I can see grub etc, would it help to show the files and folders on this partition ?

I'm not sure why the 'esp' flag is set, do I simply need to unset this flag ?

I have no idea what else to try next so any suggestions would be appreciated.

---

### Post by oldfred on 2021-05-02
Remove esp flag and create a tiny 1 or 2 unformatted partition and add bios_grub flag.
Not sure how you got grub to install without bios_grub on gpt.
It typically gives massive warnings that that it does not want to install as it had to use blocklists. You had to force an install.
And I think now it does not let you install without bios_grub.

If chrooting, you have to also mount /boot as its a separate partition.

---

### Post by freeflyjohn on 2021-05-02
> **oldfred said:**
> 
It typically gives massive warnings that that it does not want to install as it had to use blocklists. You had to force an install.


The other day I did a google search on the error below...

```

/run/lvm/lvmetad.socket: connect failed: No such file or directory


  WARNING: Failed to connect to lvmetad: No such file or directory. Falling back to internal scanning.


grub-probe error cannot find a grub drive for /dev/sdb1


```

Someone said to change the BIOS boot from LEGACY to UEFI, so I did that and tried again and also ran...

```

sudo grub-install

```

That's when I got the warnings about blocklists...

[ATTACH=CONFIG]288416[/ATTACH]

---

