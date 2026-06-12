---
title: "How to get permission to edit other partitions?"
date: 2008-06-13
forum: General Help
---

### Post by rivalslayer on 2008-06-13
I have dual boot Hardy Heron, with Windows XP SP3. And I also have a Philips GoGear MP3 player which can be used as a USB key. My 100 GB HDD has 7 parts, 6 FAT32 and one Ext3 for Ubuntu. Ubuntu mounts the other partitions for me, but I cannot edit them by default, I need to use terminal and su command for that. And I cannot edit the Philips Mp3 player contents. Can I modify settings to get some permission to edit the mounted partitions? If I can then how?

Please help.

Need it!
:confused:

---

### Post by Zorael on 2008-06-13
I'm not sure I understand, but it may just be an issue of you not having write permissions on the mount directory. Failing that, you may have to edit your /etc/fstab and make sure it's set to allow non-root users to write to the partitions. This is often the case with FAT32 partitions, where you can/need to manually set the umask (chmod numeric permissions) to allow writing, as well as perhaps define which user/group "owns" it (uid). See [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) for more information.

As for the mount directory permissions, I just generally leave it to be owned by root but let its group affinity be set to my user's group. Then I set the permissions to 775, allowing the owner and the owner's group full permissions (7), and other users read and execute permissions (5). That way I can write to it, but I can't remove the directory and mess stuff up. Obviously, if you have several users and you want to limit write permissions to a certain few, just create a new group and add those users to it. Then change the mount folder's group affiliation to that new group.

This likely does nothing if the FAT32 settings in /etc/fstab are set incorrectly, but it shouldn't be harder than that for ext3 partitions, as long as the fstab hasn't got them defined without the rw option (which is default). Again, see that forum post as well as the man page for mount ([http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)) for hints.

---

