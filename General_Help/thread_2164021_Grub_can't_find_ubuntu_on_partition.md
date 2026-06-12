---
title: "Grub can't find ubuntu on partition"
date: 2013-07-20
forum: General Help
---

### Post by cdiddy on 2013-07-20
Alright some quick backstory of how I got myself into this situation. So for some reason about a year ago I decided to encrypt my entire hard drive with truecrypt for an unknown reason. Its just one drive with windows 7 on it. A week ago I needed to install ubuntu for some things and without thinking I made a new partition and went ahead and installed 12.04 lts ubuntu(call this ubuntu install 1). Everything for that install went fine except for the fact that grub didn't recognize that windows was on the hard drive because it was encrypted. So I got my truecrypt rescue disk and repaired the original windows bootloader. Now windows was back to working but grub was gone from the picture so I couldn't dual boot. I didn't really know the easiest way to fix this so I made a new partition and installed ubuntu again on that partition(ubuntu install 2). Now I have grub back and windows works fine and ubuntu install 2 works fine but I can't get back ubuntu install 1. I don't believe I really did anything to it in the process unless truecrypt really messed with it. Grub wasn't recognizing that anything on the partition was bootable so I used daniel richters grub customizer to try ad manually add it to the grub. When I try to launch ubuntu install 1 from it it says:

```
Error: no arguments specified
Error: unknown file system
Error: you need to load the kernel first.
```

I used filesystem ext2/3/4 for the install. Anyway to possibly bring that install back or get files from it?

Thanks for your help.

---

### Post by oldfred on 2013-07-20
Another user who did manage to restore some data. I still am not sure what he did, but I somehow helped him a little.
 Restore lost partition that was truecrypt
[http://ubuntuforums.org/showthread.php?t=1874260](http://ubuntuforums.org/showthread.php?t=1874260)

---

