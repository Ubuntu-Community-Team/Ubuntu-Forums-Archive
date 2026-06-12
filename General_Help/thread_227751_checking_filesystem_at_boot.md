---
title: "checking filesystem at boot"
date: 2006-08-02
forum: General Help
---

### Post by jordilin on 2006-08-02
Every 30 boots or sth, the filesystem is checked at boot. Yesterday, I got (after the check) a message saying 20% of discontinuous blocks (or sth like that, I don't remember). What does it mean? It means that the filesystem is fragmented?...

---

### Post by jordilin on 2006-08-02
anyone?

---

### Post by Ramses de Norre on 2006-08-02
Yes it does, I don't know how you get to that much fragmentation though and neither do I know how to defragment it..

---

### Post by jordilin on 2006-08-02
> **Ramses de Norre said:**
> Yes it does, I don't know how you get to that much fragmentation though and neither do I know how to defragment it..

So, the question now would be how to defragment a hard drive with an ext3 filesystem.

---

### Post by jordilin on 2006-08-02
Although, I've always thought it was not necessary to defrag an ext3 filesystem!!!

---

### Post by Ramses de Norre on 2006-08-02
That's what they told me too, and I've never seen more than 3% or something like that myself.. so I think it's very weird that you've got 20% fragmentation..

---

### Post by jordilin on 2006-08-02
> **Ramses de Norre said:**
> That's what they told me too, and I've never seen more than 3% or something like that myself.. so I think it's very weird that you've got 20% fragmentation..

Yesterday, I was playing/investigating about encrypted loopback devices and how to create encrypted folders and then when I booted the system I got that 20%. It's really weird, and perhaps I'll have to reinstall and format my hard drive. In any case, it should not have happened this, as a loopback device is a special device that allows you to mount a normal file as it was a physical device and it has nothing to do with fragmenting the filesystem. 
How can I recheck the filesystem again without having to boot 30 times?

---

### Post by Ramses de Norre on 2006-08-02
```
sudo shutdwon -rF now
``` will reboot and force an fsck. 
And I'd look around about fragmented ext3 partitions before you reinstall, there might be a fix/solution.

---

### Post by jordilin on 2006-08-02
> **Ramses de Norre said:**
> ```
sudo shutdwon -rF now
``` will reboot and force an fsck. 
And I'd look around about fragmented ext3 partitions before you reinstall, there might be a fix/solution.

I will recheck again and see if I get the same weird thing.

---

### Post by ajgreeny on 2006-08-02
How much free space have you on your ubuntu partition?  I believe there is more likelyhood of fragmentation when space is very nearly used up on the partition.  How you can defragment, however, I'm afraid I don't know.

---

### Post by halfvolle melk on 2006-08-02
Look what our very own Jdong came up with :)
[http://www.ubuntuforums.org/showthread.php?t=169551](http://www.ubuntuforums.org/showthread.php?t=169551)

---

### Post by jordilin on 2006-08-02
I've rechecked the filesystem and these are the results:
for my / root partition 20Gb is only 0.7 % non contiguous so that's all right
for my /boot paritition 100Mb is 20% non contiguous, so being such a small partition I don't worry
for my /home partition 60Gb is 17% non contiguous. So perhaps being a big partition, I should not worry too much. Perhaps, I get this because I write a lot on my /home.

---

### Post by jordilin on 2006-08-02
> **halfvolle melk said:**
> Look what our very own Jdong came up with :)
[http://www.ubuntuforums.org/showthread.php?t=169551](http://www.ubuntuforums.org/showthread.php?t=169551)

Thanks, I have taken a look, and I'm very surprised. A defragmenter for Linux. I really thought ext3 filesystems didn't have to be defragmented.

---

