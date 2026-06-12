---
title: "Did Ubuntu Live overwrite all 32GB of my USB?"
date: 2016-04-20
forum: General Help
---

### Post by David_rom on 2016-04-20
I may have done something very stupid. I had my files saved to a 32GB SD card. I needed 1.1GB to write Ubuntu  Live to that USB and I did so. Now that is only thing on the disk? I  may have done something with partitions an/or formatting. I have Ubuntu up and running, just need those files and it appears the 1.1GB Live is the only thing on the disk now. 

Please could someone tell me what to do. Do I just delete the Live Ubuntu? Reformat?

Also, my backup is encrypted and there is a password. Only the password  doesn't seem to be working anymore. Is there any hope here either? I  have that backup saved two places.

---

### Post by CharlesA on 2016-04-20
How did you create the live disk? It is likely doing so overwrote what was on the disk previously.

You can try recovering it or just restore from backups.

---

### Post by mastablasta on 2016-04-20
> **David_rom said:**
> I may have done something very stupid. I had my files saved to a 32GB SD card. I needed 1.1GB to write Ubuntu  Live to that USB and I did so. Now that is only thing on the disk? I  may have done something with partitions an/or formatting. I have Ubuntu up and running, just need those files and it appears the 1.1GB Live is the only thing on the disk now. 

Please could someone tell me what to do. Do I just delete the Live Ubuntu? Reformat?

Also, my backup is encrypted and there is a password. Only the password  doesn't seem to be working anymore. Is there any hope here either? I  have that backup saved two places.

you very likely formatted the USB. this is not needed. see Yumi installer for example. 

if file system is fat32 there used to be unformat tool available in MSDOS (and some later windows version). that should hopefully do the trick. there is also some recovery software available for recent windows versions.

otherwise the iso on USB takes slitghtly more than it's compressed version (on download). for example I have multiple specialist Linux distros on a 16 GB drive (using Yumi). they take about 8 GB, the rest I just use for data.

I also have a separate Xubuntu on USB together with portable virtualbox. it all takes up about 1 Gb. the rest of the disk is various files, portable apps for windows etc. etc.

in other words USB image can hold other data not related to the OS image.

---

