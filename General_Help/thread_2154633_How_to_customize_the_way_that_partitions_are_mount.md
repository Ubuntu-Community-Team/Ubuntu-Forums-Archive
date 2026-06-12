---
title: "How to customize the way that partitions are mounted via dolphin file manager?"
date: 2013-06-15
forum: General Help
---

### Post by ljxfstorm on 2013-06-15
Recently I installed Paragon's ntfs and hfsplus driver  (ufsd)  for linux to obtain hfsplus journal read/write support(and maybe better perfomance for ntfs partitions :-) ).

It works well,I can mount a ntfs or hfsplus partiton via the following command:

sudo mount -t ufsd /dev/sda5 /mnt/sda5

Here comes the question,by default ntfs partitions are mount via ntfs-3g when i click on the ntfs partition in the dolphin file manager.How can I make the file manager mount a ntfs partition via paragon's driver by default?  And the same to hfsplus.

I learned that mounting a external partition via file manager is done by "udisks" ,can the way that udisks behaves be configured?

My system is Kubuntu 13.04 x86_64

---

### Post by kanhiya on 2013-11-19
HI, i am also having exactly the same problem. I banged my head for two days, no solution yet, only hope left is to customize udisk source code to work for you. I think this will not also help you.

I am not a programmer and couldn't guide you best. I am also looking for solution.
Take a look at below link
[http://ubuntuforums.org/showthread.php?t=1606193](http://ubuntuforums.org/showthread.php?t=1606193)
Read above link properly, and i think it has what we are looking for. I will also compile and see if there is any success. Keep trying for udev rules and udisk. These are the only things to concentrate and make a tutorial so that other users can get benefit from it.

---

### Post by VMC on 2013-11-19
@[ljxfstorm]("http://ubuntuforums.org/member.php?u=1831129"), You bring up an interesting topic. I didn't know about Paragon NTFS for Linux beore today. I've googled several benchmarks and they claim its much faster than ntfs-3g.

Here's one thread several years ago: [http://ubuntuforums.org/showthread.php?t=911135](http://ubuntuforums.org/showthread.php?t=911135)
I've checked some others also. I find cloneing any ntfs partition slower using clonezilla, and maybe Paragon would be the solution. In the above article Paragon says its free for home use.

---

