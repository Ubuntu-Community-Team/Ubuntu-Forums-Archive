---
title: "[SOLVED] I installed the Master Kernel and I can't find my Windows partition."
date: 2007-08-27
forum: General Help
---

### Post by RonB123123 on 2007-08-27
I installed the Master Kernel and I can't find my Windows partition. What do I do?

Can I somehow recover the partition? I really need to do this because there are very important documents on my Windows partition. 

By the way, I installed the Master Kernel using this thread. 
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel)

Can someone please help me?

---

### Post by scrooge_74 on 2007-08-27
If you did not change anything else besides the kernel it should be listed in your/etc/fstab file. Before editing that file make a backup of it

If you type df in a terminal it shoud tell you what partitions and space you have. If you type mount it will tell you what is mounted.

---

### Post by RonB123123 on 2007-08-28
Thanks for the help, but I ended up fixing it.

I opened the terminal, and ran this.
```

mount -a

```

Now everything is mounted and you can see your files in /media/sda1. Reboot, and it will show up on your desktop as an icon. :)

---

