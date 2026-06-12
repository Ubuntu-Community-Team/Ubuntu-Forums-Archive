---
title: "vmware server doesn't recognize bootable cd"
date: 2007-12-12
forum: General Help
---

### Post by Dave_Man on 2007-12-12
Hi, 

For some reason my vmware server doesn't seem to recognize the bootable CDs in the drive.
Anybody had this problem?
I tried with several different CDs.

Thanks.
Dave.

---

### Post by gaten on 2007-12-13
Have you tried booting the ISO from the VM? You can specify to use an ISO image for the cdrom in the Settings menu for that particular VM. Then, once you're done, change it back to the regular CDROM. 

Sorry if that doesn't answer your question, but that seemed to be the easiest workaround to me.

---

### Post by fjgaude on 2007-12-13
After you have tried everything else, try using CTRL-C, and see what happens.

I remember I had that issue but somehow I just hit CTRL-C and the CD started loading.

Good luck.

---

### Post by Dave_Man on 2007-12-13
yea eventually I just used an ISO image.
weird though.
never mind.
Thanks guys.

---

### Post by mohtasham1983 on 2008-02-06
I'm having the same problem. I tried all combinations, but it didn't work.

I only have win xp cd and don't have any image. When I select ISO, I don't know which file to select.

This is information about my CD ROM:

*-cdrom
                description: DVD reader
                product: CDRW/DVD CDD5263
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UD91
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open

---

### Post by gaten on 2008-02-07
You can make an ISO of your WinXP cdrom by entering this into the terminal
```
dd if=/dev/cdrom of=/cdrom_image.iso
```

Then you would obviously select **cdrom_image.iso** in Vmware as your ISO file.

Hope that helps.

---

