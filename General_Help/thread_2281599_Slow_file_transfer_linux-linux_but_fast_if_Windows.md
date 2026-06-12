---
title: "Slow file transfer linux-linux but fast if Windows is in the middle"
date: 2015-06-08
forum: General Help
---

### Post by james251822 on 2015-06-08
I'm in the process of migrating a few TB of media from my Ubuntu 14.04 server to an unRAID server. I mounted the smb share from the unRAID and started copying the data using rsync over but I was only getting about 100mbps transfer speeds despite the fact that it's a gigabit connection. I then used my windows computer to do the copying and it's saturating the Gigabit connection. Any ideas why this might be?

I'd love to get this going at speed directly on the Linux machine as it'll save me leaving my windows PC on for a few hours.

Cheers,

James

---

### Post by SeijiSensei on 2015-06-08
Can you mount the device with NFS rather than SMB?  That would probably have better performance.

---

### Post by james251822 on 2015-06-08
I tried NFS but had trouble mounting as I've no experience with it. The fact that Windows is reading from and writing to SMB shares suggests that SMB can be much faster - just don't know why it's 10x slower when done from Linux.

---

