---
title: "32 bit to 64 bit"
date: 2013-02-16
forum: General Help
---

### Post by pfeiffep on 2013-02-16
Just installed Ubuntu 12.10 from a DVD included with book Ubuntu Unleashed - the install version was 32 bit. So far everything works booting from the second internal drive:p. I really wanted to try out the 64 bit version. How can I 're-install' "over the existing" 32 bit installation? I have no need to save anything;).

Thanks in advance,
Pete

---

### Post by howefield on 2013-02-16
Download the 64 bit version and clean install over the top of your existing install. There is no upgrade path.

---

### Post by pfeiffep on 2013-02-16
> **howefield said:**
> Download the 64 bit version and clean install over the top of your existing install. There is no upgrade path.
Thanks - follow on question ...

I'm in the download process now. How do I choose the option over my existing install when it's on a secondary drive. I haven't touched the Win7 install at all since I have a second physical internal device.
Pete

---

### Post by howefield on 2013-02-16
You could select "Something Else" during the install process at the partitioning stage and mount your existing partitions as appropriate, which probably means / and /swap unless you created extra partitions for /home or anything else ? (you don't actually need to mount swap, it'll get found and used automatically)

Just watch where grub is going to be installed, to ensure it goes to the same disk as previously.

---

### Post by pfeiffep on 2013-02-16
Thank You - I'll be certain to watch for grub's location
Pete

---

### Post by Mark Phelps on 2013-02-16
> **pfeiffep said:**
> Thanks - follow on question ...

I'm in the download process now. How do I choose the option over my existing install when it's on a secondary drive. I haven't touched the Win7 install at all since I have a second physical internal device.
Pete

To be really "safe", you should really have the Win7 drive disconnected when you do this -- that way, you don't have to worry about where Grub gets written.

---

### Post by Sef on 2013-02-16
> To be really "safe", ....

To be really safe, make a backup of the disk with [clonezilla]("http://clonezilla.org").

---

