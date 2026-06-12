---
title: "Help to extend sdb1 with existing free space"
date: 2020-02-28
forum: General Help
---

### Post by wiehan2 on 2020-02-28
Hi, hoping someone would guide me in extending a partition on ubuntu server.

The server is a VM. Space ran short on /dev/sdb1/. I've allocated more space to the drive on the VM side, but unsure how to extend sdb1 to utilize this space. Any guidance appreciated.

**df-h results:**
Filesystem                                            Size  Used Avail Use% Mounted on
udev                                                    1.9G     0  1.9G   0% /dev
tmpfs                                                   394M  824K  393M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv       14G  6.8G  6.4G  52% /
tmpfs                                                   2.0G     0  2.0G   0% /dev/shm
tmpfs                                                   5.0M     0  5.0M   0% /run/lock
tmpfs                                                   2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop0                                           92M   92M     0 100% /snap/core/8592
/dev/loop1                                           92M   92M     0 100% /snap/core/8689
/dev/sdb1                                            738G  648G   53G  93% /local
/dev/sda2                                            976M  145M  764M  16% /boot
/dev/sda1                                            511M  6.1M  505M   2% /boot/efi
tmpfs                                                  394M     0  394M   0% /run/user/1000

**fdisk -l  results show sdb to have 850GB available:                                                                                                                             **
Disk /dev/loop0: 91.3 MiB, 95748096 bytes, 187008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91.4 MiB, 95805440 bytes, 187120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 30 GiB, 32212254720 bytes, 62914560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EA0D8C73-C2EB-4658-BC75-E0FFE87272BE


Device       Start      End  Sectors  Size Type
/dev/sda1     2048  1050623  1048576  512M EFI System
/dev/sda2  1050624  3147775  2097152    1G Linux filesystem
/dev/sda3  3147776 62912511 59764736 28.5G Linux filesystem


GPT PMBR size mismatch (1572863999 != 1782579199) will be corrected by w(rite).
**Disk /dev/sdb: 850 GiB, 912680550400 bytes, 1782579200 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 85BD53EF-E9EE-4A57-B852-C6F568A194C3


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 1572861951 1572859904  750G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 14 GiB, 15032385536 bytes, 29360128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Any help appreciated.

---

### Post by CelticWarrior on 2020-02-28
I never did it in command line, I can't help you with that.

But if you're able to boot a desktop live session it could be easily done with Gparted.

---

### Post by wiehan2 on 2020-03-02
Thank you CW.

I would like to do it via cmd line and use it as a learning experience.

Any guidance anyone?

---

### Post by CatKiller on 2020-03-02
The non-graphical partition editor is [parted](https://www.gnu.org/software/parted/manual/parted.html). It's what GParted uses underneath.

---

### Post by wiehan2 on 2020-03-03
Thank you CatKiller, could you possibly give me some guidance on how to achieve the end goal. Working with partitions is quite risky business and Linux isn't my first language, I would hate to break the system. Any and all help is greatly appreciated.

---

### Post by CatKiller on 2020-03-03
Nope. As you say, it's a process that's fraught with peril, so I've only used GParted (and Partition Magic, way back when I used Windows) to edit the partitions. A graphical presentation of what you're doing before you do it is very comforting.

Looking at your output again, ```
/dev/mapper/ubuntu--vg-ubuntu--lv 14G 6.8G 6.4G 52% /
``` seems to show that you're using logical volumes rather than partitions, and I have no experience of that at all.

---

### Post by yancek on 2020-03-03
The standard methods/commands used to resize partitions will not work as indicated above.  You are using LVM so I would suggest you do an online search using those terms.  Accordingt to the link below, it appears to be doable with parted but I would advise reading any instructions carefully before beginning.  Part of the explanation at the site below discusses logical/extended partitions.  Ignore that as it doesn't apply to your system.

 [http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/](http://sirlagz.net/2016/01/20/live-resizing-lvm-on-linux/)

---

