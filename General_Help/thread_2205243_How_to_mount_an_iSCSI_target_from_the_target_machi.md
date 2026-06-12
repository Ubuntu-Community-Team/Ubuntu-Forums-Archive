---
title: "How to mount an iSCSI target from the target machine?"
date: 2014-02-12
forum: General Help
---

### Post by gmoore777 on 2014-02-12
[64-bit PrecisePangolin on both machines.]

I created an iSCSI target on machine #1.
I can connect from an iSCSI client machine, machine #2
and can write files (backups) from machine #2 to machine #1, and I can see
these files from machine #2.
So everything is perfect in this client/server relationship.

Let's assume machine#2, catches on fire and is destroyed.
No problem, my backups are on machine #1. Right?

But, I can't seem to successfully Google, nor figure out, how
to access/mount these files that are sitting on machine #1 from machine#1.
How does one do that?
(don't suggest that I get a machine #3 and turn that into an iSCSI client machine)

I tried this on machine #1:
    sudo mount  -type  ext4  /dev/md2  /mnt

        mount: Wrong fstype, bad option, bad superblock on /dev/md2
        missing codepage or helper program or other error

/dev/md2 represents a RAID segment on machine #1.
It is mapped to these partitions /dev/sda3 and /dev/sdb3.

From machine #2, /dev/md2 is the remote iSCSI target that machine #2
is connected to. Machine #2 views this iSCSI target as an empty "local" device.
(/dev/sdb) 
From Machine #2, I had created a partition on this "local" raw device,
formated it as ext4, and created a filesystem on it and copied
my backups to it. (this is the part that is working perfectly.)

But how do I see these files while sitting on machine #1?

---

### Post by gmoore777 on 2014-02-12
Another way to state the problem:

Since machine #2 ran an `fdisk` against this iSCSI target, 
thus creating a partition table (MBR?) at the beginning of this "partition",
on machine #1, I need to tell the `mount` command, 
"hey, mount this device /dev/md2, but skip ahead 512 bytes 
 before trying to figure out how to mount this partition".

I did a `man mount` but there are no options for ext2/3/4
that says to skip the first n-bytes.

There is a "reserved=value" mount option for the "affs" file system
which is the Number of unused blocks at the start of the device, but
nothing like that for ext2/3/4.

Does this information help anyone?

---

### Post by gmoore777 on 2014-02-13
Note to self:
I read that it's not a good idea to install the iSCSI initiator on the iSCSI target machine, but
until I find a different solution, I have to at least try this.

I install the iSCSI initiator on the iSCSI target machine:
    sudo apt-get install open-iscsi

I do NOT edit /etc/iscsi/iscsid.conf because I don't want this service
to start up automatically; only manually.

Interesting that `fdisk -l` now sees that /dev/md2 has a partition table
and a partition, supposedly named /dev/md2p1:

Disk /dev/md2: 95.9 GB, 95860686848 bytes
/dev/md2p1            2048   187227903    93612928   83  Linux

(and the values for /dev/md2p1 do match the fdisk output
 from the iSCSI client/initiator machine. so the intiator
 running on the target machine, is reading the partition table
 correctly on /dev/md2)

I run discovery and it finds my one iSCSI target:
      `sudo iscsiadm --mode discovery --type=sendtargets --portal=192.168.0.103`
192.168.0.103:3260,1 iqn.2014-10.net.comcast.bee005:raid.dev.md2

I restart the iSCSI initiator, just for the heck of it:
`sudo service open-iscsi restart`
 * Disconnecting iSCSI targets  [ OK ] 
 * Stopping iSCSI initiator service [ OK ] 
 * Starting iSCSI initiator service iscsid [ OK ] 
 * Setting up iSCSI targets      [ OK ]   

But the big problem, is that I cannot `mount` that partition:

$ sudo mount -v --types ext4 --read-only /dev/md2p1 /mnt
mount: special device /dev/md2p1 does not exist

It is true that the directory "/dev/md2p1" does not exist,
but fdisk thinks it does.

So, I'm getting closer to my solution.
I at least have at least one program, `fdisk` that can
somewhat see that /dev/md2 is not merely a partition,
but a raw device, with an MBR on it, and can read the partition
table on that MBR and assigns it the name of /dev/md2p1.


But, I'm still in the same boat, I can't mount this partition,
in order to view the files that are in it.

---

### Post by gmoore777 on 2014-02-13
Well, I rebooted the iSCSI target machine, mostly to see if it would
boot up after mucking with it for so long.
Well, success!
I can now mount that iSCSI target ( a partition-inside-of-a-partition) with:

    `sudo mount /dev/md2p1 /mnt`

and I can drill down and find my backups that I made from the real 
iSCSI intitiator machine, and was able to access my files and play a SpeedRacer audio file.

So now I feel at ease, that when my iSCSI initiator machine catches on fire,
that my backups that are on the iSCSI target machine are retrievable from
the very same iSCSI target machine.
I don't need to get a 3rd machine and set it up as an iSCSI intitiator machine,
in order to retrieve my backups. Especially since my notes to do all of this
are only found in my backups.

[Solved]

---

