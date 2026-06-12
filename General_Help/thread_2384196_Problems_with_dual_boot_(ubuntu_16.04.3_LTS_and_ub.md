---
title: "Problems with dual boot (ubuntu 16.04.3 LTS and ubuntu 17.10)"
date: 2018-02-03
forum: General Help
---

### Post by jjer on 2018-02-03
Hi, 

I succesfully installed Ubuntu 16.04.3 LTS (as OS1 in below table) a few days ago. The plan was also to have Ubuntu 17.10 (as OS2) alongside Ubuntu 16.04.3. 
Today I installed Ubuntu 17.10 (as OS number 2) alongside the Ubuntu 16.04.3 LTS and ran into trouble. 

I have tried to run boot-repair from a USB, without much success. 

Problem is: 
- I can only boot Ubuntu 16.04.3 LTS into terminal window as root. 
- I cannot boot into Ubuntu 17.10. 
- Boot repair says I must select "sda1/EFI/Ubuntu/shimx64.efi" when booting. I cannot find this entry/file in the list of boot options. 

See [http://paste.ubuntu.com/26514041/](http://paste.ubuntu.com/26514041/) where boot-repair has placed it's report. 

The plan is as following:
Ubuntu 16.04.3 LTS will have / at /dev/sda6, /boot at /dev/sda2, and /home at /dev/sdb7 (and it seemed to work before I installed Ubuntu 17.10). 
And Ubuntu 17.10 should have / at /dev/sda7, /boot at /dev/sda3 and /home at /dev/sdb8. 
I planned to put the boot loaders for both at /dev/sda1. 
See more details in the below table: 
```
###############################################################
# SSD disk, type: Kingston, size: 120 034 MB, device: /sda
#  Device:     Type:   Name:  P/L: Size:  OS:  OS mount path
#  ----------- ------- ------ ---- ----------- ---- ----------------- 
#  /dev/sda1   efi     efi1   P        768 MB  1&2  /mnt/efi1
#  /dev/sda2   ext2    boot   P      1 024 MB   1   /boot
#  /dev/sda3   ext2    boot2  P      1 024 MB   2   /mnt/os2/boot2
#  /dev/sda4   swap    swap   L     16 384 MB   1    n/a
#  /dev/sda5   swap    swap   L      8 192 MB   2    n/a
#  /dev/sda6   ext4    root   L     62 899 MB   1   /
#  /dev/sda7   ext4    root2  L     29 741 MB   2   /mnt/os2/root2
###############################################################
# HD disk, type: ? , størrelse: 2 000 398 MB, device: /sdb
#  Device:     Type:   Name:  P/L: Size:  OS:  OS mount path
#  ----------- ------- ------ ---- ----------- ---- ----------------- 
#  /dev/sdb1   efi     efi2   P        768 MB   3   /mnt/efi2
#  /dev/sdb2   ext2    boot3  P      1 024 MB   3   /mnt/os3/boot3
#  /dev/sdb3   ext4    opt    L    150 050 MB   1   /opt
#  /dev/sdb4   ext4    opt2   L    150 050 MB   2   /mnt/os2/opt2
#  /dev/sdb5   ext4    var    L     50 050 MB   1   /var
#  /dev/sdb6   ext4    var2   L     25 050 MB   2   /mnt/os2/var2
#  /dev/sdb7   ext4    home   L  1 014 049 MB   1   /home
#  /dev/sdb8   ext4    home2  L     50 049 MB   2   /home2
#  /dev/sdb9   ext4    git    L    350 050 MB  1&2  /mnt/git
#  /dev/sdb10  ext4    root3  L    200 050 MB   3   /mnt/os3/root3
#  /dev/sdb11  ext4    spare  L      9 207 MB  any  /mnt/spare
###############################################################

```
I am grateful of any help to repair my system. 
Best regards, jjer

---

### Post by jjer on 2018-02-03
Hi again, 
I have now managed to boot into Ubuntu 17.10 after issuing the following command as root in Ubuntu 16.04.3 LTS terminal window: "update-grub". 
I have now run boot-repair's "boot info summary" tool again [http://paste.ubuntu.com/26514675/](http://paste.ubuntu.com/26514675/)

Now I hope anyone can give me a hint on how to enable booting into Ubuntu 16.04.3 LTS into the graphical user interface. 
I can boot into terminal text interface as root in Ubuntu 16.04.3 LTS. 
It seems that most of the partitions are mounted in Ubuntu 16.04.3.1 LTS (except /dev/sda7, /dev/sdb4, /dev/sdb6 and /dev/sdb8 for the newly installed Ubuntu 17.10 where the partition UUIDs seem to have changed according to /etc/fstab vs blkid comparisson).  
This is strange: To me it seems that the trouble is that Ubuntu 16.04.3 LTS doesn't want to boot into the Graphical User Interface anymore? 

Should boot with the "Ubuntu 16.04.3 LTS installation DVD" and try to repair "Ubuntu 16.04.3 LTS"?  

Thanks again and best regards, 
jjer

---

### Post by oldfred on 2018-02-03
You have made it very complicated when it does not need to be.

Generally desktops do not need separate partitions or you just need / (root).
If one install and newer user you can add /home as a separate partition.
Or if you want to multiple install, better to add a shared data partition which you then can mount in each install.

You cannot share /boot or you get conflicts and maybe one system overwrites boot files of the other.
You can share swap as long as not hibernating & hibernation not recommended. Ubuntu boots fast enough without hibernation.

You do have UEFI install on gpt partition drives and have both drives as gpt.

Note I do not yet have both drives fully allocated. And some are now old installs which I will reuse with another newer install.

```
fred@Z170N:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4 bionic  bionic      25.4G e1e5879e-1828-4a1c-806c-b29c426ccc34 
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8 yakkety yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 
```

---

### Post by jjer on 2018-02-03
Hi Oldfred, 
Thanks for your reply. I know it is very complicated :) I guess it was fun using the partition tool adding /var, /opt and so on. 

Still, I guess I would have run into the same trouble with only /boot /home and / for each OS?  The reason I want two separate OSes is keep one software tool in 17.10 that always mess up the other settings for other programs. I am afraid of sharing /home between multiple Ubuntu OSes, as Ubuntu seems to be very sensitive to accidental modifications of configuration files.   

It seems to me now that it is Ubuntu 16.04.3 LTS graphical user interface setup that has been "damaged". Perhaps something in the boot process of Ubuntu 16.04.3 LTS was modified? Now, when booting into Ubuntu 16.04.3 LTS, I end up as root in a full screen text terminal window. The UUIDs of the partitions used by Ubuntu 17.10 are also changed in Ubuntu 16.04.3 LTS.

Should I re-install Ubuntu Desktop?  [COLOR=#111111][FONT=Consolas]sudo apt install ubuntu-desktop[/FONT][/COLOR]

---

### Post by oldfred on 2018-02-03
I think that is because some partition was reused and you now have conflicts.
Reinstall of desktop will not resolve UUID issues.
While Boot-Repair will find & mount a separate /boot, it does not look for other system partitions which may be needed to repair a system as not normally used with desktops and those that do have separate system partition know how to chroot into system, mount all the required partitions and make repairs.

I really suggest starting over with two / (root) partition, the ESP, swap for 16.04 as later versions will use swap file unless you already have a swap partition.
Then you can have a large data partition.
That avoids the issues of maintaining each system partitions use and then its size.

---

### Post by jjer on 2018-02-03
Hi again, 
The problem is solved by updating the UUID values for partitions in /etc/fstab (that was used during installation of Ubuntu 17.10).
The UUID values in the /etc/fstab file (of Ubuntu 16.04.3 LTS) that was the cause of the problems, because they changed values when I installed Ubuntu 17.10 alongside the existing Ubuntu 16.04.3 LTS. 
Thanks for your help.

---

### Post by jjer on 2018-02-04
Last comment: 
Ubuntu 16.04.3 LTS booted up with no wireless or wired connection (while working OK in Ubuntu 17.10). 
Solution to this problem was to recreate the symbolic link for /etc/resolv.conf as described in [this answer]("https://askubuntu.com/a/622493"). 
I hope everything is OK now. 
Thanks again.

---

