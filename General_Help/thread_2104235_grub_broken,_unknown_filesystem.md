---
title: "grub broken, unknown filesystem"
date: 2013-01-12
forum: General Help
---

### Post by gloww on 2013-01-12
Hez Guys,

first time i need to ask for help in an Ubuntu forum.
Today my Ubuntu crashed while i was starting Virtualbox. I also did a small apt upgrade.
After poweroff restart i was greated by Grub telling me that it doesnt know my filesystem and couldnt boot. I loaded a live cd and installed boot repair and startet it. it couldnt repair it. here is the boot info script it created. It seems my filesystem is broken.

[http://paste.ubuntu.com/1524249/](http://paste.ubuntu.com/1524249/)

What can i do? What can it be? any ideas?
I also have problems to boot the filesystem...

---

### Post by oldfred on 2013-01-12
I would try this:
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1


Do you really have a 1TB drive formatted as one partition with FAT32? If you think fsck will take a while try chkdsk on sdf.  FAT32 is ok for small partitions, primarily camera cards or similar.
       
 NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by gloww on 2013-01-12
Thanks a lot. that solved it totaly. i was so in panic i forgot about e2fsck. Thanks  so much.
After repairing i again had to repair the boot sector. But then it worked like nothing happend. thanks!

---

