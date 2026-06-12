---
title: "Server locks up while streaming video suspect hardware failure"
date: 2015-10-13
forum: General Help
---

### Post by jaskerx on 2015-10-13
Have already posted here [https://askubuntu.com/questions/684990/server-locks-up-while-streaming-video-suspect-hardware-failure](https://askubuntu.com/questions/684990/server-locks-up-while-streaming-video-suspect-hardware-failure) thought I'd double my chances. Basically having errors on ata3 wanted to make sure I've linked it to the proper sdx so I know what HD is giving me issues problem is that it links to both sda and sdb. I'm suspecting a hardware failure I'm just not sure if it could be sda, an intel 535 that is not even a month old. Sdb which is a seagate drive with lots of reallocation errors the most likely culprit since its filling up and was the drive with the video I was watching on it. Or my motherboards sata controller.

---

### Post by SeijiSensei on 2015-10-13
Install the **[smartmontools]("https://help.ubuntu.com/community/Smartmontools")** package and run a test against your drives.

I've always found streaming over Samba clunky.  I use NFS or **minidlna** to devices like phones and tablets.

---

### Post by jaskerx on 2015-10-13
Yes had a question about that too, the Kingston ssd I had before it was replaced by the Intel 535 was able to do a smart test while the drive was mounted or running. The Intel 535 drive on the other hand has never completed a smart test because all the tests (long and short) would get "manually" aborted so I just kind of gave up. Should a Intel drive be able to do a smart test while its mounted and running? Would really like to avoid shutting down the server and removing the drive to find a Windows box to hook it to just to run intels ssd toolbox.

---

### Post by SeijiSensei on 2015-10-14
If the tests abort, I'd guess the drive has hardware problems.  I'm pretty sure smartctl just reads the area on the drive where the SMART data is stored rather than actually scanning the device.

I have no SSD drives so I cannot say what is normal behavior for them.  However there's an Intel tool that runs on Linux: [https://downloadcenter.intel.com/download/23931/Intel-Solid-State-Drive-Data-Center-Tool](https://downloadcenter.intel.com/download/23931/Intel-Solid-State-Drive-Data-Center-Tool).  While it only lists RedHat and SUSE as supported operating systems, that's probably because they didn't test the software on other platforms like Debian or Ubuntu.

---

### Post by jaskerx on 2015-10-15
Thanks for the link but I've search Intel's site trying to find something that might work with the 535, the link you provided had a zip with .rpm's. The linux firmware update app does not specifically say that its compatible with the 535 series although it's compatible with the 530 series maybe Intels not keeping up the documentation or maybe it won't work. That leaves the intel ssd toolbox which is windows only. 

As an update I shutdown the server to replace the sata cable and didn't get an failed command: WRITE DMA error for about 12 hours. I realize at some point I'm going to have to pull the drive and test it and most likely either update the firmware or RMA it because it is pretty weird that it won't complete a single smart test.

---

### Post by SeijiSensei on 2015-10-15
You can convert an rpm to a deb using "[alien](https://www.howtoforge.com/converting_rpm_to_deb_with_alien)."

---

### Post by jaskerx on 2015-10-15
Thank you once again alien converted the package it installed fine however it seems that the page is up on its documentation because as far as I can tell this intel 535 drive of mine is not compatible with this software. It won't find it/detect it no matter what I do and I did read through the pdf manual, looks like the software only supports enterprise drives. I'm still going to have to pull it and try the ssd toolbox.

---

### Post by jaskerx on 2015-10-16
Well I'm not sure what to say about Intel ssd's but its like their firmware isn't compatible with smartctl I took the server down this morning and pulled the drive. Hooked it up over a sata interface (doesn't like usb) and flashed the firmware from rg20 to rg21 and ran a full diagnostic test that completed successfully using intel ssd toolbox which doesn't show up under smartctl. Hook it back to the server and boot back up nothing has changed still getting kernel errors, could this be a problem with the ubuntu kernel driver for this drive or something. The only reason this is a problem is it locks up the system while it errors out other than that the drive is working fine.

---

### Post by jaskerx on 2015-10-16
Posted over at the intel forum as well

[https://communities.intel.com/message/341164#341164](https://communities.intel.com/message/341164#341164)

---

