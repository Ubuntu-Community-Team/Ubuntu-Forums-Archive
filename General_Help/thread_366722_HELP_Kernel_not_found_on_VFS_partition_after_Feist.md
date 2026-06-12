---
title: "HELP: Kernel not found on VFS partition after Feisty upgrade"
date: 2007-02-21
forum: General Help
---

### Post by cronholio on 2007-02-21
I think I just messed up my dist-upgrade to Feisty. I remember that early in the process I was asked if my root partition resides on a RAID or VFS, and if drivers (?) for any of these should be loaded early in the boot process. I boldly replied "none". Now what I get when booting is this:

```
VFS: Cannot open root device
Kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0,0)
```

Can anyone tell me how to load VFS support before mounting the root partition? I do have access to the root file system via Knoppix Live CD.

Any help is appreciated - I really rely on that system (I know I shouldn't have done the upgrade but hey, you break it, you learn :) ).

---

### Post by cronholio on 2007-02-21
Anybody?

I searched for the error on the net but it seems that usually it has to do with a corrupt file system. In my case I think I need some initrd entry in the grub.conf... :???:

---

### Post by cronholio on 2007-02-21
I ran reiserfsck on the partition and it seems fine. I tried booting other (older) kernels which gives me the same error message. They obviously all do have ReiserFS support, so the problem must be related to something else that changed with Feisty.

---

### Post by cronholio on 2007-02-21
It would probably help if I mount the partition on the live CD, chroot into it and use aptitude to force a reinstall of the package that asked me the question I mentioned in my original post, so this time i can give the correct reply. Can anyone tell me which one it might be?

---

### Post by cronholio on 2007-02-21
I can get a login shell on my system now by using the Feisty Live CD and giving root=/dev/hda1 as boot parameter. Any ideas on how to proceed?

**EDIT: Never mind, issue has been resolved.**

---

### Post by revoltism on 2007-02-22
I have problably the same issue as you did. In my case i choosed "all". I haven't had time looking this up. I think it has with the kernel upgrade to 2.6.20 and maybe som hardware problems cause it freezes on boot up complaining about network. 

If you solved it i would preciate if you could post how you did it.

---

### Post by cronholio on 2007-02-22
If it complains about network, it is probably not the same issue that I had. In my case it panicked right after GRUB tried to load the kernel. Anyway, maybe this helps: I used the Feisty Live CD and chose Start Ubuntu, but pressed F6 and gave it "vmlinuz1 root=/dev/hda1" as boot options. That way I got hundreds of messages about modules failing to load, but in the end I had a root prompt on my partition. I couldn't access the network or mount a CD-ROM, but fortunately I still had most of the packages in the apt cache, so I could dist-upgrade again until everything was fine.

If the Live CD thing doesn't work for you, you might want to boot it normally, mount your old drive, chroot into it and finish the dist-upgrade.

---

### Post by ljoslin on 2007-02-24
I have the same issue, I upgraded to feisty as well.  How did you reslove this?

Ljoslin

---

### Post by cronholio on 2007-02-25
> How did you reslove this?

Erm, look at the post directly above yours, that's where I explained it.

---

