---
title: "Missing GRUB after deleting windows 7 partition"
date: 2015-08-24
forum: General Help
---

### Post by rolands2 on 2015-08-24
Hello!

So I had installed Ubuntu 15.04. and windows 7 on my samsung laptop and decided to install windows 10 on partition where windows 7 was installed and run into an error (Windows cant be installed to this disk. the selected disk has an MBR partition table. On EFI systems, Windows can only be installed to GPT disks), so I formatted and deleted that partition (which was very stupid) but it didnt helped and when I rebooted laptop instead of GRUB showing up on boot it shows black screen with some info about laptop and just keeps rebooting. So then I used ubuntu live cd to recover my deleted partiton with test disk which it surprisingly did, but i guess boot information was not recovered and problem still persists. Then i tried utility Boot-repair which stated that it succesfully installed back GRUB, but on boot it still doesnt show up, so now I have run out of options and need some suggestion how to boot into Windows or Ubuntu without wiping all data out.

PS.
I have added screenshot with my partitions. The first partition "New volume" is the one where windows 7 is installed, but I have no idea on which partition ubuntu bootloader could be installed.

Also boot-repair generated this log file:
[http://paste.ubuntu.com/12187224/](http://paste.ubuntu.com/12187224/)

UPDATE!

I managed to boot into Ubuntu by changing partition label to BOOT  to the partition where windows 7 is/was installed on gparted, but Grub doest show windows 7 as an option when booting. So any ideas have to fix that would be much appreciated.

---

### Post by oldfred on 2015-08-24
Summary report did not show any Windows to find.
Windows only boots from the primary partition formatted NTFS with the boot flag. Or sda1 thru sda4. And you must have Windows boot files. Grub2's os-prober does not use boot flag or active partition as Windows does but just looks for the boot files.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

If one of your three NTFS are the bootable partition, you need to put boot flag back on it and use your Windows repair flash drive to restore & reset the boot files & run other Windows repairs. That cannot be done from Linux. And grub only boots working Windows, so you always need a Windows repairCD or flash drive.

---

### Post by rolands2 on 2015-08-24
Yes, I thought testdisk recovered files but it only recovered the deleted partition and not files. Now after opening that partition on ubuntu its actually empty with only some recovery log files in it.

What method would be the best to recover data from that partition on ubuntu then if at all possible?

---

### Post by oldfred on 2015-08-24
If deeper search with testdisk does not find files, you alternative with Linux is photorec. I have used it. It is slow, requires lots of space on anther drive for recovered files, does not recover full file names only extensions which then requires lots of work to figure out which file is which. It also will recover deleted files. I had some text files I saved a lot and it recovered many versions which took a lot of comparisons to find most of data. Or oldfred backs up more frequently. 

       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery

[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

[URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

