---
title: "XFS_Repair Issue"
date: 2007-12-06
forum: General Help
---

### Post by Kingghost on 2007-12-06
Hello,

So I was seeing my serial link go up and down so I rebooted and everything was working fine, except my vg0 wouldnt mount. So I tried to xfs_repair it and this is the output I recieved.

slutb0x:/# xfs_repair -o assume_xfs /dev/vg0/media 
Phase 1 - find and verify superblock... 
sb root inode value 18446744073709551615 (NULLFSINO) inconsistent with calculated value 128 
resetting superblock root inode pointer to 128 
sb realtime bitmap inode 18446744073709551615 (NULLFSINO) inconsistent with calculated value 129 
resetting superblock realtime bitmap ino pointer to 129 
sb realtime summary inode 18446744073709551615 (NULLFSINO) inconsistent with calculated value 130 
resetting superblock realtime summary ino pointer to 130 
Phase 2 - using internal log 
- zero log... 

missing inbetween 

rebuilding directory inode 1225702584 
bad hash table for directory inode 1342177425 (no data entry): rebuilding 
rebuilding directory inode 1342177425 
bad hash table for directory inode 1344688512 (no data entry): rebuilding 
rebuilding directory inode 1344688512 
bad hash table for directory inode 1344689011 (no data entry): rebuilding 
rebuilding directory inode 1344689011 
bad hash table for directory inode 1347027107 (no data entry): rebuilding 
rebuilding directory inode 1347027107 
bad hash table for directory inode 1347297139 (no data entry): rebuilding 
rebuilding directory inode 1347297139 
bad hash table for directory inode 1348463898 (no data entry): rebuilding 
rebuilding directory inode 1348463898 
bad hash table for directory inode 1386426400 (no data entry): rebuilding 
rebuilding directory inode 1386426400 
bad hash table for directory inode 1407214284 (no data entry): rebuilding 
rebuilding directory inode 1407214284 
rebuilding directory inode 1409980307 
bad hash table for directory inode 1476395171 (no data entry): rebuilding 
rebuilding directory inode 1476395171 
bad hash table for directory inode 1482430980 (no data entry): rebuilding 
rebuilding directory inode 1482430980 
bad hash table for directory inode 1483051225 (no data entry): rebuilding 
rebuilding directory inode 1483051225 
bad hash table for directory inode 1485162665 (no data entry): rebuilding 
rebuilding directory inode 1485162665 
bad hash table for directory inode 1490611323 (no data entry): rebuilding 
rebuilding directory inode 1490611323 
rebuilding directory inode 1545482625 
bad hash table for directory inode 1546105138 (no data entry): rebuilding 
rebuilding directory inode 1546105138 
bad hash table for directory inode 1546563350 (no data entry): rebuilding 
rebuilding directory inode 1546563350 
bad hash table for directory inode 1576719133 (no data entry): rebuilding 
rebuilding directory inode 1576719133 
bad hash table for directory inode 1610612892 (no data entry): rebuilding 
rebuilding directory inode 1610612892 
bad hash table for directory inode 1618357762 (no data entry): rebuilding 
rebuilding directory inode 1618357762 
bad hash table for directory inode 1619798333 (no data entry): rebuilding 
rebuilding directory inode 1619798333 
bad hash table for directory inode 1669673937 (no data entry): rebuilding 
rebuilding directory inode 1669673937 
bad hash table for directory inode 1754694080 (no data entry): rebuilding 
rebuilding directory inode 1754694080 
bad hash table for directory inode 1756293956 (no data entry): rebuilding 
rebuilding directory inode 1756293956 
bad hash table for directory inode 1793985071 (no data entry): rebuilding 
rebuilding directory inode 1793985071 
bad hash table for directory inode 1879048358 (no data entry): rebuilding 
rebuilding directory inode 1879048358 
bad hash table for directory inode 1879480988 (no data entry): rebuilding 
rebuilding directory inode 1879480988 
bad hash table for directory inode 1884893322 (no data entry): rebuilding 
rebuilding directory inode 1884893322 
bad hash table for directory inode 1885854162 (no data entry): rebuilding 
rebuilding directory inode 1885854162 
bad hash table for directory inode 1888390172 (no data entry): rebuilding 
rebuilding directory inode 1888390172 
bad hash table for directory inode 1892569223 (no data entry): rebuilding 
rebuilding directory inode 1892569223 
bad hash table for directory inode 2015614187 (no data entry): rebuilding 
rebuilding directory inode 2015614187 
bad hash table for directory inode 2019037629 (no data entry): rebuilding 
rebuilding directory inode 2019037629 
bad hash table for directory inode 2027745957 (no data entry): rebuilding 
rebuilding directory inode 2027745957 
bad hash table for directory inode 2027745991 (no data entry): rebuilding 
rebuilding directory inode 2027745991 
bad hash table for directory inode 2041763187 (no data entry): rebuilding 
rebuilding directory inode 2041763187 
- traversal finished ... 
- moving disconnected inodes to lost+found ... 
disconnected dir inode 134217856, moving to lost+found 
disconnected dir inode 159404583, moving to lost+found 
disconnected dir inode 188928448, moving to lost+found 
disconnected dir inode 188935323, moving to lost+found 
disconnected inode 209057354, moving to lost+found 
disconnected inode 209057355, moving to lost+found 
disconnected inode 209057356, moving to lost+found 
disconnected dir inode 209513188, moving to lost+found 
disconnected dir inode 209513245, moving to lost+found 
disconnected dir inode 209513344, moving to lost+found 
disconnected dir inode 209513395, moving to lost+found 
disconnected dir inode 209513490, moving to lost+found 
disconnected dir inode 209513584, moving to lost+found 
disconnected dir inode 209677569, moving to lost+found 
disconnected dir inode 213712676, moving to lost+found 
disconnected inode 262129013, moving to lost+found 
disconnected inode 262129014, moving to lost+found 
disconnected inode 262129016, moving to lost+found 
disconnected dir inode 262132666, moving to lost+found 
disconnected dir inode 262141188, moving to lost+found 
disconnected inode 279860753, moving to lost+found 
disconnected inode 279860754, moving to lost+found 
disconnected dir inode 279860755, moving to lost+found 
disconnected inode 279860757, moving to lost+found 
disconnected inode 279860758, moving to lost+found 
disconnected inode 279860759, moving to lost+found 
disconnected inode 279860760, moving to lost+found 
disconnected inode 279860761, moving to lost+found 
disconnected inode 279860762, moving to lost+found 
disconnected inode 279860763, moving to lost+found 
disconnected inode 279860764, moving to lost+found 
disconnected inode 279860766, moving to lost+found 
disconnected inode 279860767, moving to lost+found 
disconnected inode 279860770, moving to lost+found 
disconnected inode 279860771, moving to lost+found 
disconnected inode 279860772, moving to lost+found 
disconnected inode 279860773, moving to lost+found 
disconnected inode 279860774, moving to lost+found 
disconnected inode 279860776, moving to lost+found 
disconnected dir inode 279874575, moving to lost+found 
disconnected inode 292512566, moving to lost+found 
disconnected inode 292512567, moving to lost+found 
disconnected inode 292512568, moving to lost+found 
disconnected inode 292512569, moving to lost+found 
disconnected dir inode 292519637, moving to lost+found 
disconnected inode 292519660, moving to lost+found 
disconnected inode 292774410, moving to lost+found 
disconnected inode 292774412, moving to lost+found 
disconnected inode 292774413, moving to lost+found 
disconnected dir inode 307451136, moving to lost+found 
disconnected inode 342075439, moving to lost+found 
disconnected dir inode 342357112, moving to lost+found 
disconnected inode 345352743, moving to lost+found 
disconnected inode 345352744, moving to lost+found 
disconnected inode 345352745, moving to lost+found 
disconnected inode 345352746, moving to lost+found 
disconnected dir inode 350201220, moving to lost+found 
disconnected dir inode 404630767, moving to lost+found 
disconnected inode 404635207, moving to lost+found 
disconnected dir inode 467834646, moving to lost+found 
disconnected dir inode 468060626, moving to lost+found 
disconnected inode 497816685, moving to lost+found 
disconnected inode 497816686, moving to lost+found 
disconnected inode 497816687, moving to lost+found 
disconnected inode 497816688, moving to lost+found 
disconnected inode 497816689, moving to lost+found 
disconnected inode 497816690, moving to lost+found 
disconnected inode 497816691, moving to lost+found 
disconnected inode 497816692, moving to lost+found 
disconnected inode 497816702, moving to lost+found 
disconnected dir inode 500814219, moving to lost+found 
disconnected dir inode 500815365, moving to lost+found 
disconnected dir inode 527158122, moving to lost+found 
disconnected dir inode 536871084, moving to lost+found 
disconnected dir inode 538001664, moving to lost+found 
disconnected dir inode 541074254, moving to lost+found 
disconnected dir inode 541664864, moving to lost+found 
disconnected dir inode 541770349, moving to lost+found 
disconnected dir inode 551347552, moving to lost+found 
disconnected dir inode 677133324, moving to lost+found 
disconnected dir inode 681949599, moving to lost+found 
disconnected dir inode 683059743, moving to lost+found 
disconnected inode 683118797, moving to lost+found 
disconnected inode 683118798, moving to lost+found 
disconnected inode 683118799, moving to lost+found 
disconnected dir inode 683118800, moving to lost+found 
disconnected inode 730956960, moving to lost+found 
disconnected inode 730956961, moving to lost+found 
disconnected inode 730956962, moving to lost+found 
disconnected inode 730956963, moving to lost+found 
disconnected inode 730956964, moving to lost+found 
disconnected inode 730956965, moving to lost+found 
disconnected inode 730956966, moving to lost+found 
disconnected inode 730956967, moving to lost+found 
disconnected inode 730956968, moving to lost+found 
disconnected inode 730956969, moving to lost+found 
disconnected inode 730956970, moving to lost+found 
disconnected inode 730956971, moving to lost+found 
disconnected inode 730956972, moving to lost+found 
disconnected inode 730956973, moving to lost+found 
disconnected inode 730956974, moving to lost+found 
disconnected inode 730956975, moving to lost+found 
disconnected inode 730956976, moving to lost+found 
disconnected inode 730956977, moving to lost+found 
disconnected inode 730956978, moving to lost+found 
disconnected inode 730956979, moving to lost+found 
disconnected inode 730956980, moving to lost+found 
disconnected inode 730956981, moving to lost+found 
disconnected inode 730956982, moving to lost+found 
disconnected inode 730956983, moving to lost+found 
disconnected inode 730956984, moving to lost+found 
disconnected inode 730956985, moving to lost+found 
disconnected inode 730956986, moving to lost+found 
disconnected inode 730956987, moving to lost+found 
disconnected inode 730956988, moving to lost+found 
disconnected inode 730956989, moving to lost+found 
disconnected inode 730956990, moving to lost+found 
disconnected inode 730956991, moving to lost+found 
disconnected inode 730956992, moving to lost+found 
disconnected inode 730956993, moving to lost+found 
disconnected inode 730956994, moving to lost+found 
disconnected inode 730956995, moving to lost+found 
disconnected inode 730956996, moving to lost+found 
disconnected inode 730956997, moving to lost+found 
disconnected inode 730956998, moving to lost+found 
disconnected inode 730956999, moving to lost+found 
disconnected inode 730957000, moving to lost+found 
disconnected inode 730957001, moving to lost+found 
disconnected inode 730957002, moving to lost+found 
disconnected inode 730957003, moving to lost+found 
disconnected inode 730957004, moving to lost+found 
disconnected inode 730957005, moving to lost+found 
disconnected inode 730957006, moving to lost+found 
disconnected inode 730957007, moving to lost+found 
disconnected inode 730957008, moving to lost+found 
disconnected inode 730957009, moving to lost+found 
disconnected inode 730957010, moving to lost+found 
disconnected inode 730957011, moving to lost+found 
disconnected inode 730957012, moving to lost+found 
disconnected inode 730957013, moving to lost+found 
disconnected inode 730957014, moving to lost+found 
disconnected inode 730957015, moving to lost+found 
disconnected inode 730957016, moving to lost+found 
disconnected inode 730957017, moving to lost+found 
disconnected inode 730957018, moving to lost+found 
disconnected inode 730957019, moving to lost+found 
disconnected inode 730957020, moving to lost+found 
disconnected inode 730957021, moving to lost+found 
disconnected inode 730957022, moving to lost+found 
disconnected dir inode 730957023, moving to lost+found 
disconnected dir inode 730975064, moving to lost+found 
disconnected dir inode 731107961, moving to lost+found 
disconnected dir inode 731173866, moving to lost+found 
disconnected dir inode 731229206, moving to lost+found 
disconnected dir inode 731317750, moving to lost+found 
disconnected dir inode 752117594, moving to lost+found 
disconnected dir inode 752117670, moving to lost+found 
disconnected inode 809433019, moving to lost+found 
disconnected dir inode 823780059, moving to lost+found 
disconnected dir inode 823780089, moving to lost+found 

fatal error -- creation of .. entry failed (117), filesystem may be out of space 

The thing is I have free space, its weird.

---

### Post by Kingghost on 2007-12-06
Hey all,

Done some more digging and forgot to add info

/dev/sda is a 300 gig drive
/dev/sdb is a 250 gig drive

across them is the LVM vg0, which has gone corrupt.

Apparently the reason everything is going to lost + found is due to my root inode being destroyed?

Please help!

---

### Post by atlfalcons866 on 2007-12-06
did you run xfs_repair with the filesystem mounted? if you did there is a good chance it is corrupted. you should never run xfs_repair or fsck on any mounted partition regardless of the filesystem.

---

### Post by Kingghost on 2007-12-06
I couldnt mount the vg0 because it was so badly error'd, so I ran xfs_repair on it

---

