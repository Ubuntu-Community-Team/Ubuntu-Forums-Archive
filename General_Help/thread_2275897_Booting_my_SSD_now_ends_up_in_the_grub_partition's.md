---
title: "Booting my SSD now ends up in the grub partition's intramfs"
date: 2015-04-29
forum: General Help
---

### Post by _sluimers_ on 2015-04-29
I installed Ubuntu on a new SSD, which led to the wrong SSD being booted, then I did a boot-repair.

Now my SSD is booted, but it ends up in intramfs and when I do ls, I see my /boot partition.

Boot-repair's info on my SSD below:
[http://paste.ubuntu.com/10912467/](http://paste.ubuntu.com/10912467/)

I made a video too:
[http://vid284.photobucket.com/albums/ll3/folatt/20150429_105021_zpsouxrmhna.mp4](http://vid284.photobucket.com/albums/ll3/folatt/20150429_105021_zpsouxrmhna.mp4)

---

### Post by _sluimers_ on 2015-04-29
Solved by ```
grub-install /dev/sda
```

Then it no longer went to intramfs and then once I was in I redid it with:

```

grub-update
grub-install /dev/sda
```

in the terminal.

---

