---
title: "A different grub problem?"
date: 2007-01-10
forum: General Help
---

### Post by gumbald on 2007-01-10
Just installed Vista, got that working, so then went back to restore Ubuntu by booting from the Live CD. I've followed various guides that involves various guides, but when issuing the command

```
find /boot/grub/stage1
```

I get

```
Error 15: file not found
```

Any suggestions?

EDIT: When I mount my /dev/hdb1 root partition, all the "files" are green and have names such as "??.1?"

Has Vista destroyed my Ubuntu?!

---

### Post by bodhi.zazen on 2007-01-10
What do your partitions look like ?

Post the output of ```
sudo fdisk -l
```

second, to check the obvious you need to enter that command at the grup prompt:

```
sudo grub
```

will give you a prompt:

grub >

---

### Post by gumbald on 2007-01-10
Yeah, got all that. Windows does appear to have screwed my data entirely, a reinstall didn't work, presumably because my /home was also corrupted. Trying again after wiping my whole disk...

---

