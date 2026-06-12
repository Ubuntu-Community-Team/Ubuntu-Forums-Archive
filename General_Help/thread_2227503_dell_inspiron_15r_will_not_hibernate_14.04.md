---
title: "dell inspiron 15r will not hibernate 14.04"
date: 2014-06-02
forum: General Help
---

### Post by duelistjp on 2014-06-02
I know it is disabled by default in 14.04 but when i try sudo pm-hibernate my screen goes black for a moment then comes back on. nothing else happens.  Any ideas on how to get hibernate working correctly?   Don't use it often but prefer to have the system hibernate at critical power levels rather than shutdown.  This 14.04 seems a bit buggy to me I've had problems with brightness controls and firefox as well.

---

### Post by Toz on 2014-06-02
What does /var/log/pm-suspend.log say during the hibernate attempt? Feel free to post the contents of the file.

It might also be useful to run:
```
cat /var/log/syslog | grep PM:
```
...right after a hibernate attempt as well.

Prehaps there is an obvious error code being displayed that can help troubleshoot the issue.

---

### Post by duelistjp on 2014-06-02
contents say

Jun  2 14:33:19 jp-laptop kernel: [ 3443.934685] PM: Syncing filesystems ... done.
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941458] PM: Marking nosave pages: [mem 0x00088000-0x000fffff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941461] PM: Marking nosave pages: [mem 0x20000000-0x201fffff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941468] PM: Marking nosave pages: [mem 0x40004000-0x40004fff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941469] PM: Marking nosave pages: [mem 0x9ffb0000-0xa13affff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941525] PM: Marking nosave pages: [mem 0xa9dbf000-0xaaffefff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.941576] PM: Marking nosave pages: [mem 0xab000000-0xffffffff]
Jun  2 14:33:19 jp-laptop kernel: [ 3443.942377] PM: Basic memory bitmaps created
Jun  2 14:33:19 jp-laptop kernel: [ 3443.942434] PM: Preallocating image memory... done (allocated 912070 pages)
Jun  2 14:33:19 jp-laptop kernel: [ 3444.254898] PM: Allocated 3648280 kbytes in 0.31 seconds (11768.64 MB/s)
Jun  2 14:33:19 jp-laptop kernel: [ 3444.565451] PM: freeze of devices complete after 294.369 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3444.565578] PM: late freeze of devices complete after 0.125 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3444.566075] PM: noirq freeze of devices complete after 0.494 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3444.566423] PM: Saving platform NVS memory
Jun  2 14:33:19 jp-laptop kernel: [ 3444.879679] PM: Creating hibernation image:
Jun  2 14:33:19 jp-laptop kernel: [ 3444.940957] PM: Need to copy 587210 pages
Jun  2 14:33:19 jp-laptop kernel: [ 3444.940959] PM: Normal pages needed: 587210 + 1024, available pages: 952064
Jun  2 14:33:19 jp-laptop kernel: [ 3445.529550] PM: Hibernation image created (587210 pages copied)
Jun  2 14:33:19 jp-laptop kernel: [ 3444.924714] PM: noirq thaw of devices complete after 0.103 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3444.924815] PM: early thaw of devices complete after 0.079 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3445.164793] PM: Device 00:07 failed to thaw: error -19
Jun  2 14:33:19 jp-laptop kernel: [ 3445.351239] PM: thaw of devices complete after 425.933 msecs
Jun  2 14:33:19 jp-laptop kernel: [ 3445.351405] PM: writing image.
Jun  2 14:33:19 jp-laptop kernel: [ 3445.351407] PM: Cannot find swap device, try swapon -a.
Jun  2 14:33:19 jp-laptop kernel: [ 3445.351407] PM: Cannot get swap writer
Jun  2 14:33:19 jp-laptop kernel: [ 3445.429894] PM: Basic memory bitmaps freed

---

### Post by duelistjp on 2014-06-02
I ended up because of some other issues reinstalling ubuntu without a lvm to make some stuff simpler,  it seems to work fine now although I would be interested if you can help me know what was wrong though

---

### Post by Toz on 2014-06-02
> Jun 2 14:33:19 jp-laptop kernel: [ 3445.351407] PM: Cannot find swap device, try swapon -a.
To hibernate, you need a swap partition at least the same size as your memory. The system couldn't find one.

---

### Post by duelistjp on 2014-06-02
my first thought on seeing that log but that was the odd part. it had a swap partition that was larger than my mem but it was a logical partition if that makes a difference as i installed with lvm.  when i reinstalled without lvm after i completely screwed up wifi it worked fine. oh well i might find out eventually if i keep playing around with ubuntu. thanks for the help anyways

---

