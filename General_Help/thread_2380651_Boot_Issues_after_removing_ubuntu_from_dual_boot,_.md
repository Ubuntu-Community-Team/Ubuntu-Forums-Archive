---
title: "Boot Issues after removing ubuntu from dual boot, Boot Repair Logs"
date: 2017-12-20
forum: General Help
---

### Post by zerikas on 2017-12-20
Hi everyone.

I had a working dual boot  system with Win 10 up until a few days ago. I hadn't used my Ubuntu installation in close to a year so I decided to remove it.

Deleted the partition containing Ubuntu by formating it with Windows Diskpart and prepared a usb with windows to use to fix the boot

Tried to use to the command prompt  in the repair tools of the windows install. 
```
bootrec /fixmbr
```

The operation completed sucessfully.   Didn't work on restart. Tried again with 
```
fixboot
``` or something along those lines and it also didn't work.

Looked for more solutions and tried Boot Repair on a Ubuntu live USB. It didn't work but I didn't save the logs then.

Tried using Lilo and a terminal command  i can't remember at the moment  try to fix, to no avail. 

I tried installing Ubuntu again . After installing, the boot still didn't work for any OS

Did another boot repair and this time my computer did boot into GRUB and then only showed Ubuntu in the list. ( My keyboard also didn't work in GRUB for some reason but thats another issue)

Here is my paste logs  [https://paste.ubuntu.com/26219515/](https://paste.ubuntu.com/26219515/)

Hopefully someone can help me figure this out. Been at this for days. I just want to be able to boot into Win10. If that means keeping or removing Ubuntu I'm cool either way. Just want to keep my data and Windows install at this point.

My /dev/sdb drive was my c:/ drive with Windows and most my programs and files and /dev/sbc was my d:/ drive with some programs and other media

Thanks.

---

### Post by yancek on 2017-12-20
The grub.cfg file in your boot repair output does not show any entry for any of the windows partitions so the first step would be to boot Ubuntu and open a terminal and run:

```
sudo update-grub
```

Watch the output to see if you get a windows entry.  It should be sdb2 as that is the only windows partition with all the boot files.  If that doesn't provide a windows entry try running:

```
sudo os-prober
```

Again, watch the output and if you see windows in it re-run update-grub.  Also change the boot priority to the drive (sdc) on which you have Ubuntu installed as recommended in boot repair.

---

### Post by oldfred on 2017-12-20
You show sda as 840 SSD.
But your Windows is installed in sdb 850 SSD.

You have the typical 100MB Windows boot partition as sdb1, but also have Windows boot files in sdb2 and boot flag on sdb2. Boot-Repair normally copies boot files from Windows boot partition to main partition as most users do not even know they have a Windows boot partition and some then delete it. And there are no copies, so without Windows repair disk, difficult to fix.

I might move sdb to SATA0 or first drive on motherboard. And then plug drives in SATA port order, do not skip ports.

I might move boot flag back to 850 SSD, sdb1 or sda1, if after redoing drives.
I would reinstall Windows boot loader to 850 SSD and set BIOS to boot that drive.

You may have had BIOS set to boot sda, but fixed Windows boot on sdb?
And Boot-Repair's autofix installs grub to the MBR of every drive. Do not use autofix with multiple installs or multiple drives. In advanced mode you can select an install and the MBR to install boot loader for that install. It should fix Windows if you install boot loader to 850 SSD and set BIOS to boot that drive.

If you install grub to MBR of Ubuntu drive only with advanced options and set BIOS to boot that drive, then you have dual boot working. You then should be able to boot Ubuntu or Windows from grub. Or if Windows has issues, change BIOS to directly boot Windows perhaps it repair/recovery mode directly from MBR of 850 SSD.
Grub only boots working Windows. So if Windows needs chkdsk or if a Windows update turns the fast start up back on, you have to directly boot Windows to fix it.

shows advanced screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

