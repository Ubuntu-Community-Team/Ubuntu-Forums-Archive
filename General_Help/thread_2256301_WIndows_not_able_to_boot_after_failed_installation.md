---
title: "WIndows not able to boot after failed installation of Ubuntu"
date: 2014-12-11
forum: General Help
---

### Post by max68 on 2014-12-11
Earlier today I managed to download Ubuntu and booted it successfully. I started browsing through the different options available and decided to give a shot and install Linux alongside Windows (as proposed in the setup options). The installation window froze when determining my time zone and the installation did not go through. A bit worried about my files, I quickly reboot, open up the BIOS and set my Drive with Windows OS to open first : « No bootable device »… Remembering I did have a simillar problem when updating my BIOS weeks earlier, I go back into the BIOS and switch from UEFI to Legacy (as I had to do weeks before). I reboot and the same problem occurs. I am now stuck with Linux, now fully installed on an external Hard Drive in order to not override Windows (Even though it causes me much trouble I still want to keep Linux). I have now possibility to open up Windows but it says files are (corrupted?) and that I need to insert Windows Installation disk. At that point on, I just want to recover my files as I don't really care about having Windows or not.  
 

 Here are the options I was wondering to consider :
 - Open up my laptop, take out the Drive and open the folders on my desktop
 - Cry and wait for someone to give me a little help.
 

 [http://paste.ubuntu.com/9475463/](http://paste.ubuntu.com/9475463/)
 Pastebin of me trying to get the Boot-repair app to open up my Drive.
 

 Looking forward to your responses.

---

### Post by oldfred on 2014-12-11
The desktop installer does not include all the RAID drivers, your sda & sdb are RAID.
Probably BIOS raid or "FakeRAID"

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If you add this driver, you may be able to mount your Windows, but I thought Boot-Repair automatically did that?

 sudo apt-get install dmraid

Boot-Repair did show this:

```
lrwxrwxrwx 1 root root 10 Dec 11 13:22 dm-name-isw_dcigadebjd_HDD0 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Dec 11 13:22 dm-name-isw_dcigadebjd_HDD0p1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Dec 11 13:22 dm-name-isw_dcigadebjd_HDD0p2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Dec 11 13:22 dm-name-isw_dcigadebjd_HDD0p3 -> ../../dm-3
```

Did you also leave Windows hibernated?

Or you may need BIOS set to RAID?

---

