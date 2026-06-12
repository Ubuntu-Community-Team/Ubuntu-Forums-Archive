---
title: "Edgy Kernel Update problem"
date: 2007-02-17
forum: General Help
---

### Post by JNik on 2007-02-17
Edgy update informed me there is a newer kernel version (*2.6.17-11 generic*), so I downloaded it, installed it, and restarted my pc.

Since then, edgy halts after the following messages;

```
usb 1-1: device not accepting address 2, error-71
* Activating swap...  [ok]
* Checking root file system...
fsck 1.39 (29-May-2006)
/dev/sda7: clean, 152183/286100 files, 1001573/5713107 blocks  [ok]

* Checking file system...
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda6: 135915 files, 3168994/3210708 clusters
```

If I press ALT+CTRL+DELETE I can login but I get the following message:

```
No directory, logginh in with HOME=/
```

Everything was working just fine before the update. Now I can't even boot with the older kernel. Can someone help me ?

I load the kernel with the following parameters

```
ro quiet noacpi noapic
```

Thanks in advance

---

### Post by JNik on 2007-02-17
It turns out that kernel update had nothing to do with my problem. It was just a coincidense.

There was a corrupted file on my FAT partition that was causing the problem!

the solution was:

[LIST]
[*]pressed <alt>+<ctrl>+<delete> when boot halted
[*]logged in
[*]sudo ps -ux
[*]sudo kill <fsck process>
[*]sudo dosfsck /dev/hdc1
[*]Saw the name of the file, the system halted
[*]pressed ctrl+c
[*]sudo mount /dev/hdc1 /media/hdc1
[*]removed the problematic file
[*]sudo reboot
[/LIST]

It amazes me that just one corrupted file on a non system crucial partition can prevent ubuntu from booting!!

---

