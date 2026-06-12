---
title: "USB solid state drive seen with df but not blkid?"
date: 2024-04-11
forum: General Help
---

### Post by leejenon on 2024-04-11
istributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

Hi,

I have formatted a 2TB Seagate flash drive with EXT4 on this Ubuntu system. I then was looking for the UUID so I could mound it on start-up. Although the drive listed here -

 ```
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           777M  1.9M  775M   1% /run
/dev/sda2       117G   13G   98G  12% /
tmpfs           3.8G  4.0K  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
efivarfs        128K   82K   42K  67% /sys/firmware/efi/efivars
/dev/sda1       511M  6.1M  505M   2% /boot/efi
tmpfs           777M  1.7M  776M   1% /run/user/1000
**/dev/sdb1       1.8T   28K  1.7T   1% /media/plex/plexmedia**

```

.. it's not listed here..

plex@Mini-PC:~$ blkid
/dev/sda2: UUID="d87e6127-ab9a-43b7-9d54-c1f749ebfb30" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="d2312185-a19b-4e1a-add5-9bb2c7900996"

Any ideas? Thanks Lee

---

### Post by leejenon on 2024-04-11
I used sudo blkid

Works now. :)

---

