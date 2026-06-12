---
title: "Problems with tat"
date: 2007-06-06
forum: General Help
---

### Post by woland on 2007-06-06
Hello people!

I'm playing with an embedded arm-debian system and using Feisty on my host PC.

I've made a tar archive of the external flash memory from the embedded system.
As things happened, I now need to extract this archive back to the flash device.

Here is where the problems start.
Either if I use the "sudo tar -xvzf /path/archive_filename" or with file roller (as root), I have the same error message:

```
tar: usr/lib/perl/5.8: Cannot create symlink to `5.8.8': File exists
tar: usr/share/vim/vimcurrent: Cannot create symlink to `vim70': File exists
tar: usr/share/perl/5.8: Cannot create symlink to `5.8.8': File exists
tar: usr/share/groff/current: Cannot create symlink to `1.18.1': File exists
tar: usr/share/doc/vim-tiny: Cannot create symlink to `vim-common': File exists
tar: usr/share/doc/ncurses-bin: Cannot create symlink to `libncurses5': File exists
tar: usr/share/doc/ncurses-base: Cannot create symlink to `libncurses5': File exists
tar: usr/share/doc/perl-base: Cannot create symlink to `perl': File exists
tar: usr/share/doc/libstdc++6: Cannot create symlink to `gcc-4.1-base': File exists
tar: usr/share/doc/dselect: Cannot create symlink to `dpkg': File exists
tar: usr/share/doc/libgcc1: Cannot create symlink to `gcc-4.1-base': File exists
tar: usr/share/doc/debconf-i18n: Cannot create symlink to `debconf': File exists
tar: Error exit delayed from previous errors
```

Any ideas on how to fix this?

---

