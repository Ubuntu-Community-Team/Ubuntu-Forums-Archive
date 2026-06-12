---
title: "Grub rescue error"
date: 2016-06-11
forum: General Help
---

### Post by Mista_Petroz on 2016-06-11
my ubuntu launches to grub rescue screen and i am stuck :(

here is the boot repair log created by boot-repair [http://paste.ubuntu.com/17198446/](http://paste.ubuntu.com/17198446/)

---

### Post by oldfred on 2016-06-11
At the top is says it cannot mount sda2, but partition table list says it is Linux.
And grub is trying to boot from sda2, but then cannot see it.

If you used ext4 for format, you can run fsck to try to repair it.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda2
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda2

---

