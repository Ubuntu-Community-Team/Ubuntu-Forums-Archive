---
title: "removing grub entries (leftover after upgrading to 7.04?)"
date: 2007-06-29
forum: General Help
---

### Post by kraigory on 2007-06-29
okay, i have a dual boot xp and 7.04 working well.

The only problem is, there are 2 other entries in GRUB that I don't need- they all look the same except the kernel versions are different. I first installed dapper and then upgraded to edgy, and then to feisty, and thats when all the extra entries came from. I'm assuming I can just delete/remove them, as I don't need to boot into an older kernel, right?

So how do I remove these from the grub menu? Can I just delete the entry in the grub menu.lst, or do I have to do something a little more thurough?

fyi i haven't tried booting them yet, not sure what would happen.


EDIT: thought this might help.


```

**/boot/grub/menu.lst**

title		Ubuntu Linux, kernel 2.6.20-16-386 (main)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=b60a3e18-5020-4a1d-ae4f-bbf4e6e277d9 ro single
initrd		/boot/initrd.img-2.6.15-26-386

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by PgR on 2007-06-29
If your machine is running OK with the new kernel, then you can remove them if you like.

Then again, if your desire is to simply remove them from the menu you're offered, comment out the ones you don't want with a # at the start of each line. That way you can re-enable it if you want.

---

### Post by Irony on 2007-06-29
Uninstall the old kernels from synaptic (or else they just take up space), I think this will also update your menu.lst but if not just manually remove them.

---

### Post by mikewhatever on 2007-06-29
All those kernels are installed on your machine, so, consider uninstalling them from synaptic. The easiest way to find the packages to uninstall is to search for the relevant kernel number. This should also remove the entries from grub menu.

---

### Post by kraigory on 2007-06-29
excellent, thanks!

---

### Post by springs420 on 2007-10-24
Just what I was looking for. Thank you.

---

