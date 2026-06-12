---
title: "Virtual Terminal Resolutions Won't Change"
date: 2007-10-26
forum: General Help
---

### Post by loadeddreams on 2007-10-26
Right now, my virtual terminals (Ctrl+Alt+F1 etc) aren't able to be used at all.. if I go to tty2 all I can really see is the hostname login, and it's so big even my username can't fit into the entire line.

I have went into /boot/grub/menu.lst and changed ...

```
# defoptions=quiet splash
```
to
```
# defoptions=vga=normal quiet splash
```

I also changed it in the kernel boot parameters e.g.
```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f98b3bf4-9ba6-474b-bf49-fc150c0c5222 ro quiet splash vga=normal
```

I read quite a few different placed online that this would help, but no luck when I completely disabled the framebuffers.

I also tried vga=789 and vga=791
neither of them work... it's always either an insanely small resolution, or an insanely small resolution with text that isn't even black... like there is a layer of almost opaque black over the screen..

now in my menu.lst the defoptions have a # in front of them, like they're commented out... but in that file above, it says not to remove the #'s...
Either way I added it to the kernel boot options to be safe... so anyways, is there any way to fix my virtual terminals? :(

thanks!

EDIT: I also don't see *any* information when I boot up (services starting) or get any graphic splash, but I do when I'm powering down.

---

### Post by loadeddreams on 2007-10-27
just a bump.. still really lost on this and I've read countless things on the internet.. none of which seem to work :(
open to any suggestions!

---

