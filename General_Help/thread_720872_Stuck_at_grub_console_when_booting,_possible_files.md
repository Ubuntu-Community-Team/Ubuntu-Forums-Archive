---
title: "Stuck at grub console when booting, possible filesystem problem"
date: 2008-03-10
forum: General Help
---

### Post by Roberto Bonvallet on 2008-03-10
Hi all.

One day my laptop froze when I was using it, and the disk (I think) made an ugly sound.  When I turned it off and on again, it didn't boot, but got stuck at the grub console prompt.

Here's the console session after I tried to boot manually:
```

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> kernel /vmlinuz root=/ ro
   [Linux-bzImage, setup=0x1c00, size=0x157a82]

grub> initrd /initrd.img

Error 16: Inconsistent filesystem structure

```

Trying with vmlinuz.old and initrd.img.old:
```

grub> kernel /vmlinuz.old root=/ ro
   [Linux-bzImage, setup=0x1c00, size=0x157860]

grub> initrd /initrd.img.old
  [Linux-initrd @ 0x7969000, 0x67644b bytes]

grub> rootnoverify (hd0,0)

grub> chainloader +1

Error 13: Invalid or unsupported executable format

```

Another error I get when I try to cat some files (not all of them, just some) is:
```

grub> cat /boot/grub/menu.lst

Error 18: Selected cylinder exceeds maximum supported by BIOS

```

It seems that the filesystem is screwed up.  I'd like just to be able to boot once in order to copy my files somewhere else, and then to check whether the disk is broken or not.  It is a laptop, so I hope for a solution that doesn't involve taking the disk out of it.

What should I try, without risking my files?
Thanks in advance for any help.

---

### Post by Roberto Bonvallet on 2008-03-10
[...]

Silly me, I hadn't tried just typing "boot".  I could manage to make it boot, but I get a lot of errors like the following while booting (numeric values replaced with ellipses):
```

[...] hda: task_in_initr: error=0x01 { AddrMarkNotFound }, LBAsect=..., sector=...
[...] ide: failed opcode was: unknown
[...] hda: task_in_initr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[...] hda: task_in_initr: error=0x40 { UncorrectableError }, LBAsect=..., sector=...
[...] end_request: I/O error, dev hda, sector 22613339

```

After a while, it shows the login prompt.  When I try to login, both as root and as a normal user, I get a lot of the same errors and I don't get logged in, but get the login prompt again instead.

Any helpful clue anyone?

---

