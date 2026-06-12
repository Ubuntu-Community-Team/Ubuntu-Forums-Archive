---
title: "Copying speeds way too slow?"
date: 2013-02-08
forum: General Help
---

### Post by black3agl3 on 2013-02-08
Here is my /etc/fstab[B]

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=413586af-c889-4745-b869-04b357ea7f73 /               ext4    errors=remount-ro 0       1
/dev/sda3    /mnt/exthd    ntfs-3g    user,sync    0    0
# swap was on /dev/sda6 during installation
UUID=efa57a47-b476-43f7-9ca0-1a4d94e6d2ff none            swap    sw              0       0[/B]

Trying to move a 14 MB file from my ext4 partition to the /dev/sda3 partition takes around 5 minutes.

If I unmount the /dev/sda3 partition and sudo mount /dev/sda3 /mnt/exthd , the transfer takes around 2 seconds.

Is there some kind of problem with how I made the entry in /etc/fstab?

EDIT: For some reason I can't edit my profile details. I'm actually using ubuntu 12.10

---

### Post by thnewguy on 2013-02-08
The only difference between mounting manually or by using the entry in your fstab file would appear to be the presents of the "sync" option in your fstab file. What happens if you take that out? I'm fairly certain "sync" isn't a default parameter.

---

### Post by Impavidus on 2013-02-08
You can't change your profile because you've less than 25 posts.

The problem may be this:> 
**/dev/sda3    /mnt/exthd    ntfs-3g    user,[COLOR=Red]sync[/COLOR]    0    0**The entire file is copied at once. When not using sync, execution is delayed.

---

### Post by black3agl3 on 2013-02-08
So, when I cut and paste via GUI, the actual moving of the file is also delayed?

---

### Post by 3rdalbum on 2013-02-08
> **black3agl3 said:**
> So, when I cut and paste via GUI, the actual moving of the file is also delayed?

There are two factors at play here.

First, writing to NTFS drives is slower than writing to a drive with a native filesystem (such as ext4). This has always been the case, although it should be quicker than you describe.

If you remove the 'sync' parameter from fstab you will get faster copying. Sync copies one chunk from the source disk, puts it on the destination disk, then copies the next chunk, etc. Without sync, Linux will read as much from the source as it can, and SIMULTANEOUSLY write to the destination. A lot faster. Also, the "copy" operation appears to finish when the whole source file has been buffered, and the system continues writing to the destination in the background.

Sync is safer for people who forget to eject their USB drives before ripping them out of the USB port.

---

### Post by black3agl3 on 2013-02-09
Let's say I remove the whole entry from the fstab file, and I mount the partition via Nautilus, like somebody who does not know the existence of the fstab file. Is the partition mounted sync or async?


EDIT:
> mount the partition via NautilusBy this i mean clicking the appropriate partition under the **Devices** section in the left sidebar

---

### Post by sudodus on 2013-02-09
> **black3agl3 said:**
> Let's say I remove the whole entry from the fstab file, and I mount the partition via Nautilus, like somebody who does not know the existence of the fstab file. Is the partition mounted sync or async?


EDIT:
By this i mean clicking the appropriate partition under the **Devices** section in the left sidebar
'async' or buffering

You can run the command ```
sync
``` and wait for it to return to prompt (in the terminal window), to know that the write operation has finished. And after 'ejecting' you can check that the partition is no longer mounted with the command ```
df
```

---

### Post by black3agl3 on 2013-02-09
I see... I seems like im repeating myself but i would like to confirm two things:

1) Are partitions mounted sync or async in windows?
2) The main linux partition, the partition attached to **/** is also mounted async?

EDIT:
Three things actually...
The file transfer dialog shown when copying or moving files refers to the buffering process?

---

### Post by sudodus on 2013-02-09
> **black3agl3 said:**
> I see... I seems like im repeating myself but i would like to confirm two things:

1) Are partitions mounted sync or async in windows?
async, you need to 'click to remove safely' alias eject also in Windows> 
2) The main linux partition, the partition attached to **/** is also mounted async?
Yes, this is important to increase speed, and this is why ***you should not stop the computer the hard way*** pulling the plug (if a desktop) or pressing the on/off button 4 seconds (if a laptop). 
If the system is unresponsive (which happens seldom in Linux), try this sequence:

While pressing the hotkey combination
***alt + SysRq***
all the time, type the following letters slowly (one each second)
***r e i s u b***
> 
EDIT:
Three things actually...
The file transfer dialog shown when copying or moving files refers to the buffering process?
No, I don't think so. Even when that dialogue window has disappeared, writing may continue. Check with ```
sync
```

---

### Post by black3agl3 on 2013-02-09
> **sudodus said:**
> 
***alt + SysRq***
all the time, type the following letters slowly (one each second)
***r e i s u b***

SysRq is the Print Screen key? My keyboard does not show SysRq.

> 
No, I don't think so. Even when that dialogue window has disappeared, writing may continue. Check with ```
sync
```I did the following:
[remount cause the partition is currently mounted sync]
[B]sudo umount /dev/sda3 
sudo mount /dev/sda3 /mnt/exthd[/B]

Then I tried to copy a folder [/mnt/exthd/Projects/new/] of around 7 GB to [/mnt/exthd/new] so that i could get a file transfer dialog that would not disappear immediately.
The estimated time was 3 minutes.

I launched terminal and typed in **sync** followed by enter.
After around 5 seconds the sync command was done and i was returned to prompt.

The file transfer dialog was only 200 MB out of 7.1 GB done.

Now im kind of lost. Isn't sync supposed to make sure all file transfers are done? That's what i understood from your previous post and **man sync**.

---

### Post by Impavidus on 2013-02-09
> **black3agl3 said:**
> SysRq is the Print Screen key? My keyboard does not show SysRq.It varies. Often it's print screen, but on my HP laptop it's delete.

> 
I launched terminal and typed in **sync** followed by enter.
After around 5 seconds the sync command was done and i was returned to prompt.

The file transfer dialog was only 200 MB out of 7.1 GB done.

Now im kind of lost. Isn't sync supposed to make sure all file transfers are done? That's what i understood from your previous post and **man sync**.I imagine this is on a file-by-file basis. The file currently being copied is entirely written to the other partition, after which sync returns. But the file manager then opens the next file and starts copying that. I presume this is normal behaviour when copying directories.

---

### Post by 3rdalbum on 2013-02-09
The "sync" command just flushes the buffer - it writes everything from the buffer to disk and returns when it is done. If you run it in the middle of a file copy, it will temporarily stop filling the buffer and flush it, then exit and copying will continue as normal.

---

### Post by black3agl3 on 2013-02-09
Ok. Thanks everybody for all the answers. I suppose I have to do some more googling to properly understand how the whole sync and async thing works.

For now I'll just remove the **sync** option from the fstab file.

Cheers,
black3agl3

---

### Post by sudodus on 2013-02-09
> **black3agl3 said:**
> SysRq is the Print Screen key? My keyboard does not show SysRq.

Yes, it is often on the Print Screen key. Try
***alt + that key***
> 

I did the following:
[remount cause the partition is currently mounted sync]
[B]sudo umount /dev/sda3 
sudo mount /dev/sda3 /mnt/exthd[/B]

Then I tried to copy a folder [/mnt/exthd/Projects/new/] of around 7 GB to [/mnt/exthd/new] so that i could get a file transfer dialog that would not disappear immediately.
The estimated time was 3 minutes.

I launched terminal and typed in **sync** followed by enter.
After around 5 seconds the sync command was done and i was returned to prompt.

The file transfer dialog was only 200 MB out of 7.1 GB done.

Now im kind of lost. Isn't sync supposed to make sure all file transfers are done? That's what i understood from your previous post and **man sync**.
Well it synced, but then the copying contined, because it had not finished. ***You should run sync after the copying process tells you it has finished*** (so the system says it has finished, but the crude work of writing from the buffer to the disk (or flash) has not finished.

---

### Post by black3agl3 on 2013-02-09
I tried copying another 8 GB file and waited around 3 minutes until the file copy dialog closed. As quickly as i could i ran **sync**. It returned me to the terminal prompt instantly as far as I could tell. Does that mean the actual writing to disc was already done?

If the writing was already done, how do i explain the fact that copying a 14 MB file takes 5 minutes when the partition is mounted sync, but copying a 8 GB file takes 3 minutes when the partition is mounted async? I'm no expert but it seems to me there is a too large difference in copying speeds?

---

### Post by sudodus on 2013-02-09
> **black3agl3 said:**
> I tried copying another 8 GB file and waited around 3 minutes until the file copy dialog closed. As quickly as i could i ran **sync**. It returned me to the terminal prompt instantly as far as I could tell. Does that mean the actual writing to disc was already done?

If the writing was already done, how do i explain the fact that copying a 14 MB file takes 5 minutes when the partition is mounted sync, but copying a 8 GB file takes 3 minutes when the partition is mounted async? I'm no expert but it seems to me there is a too large difference in copying speeds?

This is explained here
> **3rdalbum said:**
> There are two factors at play here.

First, writing to NTFS drives is slower than writing to a drive with a native filesystem (such as ext4). This has always been the case, although it should be quicker than you describe.

If you remove the 'sync' parameter from fstab you will get faster copying. Sync copies one chunk from the source disk, puts it on the destination disk, then copies the next chunk, etc. [COLOR="Red"]Without sync, Linux will read as much from the source as it can, and SIMULTANEOUSLY write to the destination. A lot faster.[/COLOR] Also, the "copy" operation appears to finish when the whole source file has been buffered, and the system continues writing to the destination in the background.

Sync is safer for people who forget to eject their USB drives before ripping them out of the USB port.

---

### Post by black3agl3 on 2013-02-09
"A lot faster"
Is 952 times faster a realistic value?

---

### Post by sudodus on 2013-02-09
> **black3agl3 said:**
> "A lot faster"
Is 952 times faster a realistic value?
Well, USB 2 is very inefficient with interrupted read/writes (as for example with thousands of small files). I guess you get a similar situation when you mount the drive with the sync option.

---

### Post by black3agl3 on 2013-02-09
I see. Thanks a lot for your input.

Cheers,
black3agl3

---

### Post by sudodus on 2013-02-09
You are welcome :-)

---

