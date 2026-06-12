---
title: "To enlarge Ubuntu partition, how do I move swap?"
date: 2015-12-30
forum: General Help
---

### Post by maxws43 on 2015-12-30
My drive has Ubuntu, then Swap, then free space.  I read that I can enlarge Ubuntu using Gparted Live CD.  My question, if I move the Swap to the end of the free space and then enlarge Ubuntu, do I need to do anything to tell Ubuntu that I moved Swap?

---

### Post by Bucky Ball on 2015-12-30
Unless the UUID changes, no. 

Run this command:

```
sudo blkid
```

You will see something like:

```
/dev/sda7: UUID="63d86782-bff4-41c1-924f-37d093fbe371" TYPE="swap"
```

... as one of the entries. The UUID= will be different to mine above. Take note of what it is. Boot to a live session from install media, open gparted and do the resize. Once it is all back together and you have rebooted to a desktop, run 'sudo blkid' again and check the UUID is the same. If it isn't, report back and we can fix that up in the fstab. (You can also look in Gparted and see if the /swap is mounted and 'swapon' for success).

Incidentally, if you have a couple of Gb of RAM, running with no /swap is perfectly fine, so if the /swap doesn't boot with the OS when you're done, no drama. We'll just switch it on (which can be done by right clicking it in Gparted and 'swapon', but we'll make it permanent by tweaking the fstab file). If the /swap is not in your fstab file at boot, the startup might grumble about the partition. Ignore and 's' for skip if you get that. :)

---

### Post by Bashing-om on 2015-12-30
maxws43; Yeah;

When you re-create the swap partition, the UUID will be different.
run terminal command
```

sudo blkid

```
to get the new UUID of swap ... and now edit the /etc/fstab file and replace swap's UUID with the new UUID.

should be good to go.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

