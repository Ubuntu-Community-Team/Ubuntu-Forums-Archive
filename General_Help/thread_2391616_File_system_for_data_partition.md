---
title: "File system for data partition"
date: 2018-05-11
forum: General Help
---

### Post by bvargo on 2018-05-11
Background 500 GB disk in a Dell laptop.  Came with Windows 10 installed.  Dual boot w/16.04.  Preparing to migrate to 18.04.
Previous partition setup (ignoring Windows rescue disk and swap) is 50/50 NTFS and ext4.
Current partition setup 50% NTFS, 25 GB ext 4 for /, and the balance in ext4 in an LVM with "/home" and "/library" (for multi-media storage) partitions.
In thinking about this, if I want to access this from Windows, it seems fairly obvious that I won't be able to use LVM to use the /library partition normally with Windows (even with e.g. a [utility like this]("https://sourceforge.net/projects/ext2read/")).

So, what I am thinking is to eliminate the LVM partition (regrettably) and make actual partitions for /home and /library.  This brings me to my question of what should these partitions be formatted to?

From what I can tell, I can delete my swap partition, merge it with another partition and just use a swap file.  For 18.04, accessing ext4 from Windows apparently poses a significant problem so would it make the most sense to put /library on NTFS so both OSs can access it?  I would also like to be able to access /home from Windows, but I could just define the location of "Documents" to be somewhere on the NTFS /library partition and deal with exceptions on a case-by-case basis.  I guess I'm specifically concerned about why ext4 would generally be preferable and what drawbacks there are to using NTFS over a journaling system.

---

### Post by SeijiSensei on 2018-05-11
The value of using ext4 is that it uses native *nix primitives like users, groups, and permissions.  In general it's always preferable to use native *nix filesystems on *nix systems.

You could format the /library partition as NTFS, create a Documents directory there, then create a symlink to it under /home/username.

---

### Post by oldfred on 2018-05-11
NTFS is also a journaling format.

With Windows 10 you must have its fast start up off. It keeps all NTFS partitions hibernated and then the Linux NTFS driver will not mount it. And Windows updates may turn fast start up back on. If you cannot boot Windows or access a NTFS partition that is the first thing to check.

I had both a /mnt/data as Linux format and /mnt/shared as NTFS when I still had XP years ago. But have migrated all data to my ext4 data partition. My /home has only user configuration in it. Even some normally hidden folders like Firefox & Thunderbird are in my data partitions. In fact, those were the first two folders I shared with XP, so I could still use same bookmarks & email in XP & Ubuntu.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by HermanAB on 2018-05-11
Windows only supports two file systems: NTFS and ReFS.  
(No, that other thing is not really a file system.)

If you need to share a partition with Windows, then you should use NTFS, since ReFS support is not in the repos yet.

However, if you are adventurous:
[https://www.paragon-software.com/home/refs-linux/](https://www.paragon-software.com/home/refs-linux/)

---

### Post by bvargo on 2018-05-12
Thanks!  This is a good start.  When you say fast boot off does this mean that I cannot use sleep (which I do a lot) at all?  Can I use hibernate if I plan on going back to Windows after and not trying to use grub2 to let me into ubuntu w/o disturbing my hibernated session?  I need to be able to use Office for a few more months and then after that, I doubt I'll be going into Windows much.  I can consider migrating the /library data partition back to ext4 if the problem with it, Windows 10, and Ubuntu 18.04 gets sorted out.

---

### Post by oldfred on 2018-05-12
You will not be able to mount a shared NTFS partition if hibernate is on.
And if you have it in fstab, system may not boot as it then cannot mount the hibernated NTFS partition.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by bvargo on 2018-06-21
Thanks for the help.  I got it working.

---

