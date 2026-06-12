---
title: "Formatting USB Drives Forces Reboot"
date: 2023-04-22
forum: General Help
---

### Post by wmichaelb2 on 2023-04-22
I'm running Ubuntu Studio 22.04, but this problem goes back to at least the previous version. I frequently reformat USB drives to either make a bootable drive, or store music. Whenever I do, the system demands that I restart before I'm able to write to the drive because the kernel hasn't yet recognized the new partition. Is there a setting that will let me avoid this? Thanks in advance.

---

### Post by sudodus on 2023-04-22
You can try with
```

sudo partprobe

```

It might help if you also flush the buffers with
```

sync

```
unmount the drive
```

sudo umount /dev/sdx*

```
where x is the USB drive's letter (for example a or b or c).

Then you can unplug the drive and plug it back. *Maybe* this eliminates reboot.

---

### Post by wmichaelb2 on 2023-04-24
Thanks for responding, I'll give that a try.

---

