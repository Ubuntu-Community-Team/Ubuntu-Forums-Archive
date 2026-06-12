---
title: "Creating raid1 array"
date: 2019-02-07
forum: General Help
---

### Post by fewjr on 2019-02-07
Hello,
     I have reinstalled Ubuntu Server 18.04.1. I installed to a 120GB ssd drive. I have 4 2TB WD Red drives. The 4 drives are formatted gpt ext4, sdb1, sdc1, sdd1 & sde1. I am trying to make raid1 array with sdb & sdc. I unmounted the 2 drives before running the command but I get this error:

~$ sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
mdadm: super1.x cannot open /dev/sdb: Device or resource busy
mdadm: ddf: Cannot use /dev/sdb: Device or resource busy
mdadm: Cannot use /dev/sdb: It is busy
mdadm: cannot open /dev/sdb: Device or resource busy

     What is it I need to do to get this to go? Is the problem that the drives are already setup with partitions? Also, I am going to use this server as a Plex server for music,videos, photos. Not sure what else as I am getting somewhat confused by all the options. I didn't do any fancy partitioning with the boot drive. If I was to start over, what would be the best partitioning scheme for a server. I've seen where its been suggested to create separate /home 
and /var partitions among others. Would those partitions be on the raided drives or on the boot drive. I confused as to the best way to go about this. This is what I have now:

~$ lsblk --f
NAME             FSTYPE      LABEL         UUID                                   MOUNTPOINT
sda                                                                               
&#9492;&#9472;sda1           LVM2_member               sGF4xU-BpA0-2N1t-02AB-rr6K-1m8D-JegiOU 
  &#9500;&#9472;goblinservant--vg-root
  &#9474;              ext4                      d30d325e-0d4a-42ae-9a5b-6110494e4797   /
  &#9492;&#9472;goblinservant--vg-swap_1
                 swap                      38a1d7f5-55ae-4ae3-bbc4-fac41534c9e7   [SWAP]
sdb                                                                               
&#9492;&#9472;sdb1           ext4        datapartition cb5045a4-2c52-4ba8-a192-ca735306e943   /mnt/data
sdc                                                                               
&#9492;&#9472;sdc1           ext4        datapartition e4ec0889-b8eb-4bf6-9b2f-7c1d65111d44   /mnt/data
sdd                                                                               
&#9492;&#9472;sdd1           ext4        datapartition bdbb00c0-ca73-459a-8701-2ed7925a9b8a   /mnt/data
sde                                                                               
&#9492;&#9472;sde1           ext4        datapartition 17e95e25-56bd-4721-a0fe-cd10d335cbf4   /mnt/data
sr0                                                                   

Thank you

---

### Post by fewjr on 2019-02-07
Ran this too. Is it cause of type ee? It needs to be fd maybe?

~$ sudo mdadm --examine /dev/sdb /dev/sdc /dev/sdd /dev/sde/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)

---

### Post by fewjr on 2019-02-07
Well I posted all that and finally realized what I was doing wrong. I was trying to umount the drives instead of the partitions. I now have my raid1 using 2 drives.

~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc[1] sdb[0]
      1953382464 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  1.8% (36019648/1953382464) finish=262.4min speed=121734K/sec
      bitmap: 15/15 pages [60KB], 65536KB chunk

unused devices: <none>


and:

~$ sudo lsblk --f
NAME   FSTYPE  LABEL           UUID                                   MOUNTPOINT
sda                                                                   
&#9492;&#9472;sda1 LVM2_me                 sGF4xU-BpA0-2N1t-02AB-rr6K-1m8D-JegiOU 
  &#9500;&#9472;goblinservant--vg-root
  &#9474;    ext4                    d30d325e-0d4a-42ae-9a5b-6110494e4797   /
  &#9492;&#9472;goblinservant--vg-swap_1
       swap                    38a1d7f5-55ae-4ae3-bbc4-fac41534c9e7   [SWAP]
sdb    linux_r goblinservant:0 3719c546-fef1-3147-37c8-8bf5db72aa2e   
&#9492;&#9472;md0  ext4                    6e354ae6-a062-49da-889d-d623b6d2b6c8   /mnt/md0
sdc    linux_r goblinservant:0 3719c546-fef1-3147-37c8-8bf5db72aa2e   
&#9492;&#9472;md0  ext4                    6e354ae6-a062-49da-889d-d623b6d2b6c8   /mnt/md0
sdd                                                                   
&#9492;&#9472;sdd1 ext4    datapartition   bdbb00c0-ca73-459a-8701-2ed7925a9b8a   
sde                                                                   
&#9492;&#9472;sde1 ext4    datapartition   17e95e25-56bd-4721-a0fe-cd10d335cbf4   
sr0

---

### Post by fewjr on 2019-02-08
...but I'm still wondering what the best layout would be for my drives/partitions for the server as I said above. Would love some advise. I'm reading everything I can with work and family and all.
fewjr

---

### Post by fewjr on 2019-02-08
Bump

---

