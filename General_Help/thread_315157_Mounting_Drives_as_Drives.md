---
title: "Mounting Drives as Drives"
date: 2006-12-08
forum: General Help
---

### Post by osarusan on 2006-12-08
Hi, I recently resized and reformatted one of my partitions on a drive, and after doing that, it won't mount. The partition changed from sdb2 to sdb3, and I went to change fstab to reflect that, only it's not using a UUID?? Something I haven't seen since before Edgy...

I've got the partition mounted now, but Edgy doesn't seem to think it's a hard drive... it doesn't show up on my Desktop or on my list of drives in Computer, but if I navigate to it's mount point, I can see everything there. How do I tell Edgy that it's a hard drive?

Thanks

---

### Post by bodhi.zazen on 2006-12-08
Interesting that the drive should change to sdb3.

First, did you re-boot ?

Second, what is your mount point?

---

### Post by strabes on 2006-12-08
can you paste the output of this command: ```
cat /etc/fstab
```

What filesystem did you format it to? Where did you mount it to? Did you: ```
sudo mkdir /media/yournewmountpoint
```

---

### Post by osarusan on 2006-12-09
Well, the first time I rebooted, it did nothing... but I rebooted again this morning and my drive is there, on my desktop, and all is good again.

I have no idea why it changed from sdb2 to sdb3... very weird, huh?

But it does seem to be working now. One question: does it matter if my fstab locates the drive as /dev/sdb3 instead of the UUID that it originally used when it auto-mounted the drives after installing Edgy? I don't know why that UUID no longer makes the drive work... but does that even matter? If so, I'd like to know how to fix the UUID to make it work again.

---

### Post by bodhi.zazen on 2006-12-09
> **osarusan said:**
> I have no idea why it changed from sdb2 to sdb3... very weird, huh?

Yes

[/quote]One question: does it matter if my fstab locates the drive as /dev/sdb3 instead of the UUID that it originally used when it auto-mounted the drives after installing Edgy? I don't know why that UUID no longer makes the drive work... but does that even matter? If so, I'd like to know how to fix the UUID to make it work again.[/QUOTE]

No, it does not matter.

If you wanted, in a terminal type:```
ls /dev/disk/by-uuid/ -l
``` to see your partitions listed by UUID.If you wnated, change the line "/dev/sda3 ..." to "UUID=## ....." where UUID=### is the number of you partiton (looks like this:

> [color=cyan]fab05680-eb08-4420-959a-ff915cdfcb44[/color] -> [color=yellow]../../sda14[/color]

---

