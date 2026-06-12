---
title: "Can't boot windows..."
date: 2007-02-16
forum: General Help
---

### Post by saz on 2007-02-16
Hi,

i've recently reinstalled Windows XP, of course it wiped out GRUB... i used SGD to restore it, and it worked fine, i may boot linux again, but i fail to boot windows :confused:, GRUB tells me device is not available.

i think that happens because the partitions changed when i reinstalled XP, so i think i need to update my GRUB menu.lst, but I do not know how, can anybody help me? i know this is a lamme question, but i never did anything like it, and i'm relatively new to linux :) 

this is the partition tree:

[IMG]http://img516.imageshack.us/img516/1771/gpartedjn9.png[/IMG]

hope you people can help me out :)

---

### Post by milton1 on 2007-02-16
can you post your menu.list and partition tree for the disk with windows?

---

### Post by igknighted on 2007-02-16
What version of windows are you using?  Either you have windows on a 17gb FAT32 partition or its not installed on this disk.  I wasn't aware XP could use FAT32 or be installed usefully on a disk that small.

---

### Post by saz on 2007-02-16
well i does, i've done it many times, don't know why it created that extended partition this time... i've must done something wrong... but whatever

[QUOTE="menu.lst"]
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1
[/QUOTE]

here is the extract of my menu.lst that has the windows entry, as you can see the values for the device and root are wrong, but i don't know which should i use now... that extended partition just confuses me out, anyone can help me out?

---

### Post by robcarr2 on 2007-02-16
If Windows is installed on hda5 then I believe the root should be hd0,4

---

### Post by saz on 2007-02-16
well, i've tried that already, but didn't work... =s

maybe i have to change the device too...

i've tried with /dev/hda3 and /dev/hda5... none worked...

---

### Post by saz on 2007-02-16
ok, just forget it, formatted the partition to on partition fat32, and i will install XP again... thanks anyway...

---

### Post by saz on 2007-02-16
everything working again.. =( lost every thing done yesterday...

---

