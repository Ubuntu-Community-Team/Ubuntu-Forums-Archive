---
title: "Corrupted Flash Drive"
date: 2013-01-17
forum: General Help
---

### Post by mehrdad_v on 2013-01-17
Hey Guys,

Hope you are doing well and don't mind me taking your time with my question. :)

I have a 16GB Corsair flash drive and it was working perfectly in both Windows (my wife's laptop) and Kubuntu (my laptop).
When it was connected to her laptop, I saw two unusual files on it which I couldn't remove them so I decided to connect it to Ubuntu in order to remove those files, but no matter how hard I tried, it seems it can't get mounted/recognised by Ubuntu.
FYI, it doesn't even work with Windows anymore.

Here is output of **ls /dev/sd*** before and after connecting flash to the laptop:
```
mehrdad@mehrdad-XPS:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5  /dev/sdb6
mehrdad@mehrdad-XPS:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5  /dev/sdb6  /dev/sdc
```Here is **dmesg** log after connecting flash drive:
```
mehrdad@mehrdad-XPS:~$ dmesg
[ 1426.027515] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
[ 1426.122148] scsi7 : usb-storage 2-1.2:1.0
[ 1427.119634] scsi 7:0:0:0: Direct-Access     Corsair  Voyager GT 3.0   1.00 PQ: 0 ANSI: 5
[ 1427.121197] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 1427.121897] sd 7:0:0:0: [sdc] 31293440 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 1427.122358] sd 7:0:0:0: [sdc] Write Protect is off
[ 1427.122368] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1427.122930] sd 7:0:0:0: [sdc] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[ 1457.520538] usb 2-1.2: reset high-speed USB device number 4 using ehci_hcd
```And here you can see Corsair in **lsusb** output:
```
mehrdad@mehrdad-XPS:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 002 Device 004: ID 1b1c:1a01 Corsair
```                                  I've tried everything I knew, all the Ubuntu forums and other forums have been searched but didn't come up with any solution.
 At least I know for sure that something is wrong with flash drive not with the system because all the other flash drives and external HDDs are working fine.
 

 I would appreciate if you have any idea about this situation and you could share it with me.
 

 Thanks in advance.

---

### Post by sidzen on 2013-01-18
Here's something I put together some time ago for a website.  Original sources are noted. Look to the second section for what you may need.  Hope it helps!
-----------------------------------------------------------------------------------------------------------------------------------
#########################################################################################################
BOTH of these Methodologies are performed at the Terminal or CLI -- where the real power of GNU/Linux is!
#########################################################################################################

SIMPLE METHOD (USB stick is functional; will destroy all existing data replacing it with your ISO)

1. Download your chosen distro ISO file, noting the path (i.e. /home/username/Downloads/)

2. Insert your USB stick and learn how your USB stick is recognized by the system, enter the command:

    sudo ls -l /dev/disk/by-id/*usb*

   This should produce output along the lines of:

    lrwxrwxrwx 1 root root  9 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0
    -> ../../sdb
    lrwxrwxrwx 1 root root 10 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0-
    part1 -> ../../sdb1

3. Unmount the usb stick  (NOTE: replace the X in sdX with whatever was returned in the first line
   from command above)

    sudo umount /dev/sdX

4. Use this command to write (as root) the image iso to your USB stick:

    sudo dd if=/path/to/your/distro.iso of=/dev/sdX bs=4M;sync


All being well, you should now have a bootable USB stick of your chosen distro.
#########################################################################################################

COMPLEX METHOD    (USB stick corrupted/need to make it recognizable again/desire a bootable distro 
        installed on a USB stick previously formatted to NTFS)

1. Download your chosen distro ISO file, noting the path (i.e. /home/username/Downloads/)

2. Physically uninstall/unplug all other USB devices from the computer and do not use a USB hub.

3. Insert your USB stick and learn how your USB stick is recognized by the system (as #2 above)

4. sudo umount /dev/sdX

5. dd if=/dev/zero of=/dev/sdX bs=512 conv=notrunc,sync

    NOTE:     this will both wipe your entire USB drive with zeros, destroy all existing data
        and TAKE A WHILE!
        
6. Partitioning and Formatting your USB Drive with cfdisk as a single partition using FAT32
    NOTE:     Please refer to [http://manual.aptosid.com/en/part-cfdisk-en.htm](http://manual.aptosid.com/en/part-cfdisk-en.htm)

    cfdisk /dev/sdX

    A. Delete all existing partitions using arrow keys to highlight each -- 

    "d" or "Delete" <Enter>

    B. Create a new partition

    "n" or "New"     <Enter>    choose     "Primary Partition"
                    NOTE: "Units" (MB)-- entire USB drive        <Enter>
    "t" or "Type"     <Enter>       "    "0B" (FAT32)                      <Enter>
    "b" or "Boot"    <Enter>    "    NOTE: toggle until "Boot" flag remains visible
    "W" or "Write"  <Enter>    "     NOTE: if you don't do this you'll have to start over!
    "q" or "Quit"   <Enter>
    
        Your newly partitioned USB stick is now recognized as sdX (usually sdb)
        and your new partition on the stick is now recognized as sdX1 (usually sdb1)

    C. Still at the joyous prompt, Format the newly partitioned USB drive!

    fdisk /dev/sdX

    mkfs -t vfat /dev/sdX1

7. Now, perform #3 and #4 of the SIMPLE METHOD, and you are done!    

    
#########################################################################################################    

SOURCES:    [http://manual.aptosid.com/en/part-cfdisk-en.htm](http://manual.aptosid.com/en/part-cfdisk-en.htm)
        [http://crunchbanglinux.org/wiki/statler_usb_installation](http://crunchbanglinux.org/wiki/statler_usb_installation)

---

### Post by mehrdad_v on 2013-01-18
Hi Sidzen,

Thank you for the great guide, but unfortunately this method didn't work.
Here is what happened in each steps:

```
root@mehrdad-XPS:~# ls -l /dev/disk/by-id/*usb*
lrwxrwxrwx 1 root root 9 Jan 18 13:55 /dev/disk/by-id/usb-Corsair_Voyager_GT_3.0_1111800000000137-0:0 -> ../../sdc
```

```
root@mehrdad-XPS:~# umount /dev/sdc
umount: /dev/sdc: not mounted
```

```
root@mehrdad-XPS:~# dd if=/dev/zero of=/dev/sdc bs=512 conv=notrunc,sync
dd: opening `/dev/sdc': No such device or address
```

and also I get FATAL Error when in try to use cfdisk
```
root@mehrdad-XPS:~# cfdisk /dev/sdc
FATAL ERROR: Cannot open disk
Press any key to exit cfdisk
```

again thank you and I look forward to hearing from you soon :)

---

### Post by sidzen on 2013-01-19
It's unfortunate the files seen while on wife's laptop are not known.  Which version is it running?  Yeh, it's probably that your Corsair is toast, especially with the weird name seen after Step2.

I'll look into it one more time, but so far prospect is not good!

---

### Post by mehrdad_v on 2013-01-19
Yeah it is!
which version of what do you mean?
anyway, I'll give you some of my system's info maybe it covers your question.
That Windows was 7 and I use Kubuntu 12.04 64bit.
dd (coreutils) 8.13
cfdisk (util-linux 2.20.1)

Thanks again and have a FAB weekend :)

---

### Post by sidzen on 2013-01-20
I must be brain-dead this weekend, but did you try <cfdisk sdc1?> in command line as root?  I used cfdisk on an unresponsive Kingston DT 100 G2 and managed to get a partition -- /dev/sdb1 .  I then used the dd command < dd if=/dev/zero of=/dev/sdb1 bs=1024 conv=notrunc,sync > to write zeros to it.   Thirdly, went to gparted to see the black-outlined unknown partition, deleted it, created a new partition table, created a new partition of entire USB and formtted it to ext2, rebooted to see if it was recognized (it was), then was able to use it again.

---

