---
title: "How to disable the &quot;file checker&quot; that apears after 39 or so startups"
date: 2006-12-28
forum: General Help
---

### Post by ByeByeBill on 2006-12-28
Hi all,just wondering how to disable that annoying file checker that hangs up my computer every 39th or so startup.If I am stuck with it,so be it,but it always happens when Im in a hurry,and realy cant wait.As always,thanks ahead of time.:)

---

### Post by pay on 2006-12-29
I think that it is compilled into the kernel. Anyway it only does it with ext3, if you use reiserfs it won't happen.

---

### Post by dcstar on 2006-12-29
> **ByeByeBill said:**
> Hi all,just wondering how to disable that annoying file checker that hangs up my computer every 39th or so startup.If I am stuck with it,so be it,but it always happens when Im in a hurry,and realy cant wait.As always,thanks ahead of time.:)
```
man tune2fs
```

---

### Post by ByeByeBill on 2006-12-29
Thanks,that worked!Have a great new year!:)

---

### Post by clarkth on 2006-12-29
I've been looking for this also, thanks! :)

---

### Post by bulldog on 2006-12-29
This is a real handy program to manage the fsck.

[http://www.ubuntuforums.org/showthread.php?t=295262](http://www.ubuntuforums.org/showthread.php?t=295262)

---

### Post by anaconda on 2006-12-29
hmmm.. 
so what was the solution? converting ext3 to reiserfs? or using tune2fs to change something?

My solution would have been to edit your /etc/fstab file and change the "0 1" in the end of the mounting line to "0   0" so that the fsck would never be run at boot time...

However I DO think that it is a good idea to run fsck for you root partition sometimes.
I keep my root partition 35GB.. it would be annoying to wait fsck to check >250GB partition..

---

### Post by glendavee on 2006-12-29
I have slightly different problem. File checking runs at every startup. File checking fsck 1.39 shows (ok) and system then hangs for about 70secs before resuming the normal startup screen. Should I try the same fix??
Thanks

---

