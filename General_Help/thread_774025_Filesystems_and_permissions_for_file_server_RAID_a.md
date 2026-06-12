---
title: "Filesystems and permissions for file server RAID array"
date: 2008-04-29
forum: General Help
---

### Post by wjrogers on 2008-04-29
My freshly-upgraded ubuntu 8.04 machine has three hard drives in it: a 250 GB drive for the system itself and two 750 GB drives. My plan is to make the two big drives into a RAID1 array for shared network storage, including media and backups, accessible to both Windows and Linux machines on the network. Last night, I figured out how to use mdadm to create the RAID1 array on /dev/md0. Now I have a few questions about fiddly problems that I'm unsure how to solve.

1. What is the best file system to use? I don't know too much about modern file systems; I just have a vague idea that ext3 is a reliable workhorse and ReiserFS is fast for large numbers of small files. Should I stick with ext3, or is there a better option?

2. I'm planning to use the mount options "rw,auto,nodev,noexec,noatime" for the /dev/md0 fstab entry, is that good? Any suggestions?

3. How do I solve the permissions problem? After I mount /dev/md0 on /mnt/fileserver, I can "sudo chmod a+w /mnt/fileserver" but then I am still stuck with the problem that newly created files are owned by the user who created them, with the usual only-I-can-write permissions. This is supposed to be shared storage, so anyone can read or write any file on the disk. I want it to act like the file system does not track permissions at all, which I guess is functionally equivalent to all files always being set a+rw. What's the "right" way to set this up?

---

