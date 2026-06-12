---
title: "Unable to configure an additional kernel"
date: 2023-04-17
forum: General Help
---

### Post by kabirgandhiok on 2023-04-17
Hi,

I had updated the kernel to 5.19 from 5.15 LTS on 22.04 a while ago and I must have autoremoved the LTS kernel at the time. Now I would like to reinstall the LTS kernel so I installed it manually. 
```

sudo apt install linux-image 5.15.0-69-generic linux-headers 5.15.0-69-generic
sudo update-grub
sudo update-initramfs -u -k -all

```

But still when I reboot and select 5.15 from the grub menu I get dropped to the shell with these errors:
```

gave up waiting for suspend / resume device
cannot find suspend / resume device
cannot find /boot device
UUID **** does not exist
dropping to shell

initramfs: 

```

At this point I don't know what else to do. Kernel 5.15 cannot find /dev/sda2 on which the system is installed and in the same partition I have the swapfile.

```

&#10095; cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=06f74d6b-2319-4026-9731-7cbc5022260e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7427-4DAB  /boot/efi       vfat    umask=0077      0       1

/swapfile none swap sw 0 0

```

The solutions I have seen on google thus far suggest removing swap info and then updating grub or removing the UUID from grub. 
Is there a way to get kernel 5.15 detect /dev/sda2 and the resume / suspend device without altering the partitions or swapfile? On kernel 5.19 the system works just fine, I would just like to have an additional LTS kernel to choose from.

Thanks for helping.

---

### Post by kabirgandhiok on 2023-04-18
Thanks for your suggestions, but the issue still persists. I tried updating initramfs the way you suggested and thereafter grub but I got the same error on boot with 5.15

The kernel parameters already have the resume-UUID and resume-offset parameters in it, so I don't understand why I need to add it manually, it's already there.

Reinstalling 5.15 didn't fix it either.

The exact error I get when booting with 5.15
```

Gave up waiting for suspend/resume device
Gave up waiting for root file system device. Common problems:
 - Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=<the uuid number> does not exist. Dropping to a shell!
(initramfs) _

```

The UUID is the id for /dev/sda2 on which the entire system and the swapfile is located. 

Thanks!

---

### Post by Bashing-om on 2023-04-18
kabirgandhiok; Hey ..

How about we take this approach - verify the config file(s) for correct UUIDs.
```

sudo blkid -c /dev/null -o list ##to know what the kernel sees as the swap UUID
less /etc/initramfs-tools/conf.d/resume
less /etc/fstab ##UUID agrees with what blkid reports ?
sudo dmsetup status ##see if there are encrypted partitions

```

see then what there is to do.

[INDENT]all in the process
[/INDENT]

---

### Post by kabirgandhiok on 2023-04-19
Hey Bashing-om, here's the information you'd asked to check:

```

&#10095; dpkg --list | grep linux-image
ii  linux-image-5.15.0-70-generic              5.15.0-70.77                             amd64        Signed kernel image generic
rc  linux-image-5.19.0-32-generic              5.19.0-32.33~22.04.1                     amd64        Signed kernel image generic
rc  linux-image-5.19.0-35-generic              5.19.0-35.36~22.04.1                     amd64        Signed kernel image generic
ii  linux-image-5.19.0-38-generic              5.19.0-38.39~22.04.1                     amd64        Signed kernel image generic
ii  linux-image-5.19.0-40-generic              5.19.0-40.41~22.04.1                     amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04              5.19.0.40.41~22.04.13                    amd64        Generic Linux kernel image
rc  linux-image-unsigned-5.15.0-70-generic     5.15.0-70.77                             amd64        Linux kernel image for version 5.15.0 on 64 bit x86 SMP

&#10095; sudo blkid -c /dev/null -o list
[sudo] password for kabir: 
device                              fs_type       label          mount point                             UUID
----------------------------------------------------------------------------------------------------------------------------------------------
/dev/loop1                          squashfs                     /snap/canonical-livepatch/202           
/dev/loop19                         squashfs                     /snap/core20/1822                       
/dev/loop27                         squashfs                     /snap/starship/2675                     
/dev/loop17                         squashfs                     /snap/gtk-common-themes/1535            
/dev/loop8                          squashfs                     /snap/gnome-3-34-1804/90                
/dev/loop25                         squashfs                     /snap/snapd-desktop-integration/57      
/dev/loop15                         squashfs                     /snap/snapd/18596                       
/dev/loop6                          squashfs                     /snap/firefox/2559                      
/dev/loop23                         squashfs                     /snap/core18/2714                       
/dev/loop13                         squashfs                     /snap/mailspring/522                    
/dev/loop4                          squashfs                     /snap/core22/583                        
/dev/loop21                         squashfs                     /snap/pycharm-community/327             
/dev/loop11                         squashfs                     /snap/gnome-42-2204/87                  
/dev/loop2                          squashfs                     /snap/core18/2721                       
/dev/loop0                          squashfs                     /snap/canonical-livepatch/196           
/dev/loop28                         squashfs                     /snap/vlc/3078                          
/dev/loop18                         squashfs                     /snap/gnome-3-38-2004/119               
/dev/loop9                          squashfs                     /snap/gnome-3-38-2004/137               
/dev/loop26                         squashfs                     /snap/starship/2670                     
/dev/loop16                         squashfs                     /snap/snap-store/638                    
/dev/loop7                          squashfs                     /snap/firefox/2579                      
/dev/loop24                         squashfs                     /snap/core/14946                        
/dev/sda2                           ext4                         /                                       06f74d6b-2319-4026-9731-7cbc5022260e
/dev/sda1                           vfat                         /boot/efi                               7427-4DAB
/dev/loop14                         squashfs                     /snap/bare/5                            
/dev/loop5                          squashfs                     /snap/core22/607                        
/dev/loop22                         squashfs                     /snap/snapd-desktop-integration/49      
/dev/loop12                         squashfs                     /snap/intellij-idea-community/427       
/dev/loop3                          squashfs                     /snap/core20/1852                       
/dev/loop20                         squashfs                     /snap/snapd/18933                       
/dev/loop10                         squashfs                     /snap/gnome-42-2204/68  

&#10095; less /etc/initramfs-tools/conf.d/resume
/etc/initramfs-tools/conf.d/resume: No such file or directory

&#10095; less /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=06f74d6b-2319-4026-9731-7cbc5022260e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7427-4DAB  /boot/efi       vfat    umask=0077      0       1

/swapfile none swap sw 0 0
/etc/fstab (END)

&#10095; sudo dmsetup status
No devices found


```

I hope this helps.

Thanks!

---

### Post by coffeecat on 2023-04-19
@kabirgandhiok, the person who replied to your first post, and who you responded to is not a person at all, just the copy-pasted output from an AI bot. As such the post has been removed from public view and the account has been dealt with in line with our rules. Sorry for the inconvenience. Bashing-om, on the other hand, is a real human being, a valued member of our forum, and gives good advice! Good luck with finding a solution to your problem.

---

### Post by kabirgandhiok on 2023-04-19
> **coffeecat said:**
> @kabirgandhiok, the person who replied to your first post, and who you responded to is not a person at all, just the copy-pasted output from an AI bot. As such the post has been removed from public view and the account has been dealt with in line with our rules. Sorry for the inconvenience. Bashing-om, on the other hand, is a real human being, a valued member of our forum, and gives good advice! Good luck with finding a solution to your problem.

thanks for letting me know @coffeecat

---

### Post by Bashing-om on 2023-04-19
kabirgandhiok; Well ...

What we now know is that you have a swap file instead of that old legacy swap partition. Not having the resume file is not a factor :D
And encryption also - not a factor.

You show that you have the HardWare Enablement (HWE) installed: "ii  linux-image-generic-hwe-22.04 " with the latest HWE kernel.
Now as you do not have  "linux-image-generic" you will be unable to pull in the Generally Available kernels: as in "5.15.0-69-generic" (.70 os the latest version).

As you show HWE as installed ... what then is the need to install the 5.15  series kernels ?

Before we proceed - no big deal to install linux-image-generic - what kernel are you presently booting?

Please post back:
```

uname -r

```

Depending on what you want to do is what we next do.

[INDENT]it's Ubuntu
[INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by kabirgandhiok on 2023-04-19
oh! so if I install linux-generic-image will I be able to keep both HWE and LTS kernels or will doing so result in package conflicts? The reason I wanted to have both is just in case something works better on the LTS kernel and as a backup kernel.

So far I have been using 5.19 and it is working just fine.
```

&#10095; uname -r
5.19.0-40-generic

```

Thanks!

---

### Post by Bashing-om on 2023-04-19
kabirgandhiok; Yepper

You can run both - just keep a close eye on your /boot/ partition (UEFI) that you do not run short of space.

However - I did miss lead just a tad ... it is " linux-generic " that is the meta package !
```

sudo apt install linux-generic
sudo apt update
sudo apt upgrade

```
where I do expect linux-image-generic and linux-headers-generic will also be pulled in as dependencies.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by kabirgandhiok on 2023-04-20
Thanks so much for helping me out with this, @Bashing-om. For now I think I'm going to stick with 5.19, I'm a little concerned about running out of space and package conflicts. I think I will first try this out on a virtual machine.

---

### Post by Bashing-om on 2023-04-20
kabirgandhiok :D

Glad to be of service - in the event that you do continue with the GA kernel availability, the package manager -in this case - will insure there are no conflicts. These kernels will happily co-exist.

[INDENT]just keep on keep'n on
[/INDENT]

---

