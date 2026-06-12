---
title: "Create Permission deny"
date: 2008-02-12
forum: General Help
---

### Post by billyyu on 2008-02-12
I have encounter a problem when I tried to acess one of my drive sda9. So I modified the /etc/fstab.

                          cfdisk (util-linux-ng 2.13)

                              Disk Drive: /dev/sda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   NTFS             []              20971.57*
                            Pri/Log   Free Space                           0.04*
    sda5        NC          Logical   NTFS             []              20971.53*
    sda6                    Logical   NTFS             []              26406.06*
                            Logical   Free Space                           2.91*
    sda9                    Logical   Linux ext3                        5173.71
    sda8                    Logical   Linux ext3                        5000.98
    sda7                    Logical   Linux swap / Solaris              1497.01

So I added the bold line into the file:# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=622e8c22-b8bb-40fe-972d-cdd1d3ffe50a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0E5461E65461D14F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=A261651970E985F1 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=00FB25EB8D680790 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=6be80f80-39e5-4190-bebc-9dfba5f593fc none            swap    sw              0       0
**/dev/sda9       /media/sda9     ext3    defaults,umask=007,gid=46       0       1**
/dev/sda6       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


But now I can see the sda9 in the /media directory, and can access to it. but can't create anything in this sda9, only root can, what should i do now?

---

### Post by taurus on 2008-02-12
I recommend you edit /etc/fstab and change it to look like this.

```
/dev/sda9   /media/sda9   ext3   defaults   0   1
```
Now, if you want to write to /media/sda9 without root privilege, just change the ownership of /media/sda9 from root to your login name, _assuming_ your login name is **billy**.

```
sudo chown -R **billy**:**billy** /media/sda9
ls -la /media
```
Reboot.

---

### Post by billyyu on 2008-02-12
Thanks, taurus. it works.

---

