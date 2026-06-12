---
title: "Gutsy Kernel Panic Init error."
date: 2007-12-07
forum: General Help
---

### Post by lszanto on 2007-12-07
I have been running gutsy for about 5 days now and once again it has crashed/failed to start at startup. I dual boot with windows vista which as not been an issue but today when I went to boot up I was met with this message:

[     20.517834] Kernel panic - Not syncing: No init found. Try passing init= option to kernel.

I don't believe I touched anything that would cause this but I did install some updates yesterday. Any help would be appreciated.

thanks, Luke

---

### Post by lszanto on 2007-12-07
*Bump* Anybody? Or is more information needed, I really need this fixed by tonight.

---

### Post by lszanto on 2007-12-07
Nobody, Is there anything I can do other that reinstall cause I think that all I need is the kernel to get reinstalled but I'm not sure if this is correct or how to do this.

---

### Post by 42Wired on 2007-12-12
I'm in the same boat. Help would be greatly appreciated.

---

### Post by misha1983 on 2007-12-29
I'm having the same problem here now.  Started when I removed an IDE DVD writer from the machine.

grub options:

```

root (hd0,0)
kernel /vmlinuz-2.6.22-14-generic root=UUID=7697777f-9ca0-468a-...
initrd /initrd.img-2.6.22-14-generic
quiet

```

Hope someone has ideas for this.

Misha

---

### Post by misha1983 on 2007-12-30
We've worked out what the problem was.  When I removed the DVD writer, I must've bumped the RAM sticks.  Remounting them solved the issue.

Other symptoms were that none of the live CDs I had booted (Fedora Core 6, Knoppix, Ubuntu).  The memory checker util from GRUB showed a whole heap of errors checking RAM.

Hope that helps someone out there.

Cheers,
Misha

---

