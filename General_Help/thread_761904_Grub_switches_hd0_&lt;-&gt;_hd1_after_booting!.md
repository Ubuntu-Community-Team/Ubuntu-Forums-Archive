---
title: "Grub switches hd0 &lt;-&gt; hd1 after booting!?"
date: 2008-04-21
forum: General Help
---

### Post by DJTurboToJo on 2008-04-21
Hey Community,

I have a weird issue with my Grub. So, here's my setup, I'll use Grub's notation:

1x IDE harddisk, that has two partitions (after that referred to as IDE):
	(hd0,0) with NTFS where Windows is the OS, marked as boot
	(hd0,1) with NTFS, for NTFS data

Some years ago, I bought a new hard disk. This has both SATA and IDE. I use it as SATA. On this disk I installed Ubuntu, here are the partitions (referred to as SATA):
	(hd1,0): NTFS, for more data ;)
	(hd1,1): FAT 32
	(hd1,4): ext2fs -> Ubuntu, here is / and /boot
	(hd1,5): ext3fs, /home
	(hd1,6): swap

So I first had the IDE hd with Windows installed. After installing Ubuntu, GRUB got installed and I think it was in MBR of that IDE disk. Recently, I had constant problems with GRUB. It wouldnt start sometimes. Then the problem went away and came back, without any (for me) understandable reason. Mostly I got the error 18 which I could "repair" with a chksdk scan on (hd0,0). It always found some errors! And I did this quit often in the last month. Well, so I was first worried that my hard disk is degrading as I had some bad sectors on the disk. I made a ntfsclone of the (hd0,0) and then formated it and did some scans (chkdsk, badsectors). Then I put the clone back on the drive and no bad sectors anymore. So, I edited the bad blocks file, as this was cloned, too and finally had no bad sectors anymore. But the problem that the GRUB menu wont load still resisted. And each time I had this issue I booted into Recovery Console for Windows did a check with chkdsk, found some problems, chkdsk corrected them and Grub booted again. It's important that no bad sectors were found after formatting this disk. There were only unused entries for file 0x9. The message that I now get is always (sorry it's in German):

Dateisystem auf \DosDevices\C: wird überprüft.
Der Typ des Dateisystems ist NTFS.
Die Volumebezeichnung lautet WinXPSystem.
5 nicht verwendete Indexeinträge aus Index $SII der Datei 0x9 werden aufgeräumt.
5 nicht verwendete Indexeinträge aus Index $SDH der Datei 0x9 werden aufgeräumt.
5 nicht verwendete Sicherheitsbeschreibungen werden aufgeräumt.
CHKDSK überprüft USN-Journal...
Die Überprüfung von USN-Journal ist abgeschlossen.
CHKDSK überprüft Dateidaten (Phase 4 von 5)...
Dateidatenüberprüfung beendet.
CHKDSK überprüft freien Speicherplatz (Phase 5 von 5)...
Verifizierung freien Speicherplatzes ist beendet.

  20482843 KB Speicherplatz auf dem Datenträger insgesamt
   9846104 KB in 54480 Dateien
     17244 KB in 4452 Indizes
         0 KB in fehlerhaften Sektoren
    255631 KB vom System benutzt
     65536 KB von der Protokolldatei belegt
  10363864 KB auf dem Datenträger verfügbar

      4096 Bytes in jeder Zuordnungseinheit
   5120710 Zuordnungseinheiten auf dem Datenträger insgesamt
   2590966 Zuordnungseinheiten auf dem Datenträger verfügbar

Well, it just cleaned up some unused index entries for file 0x9 and the number of unused index entries sometimes varies in those error messages but it's always file 0x9. And this message is always always the same that I got. I couldn't find which this file 0x9 is but the problem was again and again this file. Well, after chkdsk did its job I could boot again using GRUB.

I also wrote the GRUB into the second hard disk, because I thought maybe this will help. Well, it didnt do a thing. This is what I did (from inside Ubuntu):
	sudo fdisk -l -> the I got the list of drives that I wrote you in the beginning
	sudo grub
	> find /boot/grub/stage1 -> hd1,5
	> root (hd1,5)
	> setup (hd1) respectively setupt (hd0)
	> quit

Then I had GRUB on both hard disk but this didn't fix my starting problems. Sometimes I could boot and then suddenly I couldn't as the GRUB menu wouldn't start. To ensure if the MBR of both hds was written I unplugged one after the other and GRUB was in both MBRs. Obviously I couldn't boot without SATA as there is /boot.

So, this weekend I tried to fix this. I wanted to delete the MBR for (hd0), so that this IDE hard drive just goes to Windows. I also wanted to write a new MBR to the SATA drive. I used the newest Super Grub Disk to do this. 

The first thing I did was booting with SGD into Windows, just to check. And after that the GRUB menu from the hard disks showed up but I couldn't boot, for UBUNTU the error 22: No such partition arised. Ok, I was a bit suprised but with this SGD I was able to boot into Windows and as well as loading the menu.lst from (hd1,5) to boot normally. I could even use the option boot from MBR, I choose hd1 and everything worked. So I let SGD repair my MBR but without the CD I always got the error 22.

And here's the thing I dont understand. When I boot with the SGD I can start the grub console. In there hd0 is IDE and hd1 is SATA, as it was always in Ubuntu. So when I repair the MBR this setting is used. The problem is that grub things that hd1 is SATA and hda0 is my IDE, however when I just boot without SGD IT IS NOT. Then hd0 is SATA and hd1 is IDE. I found this when booting from MBR of my SATA drive without SGD and going into grub console. So, what I did is to manually change the root(hd?,?) parameter in all my GRUB boot menu entries. This worked for UBUNTU but not for Windows. 

Does anybody know how to fix the Windows entry?

It is just the usual entry with root, makeactive and chainloader +1. As I said on my IDE hd there's no GRUB installed anymore, as I also did a fixmbr and then a fixboot from inside the Recovery Console. So maybe the problem is that it looks at sector 1 to boot, but I really have no idea!?

And my second problem is that grub thinks that hd0 is SATA and hd1 is IDE while booting. But using Ubuntu (which I can boot now with the Grub menu from MBR of my SATA disk) or using the SGD hd0 is IDE and hd1 is SATA. I used df /boot and  df / to get /dev/sda6 which is in grub's notation (hd1,5)  and cat device.map to find that hd0 is IDE (here /dev/hda) and hd1 is SATA (here /dev/sda). EDITED: Maybe I change this device.map file, or is this a bad idea?

Well, for now I just switch the boot order in my BIOS to either load Windows or Ubuntu, but this is just an work around.

Are there any suggestions what to do, or any hints, tips or anything you want to tell me - just post your thoughts.

Thanks
TurboToJo

---

### Post by -Zeus- on 2008-04-21
First off, how did you manage to get 5 primary partitions on your hard drive?

---

### Post by DJTurboToJo on 2008-04-21
Oh, sorry. So on IDE there is one primary and one extended. And on SATA there are two primary partitions and then an extended partition under which I have these two ext3fs and the swap partition. That's why the numbers arent increasing consecutively.

---

### Post by DJTurboToJo on 2008-04-22
I changed my /boot/grub/device.map

the old setting was:
   (hd0)    /dev/hda
   (hd1)    /dev/sda

and I changed it to:
   (hd0)    /dev/sda
   (hd1)    /dev/hda

However, when I'm in Ubuntu grub tells me that hd0 is my IDE drive. 

Is there a way to tell grub that hd0 is SATA all the time and not while booting hd1 and then in my OS - or even using the Super Grub Disk - hd0.

---

