---
title: "Is there any disk defragmenter running on Ubuntu?"
date: 2007-06-05
forum: General Help
---

### Post by ekb on 2007-06-05
I know that ext3 partition doesn't need to be defragmented but I have fat32 partition (it has windows XP in it) that I want to defragment. I don't want to run disk defragmenter from windows because windows is burning my laptop (my laptop gets really hot when I run windows) even running XP with normal load e.g. web browsing. So I prefer to defragment xp partition from my Ubuntu. If you know any defragmenter which runs on Ubuntu please tell me.

thank you!

---

### Post by H3g3m0n on 2007-06-05
Unfortunatly there doesn't seem to be ant fat32 defragers around for Linux, or NTFS ones (although the ntfs linux project has had one planned for years, just like actual write support (non-FUSE) that has yet to materialize) 

There is a FreeDOS FAT32 defragmenter around that apparently runs under dosemu, [http://usalug.org/phpBB2/viewtopic.php?p=82150](http://usalug.org/phpBB2/viewtopic.php?p=82150) has some basic instructions. Although its not something that would be too easy to setup.
[http://savannah.nongnu.org/projects/free-defrag/](http://savannah.nongnu.org/projects/free-defrag/)

Otherwise booting a copy of windows under Linux in a virtualized environment like qemu or vmware is probably the only other option. If you do it often enough you could try to make a special stripped down version of windows with something like BartPE or nLite.

---

### Post by ekb on 2007-06-05
If there isn't easy option then I guess i'd would have to let windows does all the defragmenting then.

thanks anyway. :D

---

