---
title: "What does this error mean"
date: 2022-05-31
forum: General Help
---

### Post by aj2022 on 2022-05-31
Hi Community

What does this error mean and how do I fix it?

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290552&stc=1[/IMG][IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG]

Also if I boot from a USB will I be able to access my files on the other hard drive as I need access to my files

any help would be appreciated

---

### Post by Bashing-om on 2022-05-31
aj2022; Hello

Kernel says the file system on sda1 is corrupted. Now *IF* the file system on sda1 is "ext4" we can do as suggested and run that manual file system check/repair.

So what are we working with ?
Post back - between code tags ! - the output of terminal command (from the liveUSB) :
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Now, as to access to your files - Hey that depends on where they are and the state of the corruption.
We know more when we see what "fdisk" reports.

[INDENT]in small steps
[/INDENT]

---

### Post by mIk3_08 on 2022-06-01
> **aj2022 said:**
> Hi Community
What does this error mean and how do I fix it?
[IMG]https://drive.google.com/file/d/1vI-V2vUIhzm2x9pSGZV6IauOCWRnYpEg/view?usp=sharing[/IMG]
Also if I boot from a USB will I be able to access my files on the other hard drive as I need access to my files
any help would be appreciated
I agree with [COLOR=#000000]Bashing-om. I've encountered this behavior before with my old hdd. Then t[/COLOR]ry the fsck command and just follow the instructions. This will help check your directory structure, blocks, inodes and etc. Maybe it might help you solve your issue. Regards and cheers.
```
fsck /dev/therightmounted-sda -y
```

---

### Post by coffeecat on 2022-06-01
Duplicate of [https://ubuntuforums.org/showthread.php?t=2475556](https://ubuntuforums.org/showthread.php?t=2475556)

Please do not post duplicate threads of the same problem. It causes confusion and dilutes community effort.

Thread closed.

---

