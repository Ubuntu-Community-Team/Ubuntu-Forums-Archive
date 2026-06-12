---
title: "GRUB no longer lists XP since update to 7.10"
date: 2008-07-06
forum: General Help
---

### Post by Insomniac18 on 2008-07-06
So here's the story. I had Ubuntu 7.04 on this machine, and the last time I've run it before this weekend was last August. It is set up in a dualboot with XP Pro, and I use XP Pro as my primary OS. There was a power outage last  night while I was using XP, which must have corrupted the ntfs partition, since on my following reboot, when I hit XP on the grub bootloader, it said Error ## (can't remember the number but I'm gonna get 17?) and "Press Ctrl+Alt+Del to reboot." So I did this a few times and realized that XP was not going to boot.
I then started up Ubuntu which worked fine, and it asked if I wanted to update to 7.10. I let it update thinking maybe it'll fix it but it ended up being an idiotic move, since when I then rebooted and opened /boot/grub/menu.lst, the Windows entry was gone.

I then tried to see if I can atleast salvage files from the partition so I attempted to mount it via ntfs-3g. The result?

```
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

I then ran ntfsfix which outputted:

```
paras@paras-desktop:~$ sudo ntfsfix /dev/sda1
Mounting volume... Failed to load $MFT : Input/output error
Failed to startup volume : Input/output error
FAILED
Attempting to correct errors... Failed to load $MFT : Input/output error
FAILED
Failed to startup volume : Input/output error
Volume is corrupt. You should run chkdsk.

```

Any ideas, anyone?

---

### Post by EXCiD3 on 2008-07-06
If you have an XP disc/recovery disc you can do chkdsk from it. If you open /boot/grub/menu.lst there is a sample Windows entry in there that you can uncomment and use to try to boot into your Windows installation first.

---

### Post by Yuki_Nagato on 2008-07-06
```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

This took care of booting to Windows for me.  Provided your Windows installation was on the "hda0" position (the first partition).

The title is completely user preference.  You can have your title be whatever you want.

---

### Post by Insomniac18 on 2008-07-09
Thanks for all your help, but I found out the NTFS master table was corrupted. I connected it to another PC and had it in slave, and found data recovery software which helped a bit. I guess there's nothing else i can do now except replace the drive.

---

### Post by EXCiD3 on 2008-07-09
You should be able to recover your files and then just reformat the drive, no need to buy a new one.

---

### Post by Insomniac18 on 2008-07-09
Yeah I was considering that as well, but I talked to Dell Support and the rep. said that there were damaged clusters and whatnot.

Hell, if Dell is offering a free drive replacement, might as well take it.

---

### Post by EXCiD3 on 2008-07-10
> **Insomniac18 said:**
> Yeah I was considering that as well, but I talked to Dell Support and the rep. said that there were damaged clusters and whatnot.

Hell, if Dell is offering a free drive replacement, might as well take it.

haha anything free is well earned! :D just hope it doesnt happen often!

---

### Post by Insomniac18 on 2008-07-10
Amen to that!

---

