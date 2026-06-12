---
title: "New empty external 3TB hdd -- 150,2GB used?"
date: 2013-03-12
forum: General Help
---

### Post by MrsUser on 2013-03-12
I have a new external 3tb hdd. I created a GPT partition table and formatted to ext4. When checking the properties of the partition it says 150,2GB used, so only 2,8TB are available. The partition is empty though. Is this normal? And what is eating that space?!

---

### Post by Statia on 2013-03-12
Reserved for lost+found.

---

### Post by ajgreeny on 2013-03-12
You can reduce the 5% space reserved for system activities with tune2fs if it worries you too much.

Is it formatted as a single partition?

If it is a data partition with no OS on it you may like to reduce the reserved area to something like 1 or 2%.  If it's your OS partition I would leave it alone at 5%.

---

### Post by Cheesemill on 2013-03-12
It's not for lost + found, it's used for system reserved space.

By default 5% of the space of an ext partition is reserved for roots use only in case of emergencies, for example runaway processes filling up the disk with log files.
Having a reserved space means that the system would still be able to keep running in such situations.

5% used to be a reasonable amount back when hard drives were in the 10's-100's of MB size range, but in my opinion it is far too much nowadays with TB size data drives that the OS doesn't live on anyway.

Fortunately you can alter the amount of reserved space with the tune2fs command when the drive isn't mounted, for example...
```
sudo umount /dev/sda2
sudo tune2fs -m 1 /dev/sda2
```
would change the amount of reserved space to 1% (30GB).

If this is just a data drive you can quite safely get rid of this reserved space altogether by changing it to 0%.

You can check the current status of this and much more information about an ext partition by using the list option...
```
sudo tune2fs -l /dev/sda2
```

---

### Post by MrsUser on 2013-03-12
Thanks a lot! Yes, it's a single partition, data only, no OS.

---

### Post by aarons6 on 2013-03-12
wow i did not know this and i just reclaimed over 100gb
this should be changed..

5% is way too much to 'reserve' for no purpose.

---

