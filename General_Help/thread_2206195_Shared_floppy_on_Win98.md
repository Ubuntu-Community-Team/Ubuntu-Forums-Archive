---
title: "Shared floppy on Win98"
date: 2014-02-17
forum: General Help
---

### Post by pouldney on 2014-02-17
I have a Win98 computer with a floppy disk shared on the network.
   When i try  to access the floppy from ubuntu 12.04 over the network
Nautilus sees the disk but none of the files on it.
If I right click and click properties ,It shows as type folder
   and file system type cifs
     It seems nautilus thinks it is a folder not a disk..
   Files on Other shared folders on the same computer are assessable.
   When I boot Windows8 I can see and open files on the same floppy.
     Yes I know floppies are outmoded,and there is another way I can get the data off
   it.  I just like things to work!!
   
      I did some more testing on this problem. I tried another floppy disk and
 was able to see and read the files
  It seems that if there are only a couple of small files on the disk,nautilus does
  not see them,but if there is a large file it does.
   This does not happen on shared folders only the floppy disk

---

### Post by mastablasta on 2014-02-18
almost everything is a file in linux.

i am not sure how well samba is supported for win98. and i forgot how one arranges sharing in win98. convince samba it is a drive it's looking at.

i still have floppy drives on mashcines but no win98

---

