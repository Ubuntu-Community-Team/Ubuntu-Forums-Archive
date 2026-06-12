---
title: "Problems booting Ubuntu after update"
date: 2018-02-02
forum: General Help
---

### Post by olls2 on 2018-02-02
My Xubuntu installation is failing to boot after it crashed during an update.

Grub is loading in shell mode, and when I manually boot Xubuntu - using the following commands - it starts to boot before hanging.

```

grub> set root=(hd2,gpt4)
grub> linux /vmlinuz root=/dev/sda1
grub> initrd /initrd.img
grub> boot

```

I can see several errors in in the boot saying "no such file or directory", starting with:  ```
  mounting /dev on /root/dev failed: No such file or directory  
```

I booted with a live USB and all the partitions seem to be fine, but I'm not that experienced with Linux internals.  Any help would be very much appreciated!

---

### Post by oldfred on 2018-02-02
Often after a crash you have to run fsck to repair filesystem, before you can start to figure out why it crashed in first place.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by olls2 on 2018-02-02
I ran the fsck commands, the output seems to suggest no problems.

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb4
                                                                               
      987032 inodes used (23.58%, out of 4186112)
         296 non-contiguous files (0.0%)
         621 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 933912/103
    10590304 blocks used (63.12%, out of 16777216)
           0 bad blocks
           1 large file

      841403 regular files
       86546 directories
          55 character device files
          25 block device files
           0 fifos
          44 links
       58987 symbolic links (52922 fast symbolic links)
           7 sockets
------------
      987067 files
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb4
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      987032 inodes used (23.58%, out of 4186112)
         296 non-contiguous files (0.0%)
         621 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 933912/103
    10590304 blocks used (63.12%, out of 16777216)
           0 bad blocks
           1 large file

      841403 regular files
       86546 directories
          55 character device files
          25 block device files
           0 fifos
          44 links
       58987 symbolic links (52922 fast symbolic links)
           7 sockets
------------
      987067 files
ubuntu@ubuntu:~$ 

```


And the Boot Info:  [http://paste.ubuntu.com/26509565/](http://paste.ubuntu.com/26509565/)

---

### Post by olls2 on 2018-02-02
Nothing seems obviously broken in the outputs of those command as far as I can tell. 

sdb4 is the partition with the Xubuntu installation on, sda1 contains my home directory.

---

### Post by oldfred on 2018-02-02
Can you boot with this, a one line version?
       configfile (hd0,gpt4)/boot/grub/grub.cfg 

Your grub in the ESP does not look correct, missing last line?

```
 search.fs_uuid 3fff4fd5-c92c-426f-8abe-5054088e8bb7 root hd1,gpt4 
set prefix=($root)'/boot/grub' 

   
```
This is mine where install is in sda2.
```
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg 
```

Or as Boot-Repair says  you should reboot Ubuntu live installer in UEFI boot mode and run repairs from that.
You may need to fully reinstall grub. 
But you many just need to manually edit /EFI/ubuntu/grub.cfg to add the configfile line like mine.

Did you at some point swap drives or add a new drive that became sda? Grub with UEFI used to only install to ESP on drive seen as sda. And I have tried multiple times, even with version in 18.04 and it only wants to install to sda drive.

---

### Post by olls2 on 2018-02-02
Ah-ha, "configfile (hd1,gpt4)/boot/grub/grub.cfg" worked and booted my install.  It took a while to boot but that might be an unrelated problem, I think it has been slow for a while.

Adding the configfile line to the grub.cfg seems to be working too :)
I'm not sure I understand what that line is doing, is it not referencing the same file which it is in?

Thank you so much for your help! :D
I would be reinstalling from scratch otherwise!

---

### Post by olls2 on 2018-02-02
All seems good now, thanks again!

I re-started the software update, and it seemed to resume at a grub-efi- package, which is probably why the line was missing from the config file.  I'm not sure what caused the crash in the first place.

I did mess around with the drives a bit when I set up my home drive, I can't remember exactly what I did though.

---

