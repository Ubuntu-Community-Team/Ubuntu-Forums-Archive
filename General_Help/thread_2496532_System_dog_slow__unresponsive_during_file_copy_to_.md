---
title: "System dog slow / unresponsive during file copy to USB"
date: 2024-04-02
forum: General Help
---

### Post by bsh on 2024-04-02
Hey guys,
I have a xubuntu file server with several hard disks in it, and I'm making regular backups to external USB3 hard drive, transferring single huge file onto it (~130GB). While this is running, the system becomes almost unresponsive: can hardly open files or even just browse them, web servers running on the system do not respond and time out or just dead slow, etc. I have seen reports of this but haven't find a solution yet.
What I don't understand is: the drives are independent from the system disk and from each other, and there are many cpu cores as well, why does one slow disk operation chokes the entire system? Is there just one io queue or pipeline for the entire system? Can this not be paralleled?
[IMG]https://i.imgur.com/H4SJ41Q.png[/IMG]

---

### Post by TheFu on 2024-04-02
USB queuing has always had issues on Linux.
The work around is to 

a) run the tasks with **ionice** - to allow other processes time to get their IO handled.
```
IONICE(1)                        User Commands                       IONICE(1)

NAME
       ionice - set or get process I/O scheduling class and priority

```

b) run the tasks when the system isn't busy - say overnight - like most people do for backups

c) use a tool that supports limiting the speed of the transfers so other tasks get CPU/IO time slices - I think **rsync** can do this, but local **rsync** behaves different than remote rsync, which I 100% know works using the **--bwlimit** option.
```
       --bwlimit=RATE           limit socket I/O bandwidth
```

If you are backing up a full VM image file, I'd strongly encourage you to use a different backup method. It won't get better and it prevents fast backups using diffs. Around 2010, I was backing up about 20 VMs by doing the entire image file. Completing them all was taking over 8 hrs, which was the total time my bosses said I could have for backups.  I reworked the backups in 2010 and since then, backing up each VM is usually under 3 minutes, thanks for built-in versioning.  Now I treat each VM like a physical machine when it comes to backups and I completely ignore the VM-ness involved.

Have you checked the system logs yet?  I was copying a file a few minutes ago and it never finished.  Looked in the logs to see this:
```
[914843.345384] sd 1:0:0:0: [sda] tag#3 CDB: Read(16) 88 00 00 00 00 02 ca 48 24 00 00 00 04 00 00 00
[914843.345385] blk_update_request: I/O error, dev sda, sector 11983660032 op 0x0:(READ) flags 0x80700 phys_seg 128 prio class 0
[914843.345400] ata2: EH complete
```
Not looking too good for that file.  Appears at least 1 sector has just failed at a really bad time.  I just deleted the input file that is used to create the output file.  The disk involved is less than 1 yr old and has a 5 yr warranty.  I'm not thrilled having to move everything off it, but that's better than losing any important data.  Tonight, the monthly long SMART test is scheduled to run, so in the morning, I'll have a report waiting. I run weekly "short" SMART tests and during the first week of a new month, I run a "long" SMART test.
```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      5832         -
# 2  Short offline       Completed without error       00%      5664         -
# 3  Short offline       Completed without error       00%      5497         -
# 4  Extended offline    Completed without error       00%      5342         -
# 5  Short offline       Completed without error       00%      5162         -
# 6  Short offline       Completed without error       00%      4995         -
# 7  Short offline       Completed without error       00%      4827         -
# 8  Extended offline    Completed without error       00%      4670         -
# 9  Short offline       Completed without error       00%      4491         -
#10  Short offline       Completed without error       00%      4323         -
#11  Short offline       Completed without error       00%      4155         -
#12  Short offline       Completed without error       00%      3988         -
```
As you can see, I forgot to add this specific disk to the processing for the first 4000 hrs of use. We all make mistakes or forget things.

---

### Post by HermanAB on 2024-04-03
As mentioned above, ionice is one of the fixes for this problem:
ionice -c 3 cp /foo/largefile /bar

Rsync is another possibility:
rsync -av --bwlimit=100 --progress /foo/largefile /bar

---

