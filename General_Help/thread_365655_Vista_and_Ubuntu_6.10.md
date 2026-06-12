---
title: "Vista and Ubuntu 6.10"
date: 2007-02-19
forum: General Help
---

### Post by ale52 on 2007-02-19
I've installed Vista Release Candidate 1 on a test box.  It stinks but I need to play with it to learn it as I know people will make the awesome mistake of putting it on their computer and I have to fix it. :lolflag: 

Anyway, I'm trying to set up Ubuntu 6.10 on the same computer as dual boot.  I'm getting the following error messages [paraphrased]:

"...Expected null handler on exit" and "Buffer i/o error on device hda logical block 357561"

I'm still too new to Linux to figure this out.    Any advice is appreciated.

Alan <>< :)

---

### Post by highneko on 2007-02-19
You're getting this message from grub when attempting to boot something? What os is your master drive and what os is your slave? What order did you install these? Good luck.

---

### Post by LostShootingStar on 2007-02-19
Sounds like a bad hard drive...

---

### Post by brokencrystal on 2007-02-20
I have a Dell Inspiron 1501 and when I would try to install Ubuntu Edgy, it would error out every time I tried to load the boot CD.  It would never boot.  It would just give me a soft CPU lock error.  I found that there is an error where if you have an SD card in the built-in slot, it will do this every single time.  I think the problem is with Linux, because Windows Vista has absolutely no problems with this.  Anyway...

Now I wanted to dual boot Vista and Ubuntu Edgy.  I first installed a clean install of Vista.  I then removed the SD card.  Then I booted the Ubuntu Live CD.  I had to use option pci=nomsi to install it as it has a 2.5" laptop SATA drive.  I adjusted the size of my Windows partition.  Everything went perfect except, in the grub boot menu, it will not allow me to boot Vista now.  Maybe because Vista is new and grub doesn't know how to handle it?  Ubuntu boots fine.  I tried to edit the /boot/grub/menu.lst to get Vista to boot from the SATA drive, but I had no luck.  (Maybe I am not doing it correctly)  I uncommented the part of the file that refers to booting Windows, and now I see it in the boot menu and can try to boot to it, but now it comes up with the error:  NTBLDR not found or something like that...  Forgot now as I just installed Vista back on it. 

Has anyone ever done this before?  Does anyone know how to do such a thing?  Thanks in advance!

---

### Post by ale52 on 2007-02-20
> **highneko said:**
> You're getting this message from grub when attempting to boot something? 

Yes.  I have only 1 drive installed.  It is partitioned with an NTFS partition (Vista) and partition for the Linux swap file and a ext3 partition for the Linux os.

What os is your master drive and what os is your slave? 

Vista is on the master drive.  There is no slave drive.

What order did you install these? 

As stated above, I partitioned the drive with gparted (from mini-cd), then installed Vista on the NTFS partition, then attempted to install 6.10 from cd.  Error messages followed.

Good luck.

BTW - I've installed Windows XP and Ubunto 6.10 on a separate drive in the same machine without error.  They play nice. :KS 

Alan <>< :)

---

### Post by ale52 on 2007-02-20
> **LostShootingStar said:**
> Sounds like a bad hard drive...

Nope...I've installed Ubuntu and Vista at separate times without any error messages.

Alan <>< :)

---

### Post by brokencrystal on 2007-02-20
Yes, I can successfully install either Vista or Ubuntu on this PC with no problems. (Just not dual boot)  

I can install WinXP and Ubuntu just fine normally without any issues...  (Although I have not tried it on this PC due to licensing reasons)   I think grub (on Ubuntu Edgy) doesn't know how to handle Vista yet...  not sure though.

---

