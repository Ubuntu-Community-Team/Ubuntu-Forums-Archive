---
title: "Video problems AFTER install"
date: 2013-10-08
forum: General Help
---

### Post by bewareofthephog on 2013-10-08
I picked up a new video card last night, radeon HD 6450.  I threw it in my PC and booted it up, there were some weird glitches, so I installed the proprietary drivers and it worked fine.  I was planning on reimaging my machine last night so after I got the video stable I did a backup of all my data and reinstalled ubuntu 13.04 x64.  The video durring install looks great.  After install at the login screen it's split in the middle.  It looks like it's trying to extend the display on the same monitor.  I tried to login to see if I could install the drivers and it hangs.  I'm now trying to boot into failsafex from grub rescue and it's hanging at recovering blocks from /dev/hdf (I thought I'd try to install the driver via command line)

Now I'm stuck, does anyone have any suggestions?

---

### Post by bewareofthephog on 2013-10-08
Fixed, I ctrl+c'd at the fsck, installed the drivers, now I'm good to go.

---

