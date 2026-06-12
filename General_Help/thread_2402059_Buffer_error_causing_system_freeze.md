---
title: "Buffer error causing system freeze"
date: 2018-09-25
forum: General Help
---

### Post by paulmorabito on 2018-09-25
My home media server (Ubuntu 18.04) has been freezing occassionally for the past few months. There is no kernel panic logged or anything else in the logs so I was at a loss as to the cause. Finally, it occured when I was home and I managed to catch the error:

"buffer error on sda1 logical block 0 lost sync page write"

After this, everything freezes until I reboot. I forced an fsck at reboot but couldn't see the output (as boot.log isn't present and journalctl doesn't report it).

smartctl output is:

[https://pastebin.com/6XcGKVLN](https://pastebin.com/6XcGKVLN)

Any help would be really appreciated. Is my SSD dying or is something else causing this?

---

