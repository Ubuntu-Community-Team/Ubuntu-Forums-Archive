---
title: "Unable to start live-session (problem with filesystem.squasfs)"
date: 2016-02-22
forum: General Help
---

### Post by Zorrothustra on 2016-02-22
Hi,

Recently I started getting warnings after booting that my boot partition /boot/efi only had 8,2 kb of space. The warning started after I made a boot-repair usb-flash-drive to fix another machine. My guess is that making the usb-drive I somehow messed with the boot files on the machine where everything worked well. 

Intially I got rid of older linux-image and linux-header files. Then I tried to enlarge the boot partition (with Gparted), which wasn't possible because the ext4 / partition blocked it from being able to make it bigger, as mentioned in the second answer [here]("http://askubuntu.com/questions/280211/how-do-i-resize-my-boot-partition").

I obviously tried to resize the main partition but somehow it seems as if there is no possibility to make it either smaller or bigger, even with unallocated space available before or after the partition. I suspected it might have something to do with the partition being mounted, so tried to do this operation through a live-session. 

I tried to boot from a live-usb Ubuntu 14.04 (which works perfectly on other machines) and boot-repair live-session but both gave me following error:

"initramfs moint: mounting /dev/loop0 on //filesystem.squashfs failed:/ Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on filesystem.squashfs"

I finally shrank my swap to be able to make temporarlily a bigger boot partition. I copied the contents of the old boot partition in the new partition (as suggested in some threads, such as [this one]("http://ubuntuforums.org/showthread.php?t=2225043")), changed fstab with new UUID of the boot drive. It worked at first, but second time I booted up I got a blue window "Default Boot Device Missing or Boot Failed". I manage to boot however: by just pressing enter the next screen allows me to chose from two drives to boot, and one of them works. The warning of low diskspace on the boot partition is gone, that's good. I'll live with the blue screen at boot for the time being (I guess the answer to this problem is probably [here]("https://help.ubuntu.com/community/MovingLinuxPartition")), because I'dd like to resolve the underlying problem with priority. But I don't know how. 

First. Is it normal that this filesystem.squashfs is about 490 Mb big ? On another computer running the same ubuntu-version it is hardly a few kbs. It looks like this file is responsible for the original problem (lack of space on boot partition).
Second, how can I fix the serious problem of not being able to do a live-session, or even a clean install ? 

I'm running 14.04 64bit btw

Thanks in advance

Z.

---

### Post by oldfred on 2016-02-22
Your /boot/efi is not the Ubuntu /boot partition. 
Most desktop installs do not need a /boot partition, but LVM does use it.

The /boot/efi partition is the ESP - efi system partition which is a FAT32 formatted partition.

I have noticed that Boot-Repair backups up some (all?) of it and you see new folders in the ESP. If you have run Boot-Repair many times perhaps that is the issue?

Not booting flash drive is a separate issue. Did you install grub to it? It uses syslinux for BIOS boot and has grub only for UEFI boot. But grub is not in MBR.

If you can boot post this, only shows mounted partitions:
df -h

---

### Post by Zorrothustra on 2016-02-22
Thanks for your answer Oldfred,

> **oldfred said:**
> 

I have noticed that Boot-Repair backups up some (all?) of it and you see new folders in the ESP. If you have run Boot-Repair many times perhaps that is the issue?

Actually, I never ran it on the machine, I just made a boot-repair live usb on it through Unetbootin. I used that usb-drive succesfully on another machine. The low diskspace issue appeared on the machine I used to make that live usb, the next boot after making it. 

> **oldfred said:**
> 

Not booting flash drive is a separate issue. Did you install grub to it? It uses syslinux for BIOS boot and has grub only for UEFI boot. But grub is not in MBR.

Not sure what you mean by asking if I installed brub to it. It is an orginal standard 14.04 LTS I used to install Ubuntu on several machines. I mostly let Ubuntu do the rest of the work. 


> **oldfred said:**
>  If you can boot post this, only shows mounted partitions:
df -h

This is the result:

```
Filesystem      Size  Used Avail Use% Mounted on
udev            932M   12K  932M   1% /dev
tmpfs           189M  1,1M  188M   1% /run
/dev/mmcblk0p2   27G   22G  3,2G  88% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none            942M  152K  942M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/mmcblk0p4  964M  511M  453M  54% /boot/efi

```

---

### Post by Zorrothustra on 2016-02-22
Thanks for your answer Oldfred,

> **oldfred said:**
> 

I have noticed that Boot-Repair backups up some (all?) of it and you see new folders in the ESP. If you have run Boot-Repair many times perhaps that is the issue?

Actually, I never ran it on the machine, I just made a boot-repair live usb on it through Unetbootin. I used that usb-drive succesfully on another machine. The low diskspace issue appeared on the machine I used to make that live usb, the next boot after making it. 

> **oldfred said:**
> 

Not booting flash drive is a separate issue. Did you install grub to it? It uses syslinux for BIOS boot and has grub only for UEFI boot. But grub is not in MBR.

Not sure what you mean by asking if I installed grub to it. It is an orginal standard 14.04 LTS I used to install Ubuntu on several machines. I mostly let Ubuntu do the rest of the work. 


> **oldfred said:**
>  If you can boot post this, only shows mounted partitions:
df -h

This is the result:

```
Filesystem      Size  Used Avail Use% Mounted on
udev            932M   12K  932M   1% /dev
tmpfs           189M  1,1M  188M   1% /run
/dev/mmcblk0p2   27G   22G  3,2G  88% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none            942M  152K  942M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/mmcblk0p4  964M  511M  453M  54% /boot/efi

```

---

### Post by oldfred on 2016-02-23
Your ESP - /boot/efi seems large and has a lot used. I might check what is in it. I normally suggest 300 to 500MB for ESP, but you have used 511. Most installs work fine with Windows default size of 100MB for the ESP.

Is this a 32GB flash card. You have used 22 of 27GB.
If /home is inside / (root) then all data quickly can add up.
Plus you need to regularly houseclean.

 #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB


        RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by Zorrothustra on 2016-02-25
Thanks again Oldfred,

Indeed the boot/efi is large. The file causing this is the one named in the title (filesystem.squasfs), it's 480 Mb or so in size. I'm no specialist, but compared to that file on another computer I have, this seems huge. It ran on 500Mb without problems, until one day...  (see original question posted).

Trying to solve it, I took a portion out of my swap, made this the /boot/efi hoping that the file - with a little more room - would restore itself to a "normal" size. It didn't. 

I would dare to do a boot-repair out of a normal session on the pc, but if something goes wrong, I do already know I will not be able to start a live-session due to the error message, interestingly referring to that exact file. It seems risky, but unless there is another way to "clean up" that filesystem.squasfs file, I just see no other way than using boot-repair... 

BTW: There is indeed little space for my /home, but I manage it, no problem with that. Your line for the terminal helped me clean it a little more, thanks for that. 

Z.

---

### Post by oldfred on 2016-02-25
I do not have a large filesystem.squasfs in my ESP. If large like that it seems like it is from the live installer.
Did you experiment with other systems? Or run live installer command into your /dev/mmcblk0p4 for installing somehow? Or are you just running live system from partition p4?

Since flash drive, you may have installed to it and most installers would copy files to the FAT32 file system as that is normal. But Ubuntu live installer usually just has one FAT32 boot partition that has both the efi boot files and the system to use as live system or installer.

---

### Post by Zorrothustra on 2016-02-25
>  Did you experiment with other systems? Or run live installer command into your /dev/mmcblk0p4 for installing somehow? Or are you just running live system from partition p4? 

Actually it is a single boot Ubuntu 14.04 that I installed from a usb-drive on the 32Gb eMMC drive (which I thought was SSD to be honest). It worked perfectly, until the day I used the computer with the problem to create a "live-boot-repair USB" a few weeks ago, that I had to run on *another* computer. My guess is that is where the problem lies. 

Anyway, how can I proceed ? If I understand you well, the partition configuration is a bit strange. Not sure how that happened. Thing is, it worked without a problem...

---

### Post by oldfred on 2016-02-25
I think you can just probably delete that file.

The only issue on partitioning is that for a smaller device, the ESP is a bit large. Windows only uses 100MB and users dual boot. I normally suggest 300 or 500MB when you have larger drives just so in future you have room for other configurations.

---

### Post by Zorrothustra on 2016-02-25
Thanks for you help again Oldfred. I deleted the file "filesystem.squasfs". Advantage is I can now start live-session, so technically I can at least reinstall. I am relieved just for that...

On the other hand, I don't manage to start into the installed Ubuntu, I can just access it through the live session. From the two options I had in the "blue screen boot window" when starting without live-usb, one is gone, the one that worked... Started live-session again, looked into fstab from installed Uduntu, looked into gparted what I could do, I don't see where I should change things here... Seem to be turning in circles.  

I guess there is no magic formula here to avoid a reinstall ? Well, at least reinstall became an option now :)

Z.

---

### Post by oldfred on 2016-02-26
If misconfigured grub/kernel but otherwise a good install, you can use Boot-Repair's advanced mode to totally uninstall grub and reinstall. Include tick mark to install latest kernel.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by thomas101 on 2016-03-24
It could be a problem with the auto detection function of the file system together with  iso-image file.
If the file type of the iso-image is of type "udf" then you have the problem because the command "fstype" is used for the detection.
But fstype reports always iso9660, also if the file type is udf.
To find out the correct file system, you can use blkid instead.

To fix the problem, you have to modify the file "casper-helpers". The file is located in /usr/share/initramfs-tools/scripts/.

root@ole1:/# diff /tmp/casper-helpers /usr/share/initramfs-tools/scripts/casper-helpers 
45,49d44
<     # added 23.03.2016, fstype cannot detect file system of type "udf"
<     if [ "$FSTYPE" == "iso9660" ]; then            # added 23.03.2016
<        /sbin/blkid -s TYPE -o value $1 2>/dev/null # added 23.03.2016
<        return 0                                    # added 23.03.2016
<     fi                                             # added 23.03.2016

# complete function
get_fstype() {
    local FSTYPE
    local FSSIZE
    eval $(fstype < $1)
    # added 23.03.2016, fstype cannot detect file system of type "udf"
    if [ "$FSTYPE" == "iso9660" ]; then            # added 23.03.2016
       /sbin/blkid -s TYPE -o value $1 2>/dev/null # added 23.03.2016
       return 0                                    # added 23.03.2016
    fi                                             # added 23.03.2016
    if [ "$FSTYPE" != "unknown" ]; then
        echo $FSTYPE
        return 0
    fi
    /sbin/blkid -s TYPE -o value $1 2>/dev/null
}

#----------------------
To complete the change, you have to rebuild the initramfs-filesystem with
update-initramfs -u 

After these changes, I can boot iso-images which contain files with size larger than 4 GB (e.g. filesystem.squashfs).

Thomas

---

