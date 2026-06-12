---
title: "Help Recovering Raid 6 Partition"
date: 2018-04-18
forum: General Help
---

### Post by jonathon-2000-uk on 2018-04-18
tl:dr;
Raid array wont mount with 'Structure needs cleaning' error. Can still access data by mounting with 'ro,noload'. Looking for help with getting the array back to healthy state.

Thanks Jonathon


long:story;
So after a faulty cable I had my mdadm raid 6 array refuse to assemble. I forced it to assemble and it assembled with 5 out of 7, I then added the missing 2 drives and it started a rebuild. Unfortunately the drives I added were added as spares! Naturally I freaked a bit, but thought that there were still 5 drives there so my data should be fine?!
However upon tring to mount I get,
```
mount: mount /dev/md0 on /data failed: Structure needs cleaning
```
So I panicked a bit more, but I at least knew not to start trying things at that point. Currently the array is still going through the rebuild. I was naturally concerned I'd lost everything, however I was able to mount it with ro,noload
```
sudo mount -t ext4 -o ro,noload /dev/md0 /data
```
And all my data seems to be there.
Now I'm assuming its not due to the rebuild that it won't mount? If after the rebuild it mounts then I'll post the update.
But until then I though it best to look for some advice first.
I'm hesitant to run fsck on a raid partition as I've run into issues with that before, but most of the help for 'Structure needs cleaning' suggests running that.
I believe mounting with 'noload' means it doesn't load the journal, so I'm hoping it might be simple to rebuild it?
So I'm just looking for some advice on what to do in this situation, as most of the advice is for fixing drives not arrays.

Thanks Jonathon

---

### Post by jonathon-2000-uk on 2018-04-18
It seems it was because of the rebuild. After it completed I am able to mount md0 and all seems well.

---

