---
title: "boot error, cdrom_pc_intr appears to be confused"
date: 2005-10-28
forum: General Help
---

### Post by 5-HT on 2005-10-28
Allo,

I'm pretty concerned in regards to a recent boot failure.

Everything progressed normally until a point just after the kernel was trying to synchronize the system clock to that of the ubuntu servers. I was kicked out of the usplash screen, and was confronted with the message:

```
 hcd: cdrom_pc_intr: The drive appears confused (ireason = 0x01) 
```

Which simply repeated itself, rendering my pc unbootable.

 I rebooted multiple times, with the exact same error. As the error message has some bearing to my cd drive (well, dvd-rom drive), I tried placing a cd (non-bootable, just data) in the drive and thankfully breezy booted just fine.


As a little background, while Hoary installed and performed flawlessly for me (for which I'm very thankful), breezy would not install on my laptop unless I entered the "irqpoll", "acpi=off", and "no acpi" boot options, without which it complained about an IRQ (15) issue [which I believe to be (maybe i'm mistaken) a kernel (2.6.12-9-386) issue, and maybe not that of Ubuntu].

So I'm leaning towards the idea that these two issues may be related, and that my dvd-rom drive has an irq conflict with something...but why just have that spontaneous boot issue?
Shoudln't breezy simply function on my laptop or not?


Hopefully this was some strange isolated incident, and the good news is that I'm back up and running, but I'm still concerned about what went wrong, and If I should either fix something or (i'm afraid to say it as I love ubuntu) use a different os as my data is of primary concern (starving M.Sc student). 

I do back everything important up, but my only possibility is to back-up to CD, and I generate/modify important documents everyday...so it's really hard for me financially (as well as an annoyance) to have to do a backup everyday.

I'm wondering if anyone has any ideas about what that error message is (irq issue?) and if I should be concerned?

Any help is GREATLY appreciated.
Thanks for any input.

---

