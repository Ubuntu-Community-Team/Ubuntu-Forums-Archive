---
title: "systemd and /tmp"
date: 2015-08-06
forum: General Help
---

### Post by Marcaitus on 2015-08-06
So as far as I know Ubuntu and its derivatives use systemd and I recall  in earlier versions prior to the one I'm running now (15.04), there was a  /tmp mount line in fstab but now systemd mounts it automatically as  tmpfs (as I understand). The thing is though when I create a file with  ```
dd if=/dev/zero of=FILE bs=1G count=1
``` doing free -m will  show that the cache has gone up one gigabyte which is what's expected,  the problem is that my disk monitor is saying dd is writing to disk,  even my dirty page monitor is writing it up as going to disk, I know  because when I mount /tmp as tmpfs explicitly in fstab when I do a dd  the dirty pages won't go up and the disk monitor won't register it.

What's going on with this? Is systemd using RAM or the disk? I should  mention that I'm doing this during a fresh boot so I'm nowhere near  using all my RAM or anything like that. I've looked it up myself and  everywhere is saying that /tmp gets mounted as tmpfs on systemd by  default but my couple "tests" are saying otherwise. /tmp is not listed in df.

Now I could go ahead and just mount /tmp in fstab which is what I will  do if this doesn't work out but I'd rather not because right now /tmp is  sharing the trash bin so I don't have to go in there and clear it out  separately and when I did mount /tmp in fstab and eventually unmounted  it, the files that were there before the mount were still there... and  finally I'd like to learn.

---

### Post by nerdtron on 2015-08-06
from what I remember /tmp is on disk even now on systemd. and tmpfs is different from /tmp

---

### Post by Marcaitus on 2015-08-06
> **nerdtron said:**
> ... and tmpfs is different from /tmp

I know they're different. I think you're right that it's going to disk, I think the reason the cache went up is cause it's still in there even when it gets written out cause there's no reason for it not to. Also I did a df -h before and after dd and it's changing size. All signs point to it going to disk, I'll mark it as solved.

---

