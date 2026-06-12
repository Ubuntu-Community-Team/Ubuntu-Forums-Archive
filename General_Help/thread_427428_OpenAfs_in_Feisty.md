---
title: "OpenAfs in Feisty"
date: 2007-04-29
forum: General Help
---

### Post by aroch1 on 2007-04-29
Hi.  I recently installed OpenAfs from the Feisty repositories, compiled the kernel module and everything was working fine.  Upon reboot, my /afs directory is emtpy.  lsmod shows that the openafs kernel module is running.  When I recompile the kernel module, afs works until I reboot.  As compiling the kernel module is time consuming on my old machine, does anyone have an idea as to how I can fix this problem?  Let me know if you need any other information.

---

### Post by falt004 on 2007-04-29
I followed the thread below and managed to get it working:-

[http://ubuntuforums.org/showthread.php?t=264992&highlight=afs](http://ubuntuforums.org/showthread.php?t=264992&highlight=afs)

Hope this helps.
/Fuad

---

### Post by aroch1 on 2007-04-29
I followed the direcitons on that post, but I still had the same issue.  For some reason afs works if i do

```
sudo /etc/init.d/openafs-client restart
```

While this is better than recompiling the kernel module every time I want to use afs, I'd still prefer not to have to do it.  Does anyone have any experience with/solutions for a similar problem?

---

