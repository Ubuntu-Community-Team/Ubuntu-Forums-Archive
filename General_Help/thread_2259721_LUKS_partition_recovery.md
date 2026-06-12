---
title: "LUKS partition recovery"
date: 2015-01-06
forum: General Help
---

### Post by hexedone on 2015-01-06
I'm forced to open new thread since this [http://ubuntuforums.org/showthread.php?t=1643334&page=2](http://ubuntuforums.org/showthread.php?t=1643334&page=2) is inexplicably closed.

I was following the advice in that thread because my problem is very similar. A drive with 2 partitions - 1st is plain ext4, second is encrypted LUKS.
The partition table has been overwritten. I've found the beginning of the second partition  , which i need to recover, thusly:

#hexdump -s 400000m -C /dev/sdc | grep LUKS
61d3dec850  79 c8 81 6d e5 4c 55 4b  53 40 49 aa 29 df de d7  |y..m.LUKS@I.)...|


then:

#losetup -o 0x61d3dec850 -r -f /dev/sdc
#losetup -a
/dev/loop0: [0005]:477209 (/dev/sdc), offset 420166420560


ok so far, then this problem pops up:

#cryptsetup luksOpen /dev/loop0 luksrecover
Device /dev/loop0 is not a valid LUKS device.


Please advice how to proceed. Is it wrong offset? Should I seek for the magic number 0xEF53 identifying ext4 as adviced here [http://unix.stackexchange.com/questions/103919/how-do-i-find-the-offset-of-an-ext4-filesystem](http://unix.stackexchange.com/questions/103919/how-do-i-find-the-offset-of-an-ext4-filesystem)    ?

Mind you it's a 1TB drive so please I need an advice that does not force to scan the entire drive ( hours and hours) all over again if possible.
Thanx in advance.

---

