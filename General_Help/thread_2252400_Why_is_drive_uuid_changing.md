---
title: "Why is drive uuid changing?"
date: 2014-11-11
forum: General Help
---

### Post by sim085 on 2014-11-11
Hello, I have a 400GB drive. Which I format to ext4 and updated fstab to mount under /media/backup. Last time I did this the uuid of the drive was "872eda8c-2190-4517-8917-afdbfa7a9775". There was an electrical failure and when I turned computer on it did not want to boot with a message that /media/backup was still not ready. When I went to check the uuid of the drive it had changed to "872eda8c-2180-4507-8907-afcbfa6a9765". The last part has changed! 

Does anyone know why this happens?

---

### Post by sim085 on 2014-11-11
When I am trying to manually mount the drive I get the following message:


mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I therefore deleted the partition. Re-created it. Format to ext4. However when I try to mount I still get that message!

---

### Post by rbmorse on 2014-11-11
When you formatted the drive, the UUID changed again.  Did you update the FSTAB?

---

### Post by sim085 on 2014-11-12
> **rbmorse said:**
> When you formatted the drive, the UUID changed again.  Did you update the FSTAB?

Yes I did. I now am seeing something else strange. I decided to run dd command on the whole drive to make sure there is no partition data on some part of the drive which is messing things up. That said dd is running really slow. The drive specs says the transfer rate of this drive is 133 MB/s. DD is reporting 5.6 MB/s! At this rate it will take a day to run through the whole drive! Last time I had done this I do not remember it took so long. Here is dd output. Each entry is spaced by 5 minutes.

```

194581188608 bytes (195 GB) copied, 34553.9 s, 5.6 MB/s
47807757+0 records in
47807757+0 records out
195820572672 bytes (196 GB) copied, 34853.9 s, 5.6 MB/s
48110321+0 records in
48110321+0 records out
197059874816 bytes (197 GB) copied, 35153.9 s, 5.6 MB/s
48412966+0 records in
48412966+0 records out

```

---

