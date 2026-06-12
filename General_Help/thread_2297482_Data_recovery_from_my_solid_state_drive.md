---
title: "Data recovery from my solid state drive"
date: 2015-10-04
forum: General Help
---

### Post by tomaasj on 2015-10-04
Dear Ubuntu people,

need some help on data recovery.

Suddenly got the following message when starting up the laptop:

'error hdo out of disk'

I read some threads on the topic but but was not able to re-install Grub, which was recommended.

Next option is to rescue my data from this Solid State Drive (SSD).

Removed the SSD and hooked it up on my other laptop through a USB connection.

The disk image appears in the dock but I am not able to open it.

Trying to get to it through the terminal with the cd command gives me a 'Permission denied'.

How to get to my documents on the SSD ?

If not for the integrity of the SSD it must have to do something with the ownership of the SSD.


Please, can anyone of you give me advice on how to proceed ?

Tomaasj

---

### Post by tomaasj on 2015-10-04
I was able to use the CHOWN command on the mounted SSD.

This time no 'Permission denied' message, however the ls command does not reveal files and folders.

What to do ?

---

### Post by tgalati4 on 2015-10-04
Install *testdisk* and run it.  Make sure you have another large disk available to receive the recovered files.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

