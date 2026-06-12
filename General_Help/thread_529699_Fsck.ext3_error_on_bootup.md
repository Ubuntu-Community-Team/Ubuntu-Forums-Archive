---
title: "Fsck.ext3 error on bootup"
date: 2007-08-19
forum: General Help
---

### Post by jd_k on 2007-08-19
This morning when I attempted to boot into Gentoo, I received the "fsck.ext3: no such file" error (followed by the "the superblock could not be read or does not describe a correct ext2 filesystem" message). It gives me the option of entering a root password (doing so gives me full read access to all of my partitions) or pressing Control+D to reboot.

My /etc/fstab file is properly configured to mount /dev/mapper/nvidia_dcfceeei1 -- and had been working properly doing so for a week or two. My hard drive setup involves a RAID1 array (two drives, partitioned); the /dev/mapper/nvidia_dcfceeei1 partition is the linux partition.

The computer boots fine off a LiveCD; it detects my drives just fine and all my files are properly intact. As soon as I try to boot normally, I get the error message again.

Also, when the error message offers me a shell, I can access my files on the root partition by just browsing the filesystem (/, /home, etc.), but I cannot mount any of the other partitions because the devices don't show up in /dev/mapper. In fact, nvidia_dcfceeei1 doesn't show up in /dev/mapper either, so I'm not sure how it is apparently mounted (read-only) when the boot error kicks me out to the shell prompt.

I booted into Windows to post this message, but I am not in the habit of using Windows except for the occasional game, and would like to get the issue addressed so I can go back to usage. What have I done wrong? How can I fix it?

If there is a thread that speaks to my particular situation, I apologize for missing it; please point me in the right direction. Thank you for your time.

---

