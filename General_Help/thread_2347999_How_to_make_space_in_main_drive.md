---
title: "How to make space in main drive?"
date: 2016-12-30
forum: General Help
---

### Post by javierdl on 2016-12-30
Some of you (SeijiSensei, halogen2, etc) may find this post familiar.
Turns out, I started with one thread, then 2, then 3, each with a different question, but ultimately with the same purpose. Next thing I know, it all got tangled and overwhelming.
So I figured I would backtrack and try to group all the effort in here.
Here are the relevant threads (not in any particular order), so you may refer to any of these threads in your replies:
**[Can I have more than one owner for one mount point?]("https://ubuntuforums.org/showthread.php?t=2347324")**

**[Move a directory from one mount point to another]("https://ubuntuforums.org/showthread.php?t=2182174")**

**[Can I have more than one owner for one mount point?]("https://ubuntuforums.org/showthread.php?t=2347324")**

**[Moving /home to another drive]("https://ubuntuforums.org/showthread.php?t=2343317")**

**[Can I have more than one owner for one mount point?]("https://ubuntuforums.org/showthread.php?t=2347324")**


> device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat             (not mounted)  D45B-1044
/dev/sda2  vfat             (not mounted)  5968-2E1F
/dev/sda3  ext4    Partition_377 /media/nelly/Partition_377 1cc33a38-c617-4e9e-acf4-19c79415609e
/dev/sda4  swap             (not mounted)  e863d0f6-0ab2-4f1f-9fa3-55a652b02283
/dev/sda5  ext4             /mnt/steam-nelly 3ff8f52b-26d0-415f-b890-9ed186c00c5b
/dev/sdb1  vfat             /boot/efi      A023-0678
/dev/sdb2  ext4             (not mounted)  fb4b6aab-3aa9-4f22-ac08-957d3765f525
/dev/sdb3  ntfs             (not mounted)  01D21F5BB33EFBA0
/dev/sdb4  ntfs    Win10    (not mounted)  7B637EED5EAE730B
/dev/sdb6  ext4             /              649ff9fc-1a34-4427-9ca4-9310bff5963a
/dev/sdb7  swap             [SWAP]         db1e3a9e-cd9d-48de-8e42-e674b4fdb699
/dev/sdb8  ext4             /home          1c6d2b39-7de5-4e00-a7d4-7e237fb789f8
/dev/sdc1  ntfs    TOSHIBA  /media/javier/TOSHIBA A46CE4BB6CE488FE




sdb - This is where I have Ubuntu, home, most programs. Except for Steam games.

[IMG]https://sites.google.com/site/javierwebfolio/temp/home_location.png[/IMG]

sda - This is where I have more space. I thought of moving things to sda3 (Partition_377).

[IMG]https://sites.google.com/site/javierwebfolio/temp/new_home.png[/IMG]

One concern I have about moving /home to sda3, is that presently if I was the last user accessing sda3, then the next user won't have access to it, unless he/she unmounts it first, then mounts it. So my concern is: once home is there, will we be denied access, then we'll have to unmount it and mount it back? That would be a drag...

Assuming that won't be a problem, then as I recall, the next step will be to boot up from a Live USB, so that no system files will be open/running, then I'll be able to rsync home with this commands:
> cd /
sudo rsync home oldhome
sudo mkdir home
sudo mount /dev/sdb1 home



Am I in the right path so far?

Thanks guys :)

---

### Post by QIII on 2016-12-30
It is best to have one subject per thread to avoid confusion.

Please continue to work on your issues individually in the original threads.

Thanks.

Closed.

---

