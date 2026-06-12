---
title: "Error Messages"
date: 2019-11-27
forum: General Help
---

### Post by daniell59 on 2019-11-27
I can no longer boot into ubuntu. I have Ubuntu 16.04 on one hard drive and 18.04 on another one. For some reasons they both stopped working at about the same time. I only get messages on the screen that I am not familiar with. I am now online using a flash drive. I am impressed on how well it works. I attached an image in the hope that somebody can give me insight into this problem

Thanks

---

### Post by tors on 2019-11-27
Scary! Hope things will get alright!

Looks like someone has had the same problem,
[https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually](https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually)

From what I gather from that post,
you need to do a filesystem check by executing the following command at that prompt:

**fsck /dev/sda1**

I have not encountered this problem before, so feel free to read up on this a bit more before executing...

---

### Post by oldfred on 2019-11-27
I would do a full fsck on all your ext4 partitions.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required. First command should not ask for yes/y on anything.        
  Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 
    
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

It also looks like you need UEFI/BIOS updates if available. You show spectre issue.

Both Windows & Ubuntu have updated kernel & drivers.
      
 Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

Besure you know settings you changed in UEFI as update resets to defaults. I used to take photos, but my new UEFI system lists changes, so I save that data.

---

### Post by daniell59 on 2019-11-27
My system is very old. The hard drives must be more than 10 years old. Is it possible that I am experiencing hard drive issues? Soon I will be building a new machine with a ubuntu windows dual boot. Still I would like to know what is going on.

---

### Post by oldfred on 2019-11-27
You can check drive status & run tests with Smart Status.

       In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status 
    
I only know if good/bad or pass/fail.

---

### Post by daniell59 on 2019-11-27
Because of my limited Knowledge, I did the only thing that I could think of. I reinstalled Ubuntu 16.04 into the same hard drive. All seems well. I would greatly appreciate it if somebody could explain to me what happened.

---

### Post by oldfred on 2019-11-27
Without having info from before the re-install, it is now difficult to know what happened.
Always best to run Boot-repair and post link to its summary report. That gives lots of detail. I run it just to document my system.

       Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2019-11-28
Broken harddrives are possible, but it's not very likely both hard drives fail at the same time. Still, both systems may use the same boot loader on the same hard drive. It could also be a loose connector, a bad power supply, ...

---

