---
title: "How to recover an entire deleted partition ?"
date: 2017-09-02
forum: General Help
---

### Post by trenien2 on 2017-09-02
So I went and did it (though I'm not quite sure how): through whatever false maneuver, I deleted my entire /home/trenien folder. By the time I realized it, the system had recreated it. 
I believe there must have been 2-5 minutes between the deletion and me understanding what the problem was, but the only thing written were the new default user folders. So, hopefully, this might have screwed a few of the deleted files through rewriting over them, but not that many as I didn't do anything more, shut down the computer and restarted it under a live disk.

The computer has just finished copying over an image of the entire disk to another HDD, so it's now time to try and recover my life (part of what was deleted is backed up, but that's not the case for way too many files). Question is, how? I've been looking it up but so far, I've only found how to recover a deleted partition (as in, the partition itself doesn't appear anymore) or a single file. the partition is there and it isn't faulty as far as I know and there is no way I'm going to recover the 100s/1000s individual files by hand.

Ideally, I hope there is still a backup of the pre-delete state of the partition that I could restore, but I've no idea how to do that. any help?

Thanks

---

### Post by westie457 on 2017-09-02
Hi, do not expect miracles with this. Your best chances of recovering anything is using Testdisk and photorec. They are in the repo's (sudo apt install testdisk)
Use Testdisk to attempt recovery of a partition. If that does not recover anything try photorec.
Photorec finds file header information and saves with a number and extension. See [www.cgsecurity/testdisk](www.cgsecurity/testdisk) for more information.

---

### Post by dragonfly41 on 2017-09-02
Remember that you should not run testdisk or photorec on the same device you are trying to recover.
Run testdisk or photorec from a live CD/USB and ensure that the target device you are trying to recover is unmounted first before you start your recovery run(s).
Ensure that your LiveUSB has enough space to save the recovered content of your /home directory. It should be persistent.
An added precaution would be to first clone your target device so that at least you have a backup in case you screw up the recovery process.
If this entails buying another hard drive then so be it.  You can use it later as your backup device.

---

