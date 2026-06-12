---
title: "NVIDIA graphics driver dilemma"
date: 2007-01-14
forum: General Help
---

### Post by craz on 2007-01-14
Hi, I'm in a little bit of a dilemma.  I had a NVIDIA graphics BETA driver installed on my Ubuntu 6.10 machine.  I recently installed some OS updates, and a reason that I do not remember, I have to reinstall the NVIDIA driver.  So, when I went to get the latest BETA driver (I use it for my Beryl desktop), the installer informed me that my graphics card (an old Geforce 2 MX/MX 400) was no longer supported and that I would have to use the legacy driver, which has not been updated recently, and does not work with bery and the latest OpenGL applications. I want to find the old (maybe 1 1/2 months) BETA driver that I was using, but I do not have the version numer.  I don't know what I can do to find the latest recent driver that supports the Geforce 2 MX/MX 400 graphics card.  Thanks for any help.

---

### Post by useResa on 2007-01-14
Which version of the driver did you try to install now?
I am currently running the latest driver ([9746](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)) for Linux which was released December 2006. 
Before that I also used the BETA version ([9742](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)) which was released November 2006.

I also still do have some older versions available on my laptop (8774,8776,9625 and 9629). If you require any of these, let me know and I can try to get them to you.

---

### Post by craz on 2007-01-14
Thank you very much, that is very generous of you.  The two versions I tried to install are actually the versions that you listed, the BETA and the stable.  Problem is, I do not remember the newest normal driver that supported my graphics card.  Any way I can find out?

---

### Post by allwin on 2007-01-14
I had the same problem.  Since it was an old machine, I went over to Ebay and found a RADEON ATI 7000 AGP card which was a dandy replacement and cost $15 plus shipping.  Only trouble is, with Beryl, scrolling with Firefox or anything pushes the CPU to 100% and it's SLOWWWWWWWW.  But otherwise the rest of Beryl works.  Dunno if a switch in hardware is appealing to you, but I did it for the sake of experimentation, and got Beryl working on a box so slow I can't believe it (550Mhz P III).  BTW, Beryl would always give me BLACK SCREENS with nVidia hardware, regardless of driver.  I can't seem to find one platform around here which works 100% with Beryl.  YMMV.

---

### Post by Theimon on 2007-01-14
Check the link in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929) Maybe you can find a suitable driver using tseliot's (alberto) repositories.

---

### Post by cowlip on 2007-01-14
> **allwin said:**
> I had the same problem.  Since it was an old machine, I went over to Ebay and found a RADEON ATI 7000 AGP card which was a dandy replacement and cost $15 plus shipping.  Only trouble is, with Beryl, scrolling with Firefox or anything pushes the CPU to 100% and it's SLOWWWWWWWW.  But otherwise the rest of Beryl works.  Dunno if a switch in hardware is appealing to you, but I did it for the sake of experimentation, and got Beryl working on a box so slow I can't believe it (550Mhz P III).  BTW, Beryl would always give me BLACK SCREENS with nVidia hardware, regardless of driver.  I can't seem to find one platform around here which works 100% with Beryl.  YMMV.

oh god, that's the one I have (radeon 7x00)!  I can't believe I used to be so impressed by it.... 32mb of memory :)

Anyways, the best ones for Linux are Intel integrated graphics cards.  They are open source and supported by kernel updates.  But of course they have to be integrated into your motherboard in the first place ](*,)

---

### Post by craz on 2007-01-14
Thank you all for the quick and informative responses. :) Theimon, I clicked that link.  While the repo's install didn't work because the install does not create a custom kernel module, I put the new legacy version number into the nvidia address bar and that driver worked.  Funny, their latest legacy driver is still listed as 7184.  Well anyways, problem solved.  Thank you all.

---

