---
title: "Grub won't boot windows xp"
date: 2008-04-21
forum: General Help
---

### Post by dan.sanduleac on 2008-04-21
I have three hard disks in my computer. 
Two SATA, one IDE (I don't use it right now, it's just there, plugged in).
One of the SATA disks is faulty and causes XP to often crash and reset (XP is on that drive). The XP partition only has around 7.8GB so I just made a partition of the same size on my second hard disk and just ddrescue'd the XP over.
Fdisk sees the faulty SATA disk as /dev/sda and the second, good SATA disk as /dev/sdb.
Of course, now linux sees both partitions as having the same uuid, but after I copied it into the new partition I fired up the original windows XP and it saw its partition and the new one separately (assigned a new drive letter for the new one and seems to identify them by different uuids, although I don't really know how the UUID mechanism works in Windows).

Now I made the BIOS boot from sdb, in order to boot grub, and want to use the grub that is installed on 'sdb' to boot the new xp partition (of course, it's not active, the grub partition is).
Xp_old : /dev/sda2 (active)
Xp_new : /dev/sdb4
Grub : /dev/sdb1 (active)
(by the way, hd0 = sdb, hd2 = sda in grub)

I can boot the old xp partition from grub by using the map hack, mapping hd0 to hd2 and hd2 to hd0. 
The problem is now I can't boot the new xp partition, I think using map is useless, as it is located at (hd0).
My grub commands:
root (hd0,3)      -> filesystem unknown, type 0x07 
makeactive
chainloader +1
boot
The result : everything hangs and nothing happens, not even the Windows bootloader on sdb4 will start.
Can anyone help me on this ?

Edit : similar problem here (just found it) [http://ubuntuforums.org/archive/index.php/t-80592.html]("http://ubuntuforums.org/archive/index.php/t-80592.html"), only the old hard disk wasn't left in the computer. Seems noone figured it out though.

---

### Post by Vermind on 2008-04-21
Hello,
try hd1,3 and hd2,3.
See if GRUB has numbers mixed up.

---

### Post by dan.sanduleac on 2008-04-21
Hello,
Thanks for the quick reply :)
Btw, I'm sorry if, in my being hasty, I only described the situation without posting fdisk output or anything, but I am sure that what I wrote is accurate. 
About the grub mixup, I actually thought about it :) So I checked every partition of every drive with 'root (hdx,y)' and then checked to see if the partition types match the ones on the hard disk I think I'm accessing, so i'm 100% it's sdb = hd0 and sda = hd2.

I think I should note that before, I was using just the xp bootloader on sda, as it was the default boot disk in BIOS. Now I changed it to sdb, where I already had the grub installed. It's possible these older partition uuids may get invalidated when booting the new windows xp, because now the defualt boot disk is sdb, but I think at least the windows bootloader should show up after attempting to boot sdb4 from grub.

---

### Post by dan.sanduleac on 2008-04-25
Hello,
seems noone else posted :)
I just found the solution on the web, and I'll post the link here just in case anyone else ends up on this thread.
The trick was that I had to modify four bytes in the boot record of the winxp partition to point to the new partition's starting sector on the hard disk, otherwise the boot manager wouldn't start, so the system hung.

And another thing that's not included in the tutorial below: if by any chance you first copy the xp partition, using dd or similar software, and then boot the original XP, it will recognise the new partition and assign a drive letter to it, say "N:". Now, if you make the mistake of re-copying the original XP partition to the new drive, the new XP partition, once it boots, will see itself as N: and *NOT* as C:.
Thus, when (if) you delete the original xp partition or take away the hard drive that it resided on, and then boot the xp on the newly copied partition, it will suddenly have no C: drive, and after loading the important stuff (drivers,etc) all programs will be loaded from C:. You'll know this happened if windows xp fails to load past the "welcome screen".
If you made this mistake, or that welcome screen "freeze" happened to you, read on. :)
Then, you'll have to do some registry tweaking, grab a copy of systemrescuecd, boot it, and use the 'ntpass' program provided with it to modify the registry.
[note: make sure that the *new* xp partition, the one that will need some registry modifications, is not flagged dirty, chkdsk it from windows or from within the xp setup cd recovery console.]
Ok, this message is already long, but I'll just mention that you have to load the "system" registry hive (it's a file in %windir%\system32\config), and then go to MountedDevices key. Then, you have to write down the value of \DosDrives\N: , then delete that key, and then modify \DosDrives\C: in hex-mode so that it will have the value that \DosDrives\N: had before you deleted it. This is pretty non-self-intuitive to do with the ntpass program, as it is very hard to use, but it is doable once you realise how.

Original tutorial:
[http://m.domaindlx.com/LinuxHelp/win/copyingXP.htm]("http://m.domaindlx.com/LinuxHelp/win/copyingXP.htm")

---

