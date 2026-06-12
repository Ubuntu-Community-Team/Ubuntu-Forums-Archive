---
title: "Why negative numbers in showfsck?"
date: 2012-11-28
forum: General Help
---

### Post by jeeves on 2012-11-28
I have an Ubuntu 12.04 box on which I use suspend a lot. Recently I ran showfsck to see when its due its next error check and I got negative numbers:

$ sudo showfsck
***************************
* -100 * /-1 mount(s) until fsck for /dev/sda1
***************************
***************************
* -16 * /-1 mount(s) until fsck for /dev/sda2

Does anyone know how to interpret this? The negative values make no sense to me.

---

### Post by Dennis N on 2012-11-28
showfsck shows remaining boots / maximum before check. 

Check if the maximum count is set to -1:

If your OS is on sda1,

> sudo dumpe2fs -h /dev/sda1

Otherwise modify to the appropriate partition.

Look for "maximum mount count" in the output.

A -1 value means the checks are disabled.

---

### Post by Dennis N on 2012-11-28
The rest of the explanation:

To explain the first negative number in showfsck with fsck disabled, it's just arithmetic:

Let C = Mount Count
Let M = Maximum Mount Count 
Remaining Mounts Until fsck = (M - C + 1)
Showfsck reports (M - C + 1) / M mounts until fsck...

An example: file system has been mounted (or booted) 20 times, and maximum is set to 30, M - C + 1 = 11 and showfsck reports 11/30 mounts until fsck... (fsck happens when C > M and M > 0)

If fsck is diasbled with M = -1 (= 0 also disables)

M - C + 1 = -1 - 20 + 1 = -20

and showfsck reports -20/-1 mounts until fsck.

Note: The file system check (fsck) should be enabled if it is not. Use tune2fs to fix this and set the maximum; ask for help if needed.

---

