---
title: "how can I clear my mount points when fusermount exits with code 256?"
date: 2013-03-10
forum: General Help
---

### Post by gotnexusbluz on 2013-03-10
Why have all the mtp applications I've tried crashed this way? How do I clear my "mount points", and what does that mean anyway?

The only time this error ever failed to stop me from mounting my phone is when I had an erratic connection. So I have gone as advised by installing mtp, mtpfs, libmtp9, libfuse2,  mtp-tools (so that I could use mtp-detect) and also I have installed go-mtpfs (which crashed with the same error as mtp, mtpfs). I connected my phone, ran mtp-detect, and when that completed without an error I ran mtp, mtpfs, or go-mtpfs on my NexusDrive. All crashed with the same error:
```
2013/03/10 21:02:59 mount failed: fusermount exited with code 256
```
A google search found very little on this error other than that it was tripped by the mount points not being empty. No explanation of what that means for the prior asker of that question, just the advice to try creating a new directory. So I did that too: it seemed a bit silly, but I created a new mount folder Android_Device, and all three mtp programs crashed trying to mount this drive too. Can anybody explain this?

---

