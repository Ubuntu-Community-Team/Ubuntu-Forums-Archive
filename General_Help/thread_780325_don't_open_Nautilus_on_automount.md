---
title: "don't open Nautilus on automount?"
date: 2008-05-03
forum: General Help
---

### Post by excogitation on 2008-05-03
How can I either get Nautilus to autoclose on unmount,
or prevent Nautilus from opening when automounting e.g. partitions from an SD-card.

Also I'm interested in the behaviour when changing partitions on e.g. an SD-card
because I'm experiencing "weird" behaviour
(or maybe it's just my lack of knowledge/understanding).

Example:
I have an SD-card with 2 partitions like
Primary 1: 32MB fat32
Primary 2: 64MB ext3

now I unmount those and change it to
Primary 1: 16MB fat16
Primary 2: 80MB ext2

with fdisk (or gparted) and
format those accordingly...

then do partprobe or replug,
if I now write to those partitions then
replug the SD-card -> the files are gone/
or I can't modify the files/add new files.

I don't quite understand that.

---

### Post by DixieWolf on 2008-05-03
to stop auto-opening nautilus, 
open a terminal and type

gconf-editor

click the arrow next to 'apps' on the left,
find 'nautilus' under that, and click the arrow
next to nautilus, then under nautilus, 
click 'preferences'. on the right-hand side of the editor,
it will bring up a list of preferences. uncheck
'media_automount_open'

then close, and that should do it.
I'm not sure about the weird partition behavior though

---

### Post by excogitation on 2008-05-03
Thank you (was driving me nuts in addition to the partition problem when I had to close multiple of those windows).

Regarding the partition problem - 
it seems to be essential to reread the partition table information before formatting either by using partprobe (or turning of caching using sync when mounting?) also unmounting the partitions before unplugging helps avoiding errors with unwritten files :-)

---

### Post by DixieWolf on 2008-05-03
lol, occasionally that helps.

---

