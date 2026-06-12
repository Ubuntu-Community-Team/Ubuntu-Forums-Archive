---
title: "can there be two swaps for one linux partition ?"
date: 2008-07-05
forum: General Help
---

### Post by dexter.deepak on 2008-07-05
logically it seemed to me that we cant have more than 1 swap partitions for one linux partition,as there seems to be no kernel support for this.
then i heard about swap files. i have never used them,but i got a thought that if we can have a swap partition + a swap file , then why cant we have swap partition + another swap partition ?
i am asking this for suppose, i run out of swap sapce then can i create one more swap ?

i would also like someone to tell me how to create and use a swap file ..

---

### Post by jw5801 on 2008-07-05
What makes you say that there is no kernel support for having more than one swap partition?

---

### Post by dexter.deepak on 2008-07-05
oops!! i am sorry ...thats a wild guess...coz if the kernel had the support, we would have been seeing a lot more multi-swap systems.

pardon me if that is a real BAD guess...

---

### Post by VMC on 2008-07-05
> **dexter.deepak said:**
> 

i would also like someone to tell me how to create and use a swap file ..

Here you go : [http://ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file](http://ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file)

---

### Post by ramjet_1953 on 2008-07-05
I'm not sure if you understand fully what the swap file is for.

Your statement that you have never used them, intrigued me. A swapfile is controlled by the system, not you, and comes into play, when required.

In the past, when PC's had small amounts of memory, the swap file would 'kick-in' as a buffer. In doing this, things slowed down, of course, but a system crash was averted.

However, with modern PC's and the price of RAM now being so cheap, most PC's have abundant RAM, so the swapfile is rarely used in normal operation. However, if there is some operation that does use gobs of memory, the swapfile will still come into play.

The main use for the swapfile on modern machines is so that you can utilise the suspend, resume and hibernate features, found in most laptops.

That is why it is still recommended to have a swapfile twice that of your RAM (within reason, as it would probably never need to exceed 2GB).

Of course, if you never use these features and you have abundant RAM, you can safely have a smaller swapfile.

Regards,
Roger :cool:

---

### Post by jw5801 on 2008-07-05
As Roger says above, having multiple swap partitions is not really of any benefit whatsever. But you could certainly do it if you wanted. Although if you did it because you upgraded your RAM and needed more swap so you could hibernate, it would make more sense to expand the existing swap partition.

---

### Post by cariboo on 2008-07-05
I'd like to chime in here I have hardy installed on one hard drive and intrepid installed on an other both drives have a 4GB swap partitions. I found that in intrepid at least, I haven't booted up hardy for about a week, that the two swap partitons where combined for a total swap partition of just over 8GB.
Last night during a re-install of intrepid, I just eliminated the swap partition on the drive that intrepid is on and everything seems to be working ok.
This is the output of free:

```
 free
             total       used       free     shared    buffers     cached
Mem:       2025348    2000480      24868          0     119032    1004824
-/+ buffers/cache:     876624    1148724
Swap:      5662872        240    5662632
```

I see I'm going to have to resize the only swap partion as it is still a little on the big side.:)

Jim

---

### Post by sayakb on 2008-07-05
Sometimes, you need swap for letting you to suspend and hibernate. But as already mentioned, it really doesn't help much as a RAM, since the HDDs are much slower as compared to RAM. So when the system actually starts using the swap(s) mounted, your system becomes quite slow when compared to the speed it had when it was solely using the RAM.

---

### Post by dcstar on 2008-07-05
> **LinuxIsInnovation said:**
> Sometimes, you need swap for letting you to suspend and hibernate. But as already mentioned, it really doesn't help much as a RAM, since the HDDs are much slower as compared to RAM. So when the system actually starts using the swap(s) mounted, your system becomes quite slow when compared to the speed it had when it was solely using the RAM.

Exactly, in these days of cheap RAM you are a fool to yourself (and a burden to others) if you have a system that utilises a lot of disk virtual memory (swap) in ongoing operation.

However, if you do have a system that does go swap a lot, performance can be increased by having that swap partition on a separate hard disk (the fastest you can find).

---

### Post by dexter.deepak on 2008-07-05
actually, i am facing a problem in hibernation ...i dont know if it is due to less swap (1gb for my 1 gb ram), or its an ubuntu bug...coz i CAN hibernate thru the kubuntu session.

i cant extend the existing swap,as i have never done it and as i have no extra space in the neighbour partitions(what i see in the fdisk -l output)
so i plan to introduce a new space partition from a different harddisk of mine...but still i am not sure whether the new swap will be used ...the reason i cant understand that how will the kernel manage the option that "which swap partition is to be used to dump the dirty pages - the first one or the second one ?"

---

### Post by dcstar on 2008-07-05
> **dexter.deepak said:**
> actually, i am facing a problem in hibernation ...i dont know if it is due to less swap (1gb for my 1 gb ram), or its an ubuntu bug...coz i CAN hibernate thru the kubuntu session.

i cant extend the existing swap,as i have never done it and as i have no extra space in the neighbour partitions(what i see in the fdisk -l output)
so i plan to introduce a new space partition from a different harddisk of mine...but still i am not sure whether the new swap will be used ...the reason i cant understand that how will the kernel manage the option that "which swap partition is to be used to dump the dirty pages - the first one or the second one ?"

Just make the only swap partition on the other disk and then delete the old one - stop making things unnecessarily complicated.

---

### Post by dexter.deepak on 2008-07-05
this is what the problem is.. i will not always have the secondary hdd with me, so i cant remove the old swap pttn...i can only "add" to the old one.

---

### Post by jw5801 on 2008-07-05
You shouldn't need anymore swap. If you can hibernate fine from KDE but not from GNOME then it has absolutely nothing to do with your swap.

That being said, if you wanted an extra swap partition on the other hard drive, you'd just need to create it (use GParted or another partitioning tool) and then reference it in /etc/fstab (follow the same format as the existing swap partition).

---

