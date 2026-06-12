---
title: "My harddrives are acting weird"
date: 2007-02-14
forum: General Help
---

### Post by Crakie on 2007-02-14
I posted this in 'absolute beginner talk', but got no response. It is probably more appropriate here anyway.

Up until tonight, I had the 'Storage Media' applet in my panel running in such a way that a couple of mounted harddrives would show up. You know, to easily access them. But they disappeared all of a sudden. They are there and mounted, since I can access them in Konqueror and they show up in 'fdisk -l'. But even if I use the applet's option 'show unmounted harddrives', they're not shown. I also noticed that their icon in /media has changed from a little harddrive to a normal folder. Basically, it seems my mount point is not recognized as a drive.

I tried editing fstab, changing the UUID= to LABEL=. The drives are mounted just fine at boot, but still they don't show up in the panel. Any ideas?

---

### Post by Niamor on 2007-02-14
pretty weird indeed, maybe try to use system preference, hard drive and the check that it is mounted on the right path, then unmount it and remount it. I usually use the system preference and it works quite well but will probably erase your special config in /etc/fstab

---

### Post by Crakie on 2007-02-14
Thanks, forgot to mention I already tried that. I can also mount/unmount manually.

---

