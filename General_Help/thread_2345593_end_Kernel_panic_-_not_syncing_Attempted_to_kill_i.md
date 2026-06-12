---
title: "end Kernel panic - not syncing: Attempted to kill init!"
date: 2016-12-05
forum: General Help
---

### Post by darkblade12 on 2016-12-05
what is wrong with this boot code that prevents me from booting into ubuntu 14.04 on a dell inspiron 1501! i worked so hard to get this up and running!
```
setparams 'Ubuntu'
recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,ms\dos1   87706e79-28d8-490d-9aa2-f21f38becf5e
else
  search --no-floppy --fs-uuid --set=root 87706e79-28d8-490d-9aa2-f21f38becf5e
fi
linux.          /boot/vmlinuz-4.2.0-42-generic root=UUID=87706e79-28d8-490d-9aa2-f21f38becf5e ro quiet splash $vt_\handoff
initrd.           /boot/initrd.img-4.2.0-42-generic

```

someone PLEASE help me! and now, bed

---

