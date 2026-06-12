---
title: "Some questions on LVM"
date: 2012-10-16
forum: General Help
---

### Post by blenderfox on 2012-10-16
I have a couple of questions on LVM and wondered if anyone here could assist me.

Firstly, why would you use a LVM disk instead of a static partitioning? From what limited usage I have had of LVM it is really unintuitive to maintain and size.

Secondly, I have installed linux in a VirtualBox VM to experiment with the LVM and have a 15GB drive (hey, it is only an experimental machine) with two partitions, sda1, sda2. sda1 is the boot partition and sda2 is a partition which takes up the rest of the disk, and is a LVM containing a swap partition and root partition (maps to /). I have fours scenarios I would like to understand.

For the first scenario, I want to reduce the LVM to, say, 5GB, so I have room to put another partition at the end of it - for sake of argument a Windows partition, or another Linux install. So I would have:

sda1 (boot partition)
sda2 (LVM partition)
sda3 (new partition - windows, new linux, etc.)

For the second scenario, I take the original layout (without the sda3 partition) and dump it (image and restore) onto a new hard drive, with a bigger disk size, for example, 30GB. Since the image only had data up to 15GB, the LVM will only go up to 15GB. How do I resize the LVM to make use of the new space, and can I split the new space, putting some of the space into the swap, and some on the root? Can I also put some of the space into a new LVM partition within the group, and mount that? For example, putting the /home directory as a separate partition. e.g.:

sda1 (boot partition)
sda2 (LVM partition)
|--- lvm_root (maps to /)
|--- lvm_swap (swap space)
\--- lvm_home (maps to /home)

For the third scenario, I want to add to the above configuration and have the homespace of a user (or users), for example, /home/encrypteduser mapping to a space which is *encrypted*, maybe using LUKS or similar. Something like the below.

sda1 (boot partition)
sda2 (LVM partition)
|--- lvm_root (maps to /)
|--- lvm_swap (swap space)
|--- lvm_home (maps to /home)
\--- lvm_encrypted_home (encrypted space, maps to /home/encrypteduser)

For the fourth scenario, let us assume my LVM has a swap file at the *end* of the group and I want to move it to the beginning of the group, and optionally, increase the size of the space from 1G to 4G, e.g.:

sda1 (boot partition)
sda2 (LVM partition)
|-- lvm_root (maps to /)
\-- lvm_swap (swap space, 1G)

to 

sda1 (boot partition)
sda2 (LVM partition)
|-- lvm_swap (swap space, 4G)
\-- lvm_root (maps to /)

I know it is a lot of questions, but I have been hunting around looking for LVM tutorials and none of them seemed to make sense.

Many thanks for any comments or help on this topic.

---

