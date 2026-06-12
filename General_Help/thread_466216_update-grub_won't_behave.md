---
title: "update-grub won't behave"
date: 2007-06-06
forum: General Help
---

### Post by jintxo on 2007-06-06
Hello,

I have fiesty installed on an "internet" computer, used mostly for browsing. After upgrading to feisty, it wouldn't boot, for some odd reason which had to do with the upgrade process replacing my fstab entries with UUID=xxxxxxxxxxx entries and modifying menu.lst in the same fashion (#kopt=root=UUID=xxxxxxx).

SO to get things to boot normally I changed fstab back to my "standard" one with /dev/hda1, /dev/hdc and so on instead of the UUID=xxxxx stuff and added a "#kopt_2_6=root=/dev/hda1 ro" line to menu.lst so that update-grub would pick it up and generate my boot stanzas correctly.

Thing is update-grub is not behaving as it did in the past and it just deletes the line that I add (#kopt_2_6=root//dev/hda1 ro) and it resets to whatever it wants, ignoring my entry, deleting the line and setting all my boot stanzas to use the UUID=xxxxxx scheme.

This is kind of irritating and to get around that, for now, I have just created a static boot entry and don't use the auto-generated ones.

IS there a way to make this work "as expected" ? In other words, can I get update-grub to not delete my #kopt_2_6 line and use it when configuring 2.6 kernels? I though this was what update-grub was *supposed* to do.

Any help is greatly appreciated.

Cedric

---

### Post by jintxo on 2007-06-12
Okay it seems the UUID=xxxx thing didn't work in fstab for some odd reason at the time of upgrading.

I have gone back to that naming scheme after a while for my partitions and update-grub still doesn't do what I WANTED it to do, but what it does now is OK, since I am now using that naming scheme for my disks.

Thanks for reading.

---

