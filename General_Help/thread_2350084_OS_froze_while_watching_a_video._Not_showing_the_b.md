---
title: "OS froze while watching a video. Not showing the bootloader after I restarted it."
date: 2017-01-21
forum: General Help
---

### Post by hermit05 on 2017-01-21
Hi guys,

I was watching a video and suddenly the video froze and audio kept playing. I waited for a while but it didn't sort itself out so I killed the OS by long pressing the power button as nothing else was working. When I restarted the bootloader wasn't showing.
I then booted via USB and ran boot-repair. It gave me below URL:

[http://paste.ubuntu.com/23838682/](http://paste.ubuntu.com/23838682/)

Could you guys please take a look and advise on next steps if this is solvable?!

Thanks!

---

### Post by yancek on 2017-01-21
Under this section of the output: ls -l /dev/disk/by-id, there are references to sda.  Other than that, there is no informaton on anything other than the Sandisk usb drive.  Check the BIOS to see if the drive is recognized there.  If it is, try booting the usb drive again and mounting one of the partitions on the drive to see if this is possible and if you can view your directories/files.

---

### Post by oldfred on 2017-01-21
It looks like hardware is UEFI, was Ubuntu installed in UEFI or CSM/BIOS boot mode?

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

If UEFI you have a FAT32 formatted partition for the ESP - efi system partition. That may also need dosfsck.

Hard shutdown when system is doing something almost always causes corruption. Same as Windows. Order of middle commands is not critical, so mnemonics vary.

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by hermit05 on 2017-01-22
Thanks @oldfred and @yancek
The HDD was not getting detected for some reason. I then decided to open up my laptop and take the HDD out from its socket.
Just sort of cleaned it and put it back. The laptop booted as usual with all the data intact. Perhaps dust, not sure.
Thanks again for your replies. I will remember [COLOR=#000000]Raising Skinny Elephants Is Utterly Boring ;-)[/COLOR]

---

