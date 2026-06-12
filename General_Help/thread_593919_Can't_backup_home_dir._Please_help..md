---
title: "Can't backup home dir. Please help."
date: 2007-10-27
forum: General Help
---

### Post by Tom Chaudoir on 2007-10-27
I really need to backup my home directory to another drive so that I can do a clean Gutsy install from a live disk. I used update manager for the upgrade and lost HAL and can't start it although dbus seems to be running.

I tried sudo cp <source> <destination>. It throws permission errors, even when I login as root.

I tried Home User Backup. It opens, then complains that HAL isn't running. Dead end.

I tried archiving via file roller and rar and others. "Please wait. Getting file list." The system load jumps to about 5 and stays there for about half an hour, then drops to zero and the machine locks up. I mean top stops refreshing completely.

*Any* ideas greatly appreciated. I'm at the end of my rope. There just has to be an easy way out of this.

Best,
Tom

---

### Post by taurus on 2007-10-27
Where is the **destination**?  Does it happen to be a ntfs filesystem?

---

### Post by Tom Chaudoir on 2007-10-27
Thanks for answering!

Fdisk -l says. " W95 FAT32 (LBA)"

Does that help?

Best,
Tom

---

### Post by taurus on 2007-10-27
So you want to backup your $HOME to vfat filesystem?  How did you mount that vfat partition?

Probably would be easier to just tar your $HOME into a big file and then save it.  Then, you can unpack it later in Ubuntu if you wish.

---

### Post by por100pre1 on 2007-10-27
Try using Grsync for that. I use it to backup my whole user folder to and external hdd:

```
sudo aptitude install grsync
```

---

### Post by Tom Chaudoir on 2007-10-27
Nice app. Thanks!

Except it had a problem. It threw a lot of errors. There seemed to be 2 types. Here's the first:

rsync: opendir "/media/hdb/home/tom/Desktop/My files" failed: Permission denied (13)

That seems weird because it's nothing special. Just a folder on my desktop. Does the (13) mean something? That's just an example. It threw tons of them.

I can't quote the other error group because they didn't land in the error log. It was something like:

Skipping non-regular file <filename>

Any ideas?

Thanks.
Tom

---

