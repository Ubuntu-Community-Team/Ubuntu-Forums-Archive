---
title: "Can I just get rid of the boot splash?"
date: 2006-12-09
forum: General Help
---

### Post by kd7swh on 2006-12-09
Can I get rid of the boot splash, and just display the boot text?

(in edgy)

---

### Post by hikaricore on 2006-12-09
I'm not 100% sure on this but I believe if you just remove the "splash" line from your kernel line in grub's menu.lst it will only show text.

Example mine is:

[I]title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=6262cdad-9c85-431e-a15a-45a7b01539a1 ro quiet [/I]**splash**[I] vga=791
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot[/I]

If I change it to:


[I]title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=6262cdad-9c85-431e-a15a-45a7b01539a1 ro quiet vga=791
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot[/I]


to modify grub run:

```
gksudo gedit /boot/grub/menu.lst
```

and find the section similar to mine, which should be right under:

## ## End Default Options ##


Good luck,

--Aaron

---

### Post by kd7swh on 2006-12-09
if i remove quiet is boot more verbose?

---

### Post by hikaricore on 2006-12-09
I believe so.  Been awhile since I've played around with grub, I'm a little rusty. :P

---

### Post by kd7swh on 2006-12-09
removing splash worked to get the boot text, but I know that some of the boot text is being suppressed is it the word "quiet"  that is doing it? :confused:

---

### Post by hytek on 2006-12-09
just take out quiet and splash and you'll see the standard verbose booting.

---

