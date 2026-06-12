---
title: "OS does not boot with LVM and custom kernel initramfs"
date: 2013-08-26
forum: General Help
---

### Post by unimatrixdoc2 on 2013-08-26
**Q.**The problem is on boot grub doesn't fully start the OS. Theelement that appears to be the problem is LVM. Thekernel can not see the root partition.Why am I doing this: I need to build a custom kernel fromkernel.org for some video drivers to work. **Just need someone to pointme in the right direction** to get grub2 and LVM to get working. **The hand-off is the issue.** Fyi: no RAID is being used.


_Steps Taken_:


**I.** I have placed the boot partition outside of the LVM.
I have three partitions: 
```
$ fdisk -l /dev/sda
   Device Boot      Start         End     Blocks   Id  System
/dev/sda1   *        2048      499711     248832   83  Linux
/dev/sda2          501758   976771071  488134657    5  Extended
/dev/sda5          501760   976771071  488134656   8e  Linux LVM


$ ls -la /dev/mapper/*root
lrwxrwxrwx  1 root root       7 Aug 2514:55 ubuntu--vg-root -> ../dm-0

```

***Everything with the stock Ubuntukernel works great.***
***And pvdisplay, vgdisplay,lvdisplay list all the correct stuff.***


**I****I.** The kernel successfully compiled. I set all entries under RAID and LVM (makemenuconfig) to be compiled into the kernel. The initramfs was createdby:


```
$ mkinitramfs -o initramfscustom.img 3.10.9custom

```

I have looked at its contents by:


```
$ gzip -cd initramfscustom.img | cpio-i

```

and then compaired to the initrd.img made by the OS under /boot/initrd*.img
They look the same.


When I use an initramfs and boot the custom kernel the last message on the screen was:
```
    loading essential drives
    running /scripts/init-premount
    mounting root file system BeginRunning /scripts/local-top

```

***I then get a command prompt. I did as it suggested and:***
***$ ls /dev/mapper***
***It only had “control” in it.***
***The hard drive was visible and listed /dev/sda* successfully***
***blkid only listed two entriesverses the twelve that should be listed.***
***After trying: pvdisplay,vgdisplay, lvdisplay nothing was listed.***


**I****II.** Here is my custom grub makemenu:


```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to addcustom menu entries.  Simply type the
# menu entries you want to add afterthis comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "CUSTOM KERNEL" {
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
insmod lvm
#insmod drivemap
#search --no-floppy --fs-uuid--set=root 0eb601a7-bb1c-45f9-82d2-7a9eafaed858 
#search --no-floppy --fs-uuid--set=root 1fd96981-5145-4144-8ba5-e34eda532e85 
if [ x$feature_platform_search_hint =xy ]; then
  search --no-floppy --fs-uuid--set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1--hint-baremetal=ahci0,msdos1  0eb601a7-bb1c-45f9-82d2-7a9eafaed858
else
  search --no-floppy --fs-uuid--set=root 0eb601a7-bb1c-45f9-82d2-7a9eafaed858
fi
set root='hd0,msdos1'
#linux /customkernelroot=/dev/ubuntu-vg/root ro radeon.audio=1
#linux /customkernelroot=/dev/mapper/ubuntu--vg-root ro radeon.audio=1
linux /customkernelroot=UUID=1fd96981-5145-4144-8ba5-e34eda532e85 ro radeon.audio=1$vt_handoff
initrd /initramfscustom.img
}

```

As you can see I've tried several variations...


_System Info_:


```
$ uname -a
Linux xen 3.8.0-30-generic #44-UbuntuSMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
$ lspci | grep SATA
00:1f.2 SATA controller: IntelCorporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller(rev 05)

```



_Misc Links_:


(1) [https://wiki.ubuntu.com/Kernel](https://wiki.ubuntu.com/Kernel)
(2) [KernelCustomBuild- Ubuntu Wiki]("https://wiki.kubuntu.org/KernelCustomBuild")
(3) [Initramfs- Ubuntu Wiki]("https://wiki.ubuntu.com/Initramfs")
(4) [Grub2/Troubleshooting- Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2/Troubleshooting")
(5) [GNUGRUB – Documentation]("http://www.gnu.org/software/grub/grub-documentation.html")

---

### Post by unimatrixdoc2 on 2013-08-29
I forgot to include the Ubuntu bug I'm trying to work around:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/859101](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/859101)

---

### Post by unimatrixdoc2 on 2013-08-29
here is a vimdiff .config comparison. left is Ubuntu and right is my custom:

CONFIG_MD=y                                               |  CONFIG_MD=y                                                                       
  CONFIG_BLK_DEV_MD=y                                 |  CONFIG_BLK_DEV_MD=y                                                               
  CONFIG_MD_AUTODETECT=y                            |  CONFIG_MD_AUTODETECT=y                                                            
  CONFIG_MD_LINEAR=m                                   |  CONFIG_MD_LINEAR=y                                                                
  CONFIG_MD_RAID0=m                                    |  CONFIG_MD_RAID0=y                                                                 
  CONFIG_MD_RAID1=m                                    |  CONFIG_MD_RAID1=y                                                                 
  CONFIG_MD_RAID10=m                                  |  CONFIG_MD_RAID10=y                                                                
  CONFIG_MD_RAID456=m                                |  CONFIG_MD_RAID456=y                                                               
  # CONFIG_MULTICORE_RAID456 is not set         |  CONFIG_MD_MULTIPATH=y                                                             
  CONFIG_MD_MULTIPATH=m                            |  CONFIG_MD_FAULTY=y                                                                
  CONFIG_MD_FAULTY=m                                  |  CONFIG_BCACHE=y                                                                   
  ----------------------------------------------------------------------------------|  # CONFIG_BCACHE_DEBUG is not set                                                  
  ----------------------------------------------------------------------------------|  # CONFIG_BCACHE_EDEBUG is not set                                                 
  ----------------------------------------------------------------------------------|  # CONFIG_BCACHE_CLOSURES_DEBUG is not set                                         
  CONFIG_BLK_DEV_DM=y                                 |  CONFIG_BLK_DEV_DM=y                                                               
  # CONFIG_DM_DEBUG is not set                       |  CONFIG_DM_DEBUG=y                                                                 
  CONFIG_DM_BUFIO=m                                    |  CONFIG_DM_BUFIO=y                                                                 
  CONFIG_DM_BIO_PRISON=m                           |  CONFIG_DM_BIO_PRISON=y                                                            
  CONFIG_DM_PERSISTENT_DATA=m                  |  CONFIG_DM_PERSISTENT_DATA=y                                                       
  CONFIG_DM_CRYPT=m                                    |  CONFIG_DM_CRYPT=y                                                                 
  CONFIG_DM_SNAPSHOT=m                              |  CONFIG_DM_SNAPSHOT=y                                                              
  CONFIG_DM_THIN_PROVISIONING=m                |  CONFIG_DM_THIN_PROVISIONING=y                                                     
  # CONFIG_DM_DEBUG_BLOCK_STACK_TRACING is not set                 |  CONFIG_DM_DEBUG_BLOCK_STACK_TRACING=y                                             
  CONFIG_DM_MIRROR=m                                 |  # CONFIG_DM_CACHE is not set                                                      
  CONFIG_DM_RAID=m                                     |  CONFIG_DM_MIRROR=y                                                                
  CONFIG_DM_LOG_USERSPACE=m                    |  CONFIG_DM_RAID=y                                                                  
  CONFIG_DM_ZERO=m                                      |  CONFIG_DM_LOG_USERSPACE=y                                                         
  CONFIG_DM_MULTIPATH=m                             |  CONFIG_DM_ZERO=y                                                                  
  CONFIG_DM_MULTIPATH_QL=m                       |  CONFIG_DM_MULTIPATH=y                                                             
  CONFIG_DM_MULTIPATH_ST=m                       |  CONFIG_DM_MULTIPATH_QL=y                                                          
  CONFIG_DM_DELAY=m                                    |  CONFIG_DM_MULTIPATH_ST=y                                                          
  ----------------------------------------------------------------------------------|  CONFIG_DM_DELAY=y                                                                 
  CONFIG_DM_UEVENT=y                                   |  CONFIG_DM_UEVENT=y                                                                
  CONFIG_DM_FLAKEY=m                                   |  CONFIG_DM_FLAKEY=y                                                                
  CONFIG_DM_VERITY=m                                   |  CONFIG_DM_VERITY=y


left: /boot/config-
right: /usr/src/linux/.config

---

### Post by unimatrixdoc2 on 2013-08-29
here is my current kernel.org custom .config file.

---

