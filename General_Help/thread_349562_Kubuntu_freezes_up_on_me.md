---
title: "Kubuntu freezes up on me"
date: 2007-01-30
forum: General Help
---

### Post by glue on 2007-01-30
Kubuntu freezes on me 3 or 4 times a day for no explicable reason. I need to reset the computer which screws up grub and need to boot from a CD to fix grub before booting into Kubuntu. I have a 700 mhz processor with 256 megs of RAM. Is that not enough? Would I be better off switching to Ubuntu?

---

### Post by kebes on 2007-01-30
Both Gnome and KDE use up similar amounts of ressources, so switching between Ubuntu/Kubuntu probably won't help. You could try using xfce (Xubuntu), but from your specs you should be able to run Kubuntu without too much trouble.

One of my machines is a P3 600 MHz with 768Mb of RAM, and it runs Kubuntu without crashing (a bit slow, but very stable).

Random crashing like that is usually (in my experience) a hardware issue. Are you dual-booting? Does it happen in Windows also? One thing to do is a memory test. Boot into a LiveCD, and at the initial screen try doing a memtest. If you have multiple ram chips you can try removing one and see if the crashes still happen. Also, if you boot into a LiveCD for awhile, does it still crash? (If not, maybe it's the hard drive?)

You can also use the commandline program "fsck" to do a filesystem check. You might have bad sectors on one of your partitions.

Of course it could also be a motherboard issue, video card issue, etc. It may be difficult to track down, but my guess is it's hardware.

---

