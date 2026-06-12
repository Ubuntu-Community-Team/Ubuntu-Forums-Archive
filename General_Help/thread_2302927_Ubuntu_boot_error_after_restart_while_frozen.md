---
title: "Ubuntu boot error after restart while frozen"
date: 2015-11-14
forum: General Help
---

### Post by dfbcon on 2015-11-14
Ok have a laptop that had been running ubuntu for a while now. Forgive bit I'm not sure of version right now.

Any way kids were playing open arena on it and it froze.
Restarted and now it says: error^ symbol 'gvub_video_adapter_list' not found. Press any key...
Uncompression error
-- system halted.

I can find nothing online containing this video adapter error so please if any one has any suggestions I'm all ears.

---

### Post by cariboo on 2015-11-14
Start in recovery mode, and at the prompt type the following command:

```
fsck /dev/sdx
```

where /dev/sdx = the partition ubuntu is installed on.

---

