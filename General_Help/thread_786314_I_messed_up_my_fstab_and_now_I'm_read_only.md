---
title: "I messed up my fstab and now I'm read only"
date: 2008-05-08
forum: General Help
---

### Post by macjohn on 2008-05-08
Running 7.10

I had several drives mounted, was getting some troublesome error every time I booted so I checked my fstab and noticed all of my drives had 'ro' listed at some point.  For some reason, I thought this meant read only, so I changed them all to 'rw' and rebooted.

When I did, I'm stuck at a terminal.  I'm trying to get access to my fstab but keep being told I'm in a read only file system.

I tried booting to the ubuntu disk and have tried several things there but can't seem to access my old file system to edit the fstab. 

I guess the first question is... how do I access my /dev/hda1 so I can edit my fstab file?

I'm sure there will be more stupid questions to follow... so get ready.

---

### Post by DrPppr242 on 2008-05-08
I think 'mount -o remount,rw /dev/hda1 /' will remount your filesystem with write enabled.

---

### Post by macjohn on 2008-05-08
ok, did that... thanks.  Now when I try to gedit my fstab I'm told it cannot open display.

Is there another edit tool I should be using?

---

### Post by jocko on 2008-05-08
> **macjohn said:**
> ok, did that... thanks.  Now when I try to gedit my fstab I'm told it cannot open display.

Is there another edit tool I should be using?

Try nano:```

sudo nano /etc/fstab
```

---

