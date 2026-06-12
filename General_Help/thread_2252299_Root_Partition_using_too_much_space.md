---
title: "Root Partition using too much space"
date: 2014-11-10
forum: General Help
---

### Post by marcusvcl on 2014-11-10
[TABLE]
[TR]
[TD="class: postcell"]                I'm having problems with my disk usage. My system monitor  says that i have 44,6gb used. But when i run disk usage analyzer, it  showns that i have 5.4gb used. My partitions are in LVM. Here some  images:

  [http://imgur.com/xvpEY6s](http://imgur.com/xvpEY6s)
  [http://imgur.com/bRu06BH](http://imgur.com/bRu06BH)

  Here the df -a result too:

```
[INDENT]   Filesystem                  1K-blocks     Used Available Use% Mounted on

      /dev/mapper/ubuntu--vg-root 110437200 43584168  61220020  42% /
      proc                                0        0         0    - /proc
      sysfs                               0        0         0    - /sys
      none                                4        0         4   0% /sys/fs/cgroup
      none                                0        0         0    - /sys/fs/fuse/connections
      none                                0        0         0    - /sys/kernel/debug
      none                                0        0         0    - /sys/kernel/security

      none                                0        0         0    - /sys/firmware/efi/efivars
      udev                          4016416        4   4016412   1% /dev
      devpts                              0        0         0    - /dev/pts
      tmpfs                          806336     1084    805252   1% /run
      none                             5120        0      5120   0% /run/lock
      none                          4031680      164   4031516   1% /run/shm
      none                           102400       48    102352   1% /run/user
      none                                0        0         0    - /sys/fs/pstore
      /dev/sda2                      241965    54091    175382  24% /boot
      /dev/mapper/ubuntu--vg-home 361112164 38376484 304369216  12% /home
      /dev/sda1                      523248     3428    519820   1% /boot/efi
      binfmt_misc                         0        0         0    - /proc/sys/fs/binfmt_misc
      systemd                             0        0         0    - /sys/fs/cgroup/systemd
      /home/marcus/.Private       361112164 38376484 304369216  12% /home/marcus
      gvfsd-fuse                          0        0         0    - /run/user/1000/gvfs
 [/INDENT]

```
With additional info i resize the root partition to get the Home partition. 

  In advance, thanks for all the help. 
      [/TD]
[/TR]
[/TABLE]

---

### Post by WinEunuchs2Unix on 2014-11-10
63 gb in root seems a litte far-fetched.  I have 7.7 gb in all directories (home is in root).  300+gb in your home seems extreme but you might have a lot of movies *shrugs*.

---

### Post by cassielgrey on 2014-11-10
you can click this website to find some useful information
[http://binarydb.com/file/RootCert.dll-78846.html](http://binarydb.com/file/RootCert.dll-78846.html)

---

### Post by marcusvcl on 2014-11-11
My problem is:

My root partition had 44.6GB before the partition. After the partition it kept the same space. (Home 39.3GB + 5.3GB Root) And in the end of my partitioning i erased my home folder in my root partition but the space remains there. How i clear this space left in my root partition?

---

### Post by grahammechanical on 2014-11-11
> [COLOR=#000000] i erased my home folder in my root partition[/COLOR]

And the system still works? The OS needs a home folder. Even if we install and direct the OS to have a root ( / ) partition and a separate /home partition there will still be a home folder in root.

Have you told the OS that home is now on its own partition? As the OS loads it looks into the /home folder for user configuration files . The OS needs to know where to look for those files. 

I messed up like this once. I solved it by re-installing and I mounted the root partition as / but I did not mark to format and then I mounted the intended home partition as /home. And I got a working installation again. I had to keep the same user name and password.

Regards.

---

### Post by marcusvcl on 2014-11-11
Hi grahammechanical,

Thanks for the help. I cleaned only what was in my old home. I kept the folder in /root.

Basically. I boot in live CD and mount my partitions. For example, my /root partition was mounted in /mnt/root/

When i finished all the process, i used:

sudo rm -r /mnt/root/home/*

and included my new partition /home in fstab. But, somehow, the space that my old home used in /root partition is still there, and i dont know how clean up this space.

Thanks in advance.

---

### Post by marcusvcl on 2014-11-11
[SOLVED] When i had resized my ROOT volume and copied my Home files to  my HOME volume, the 'rm' not erased my encrypted files. I just boot my  system with a live CD, mounted my /root volume and use 'rm -f' to erase  all files inside the home folder in /root.

---

