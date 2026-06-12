---
title: "Ubuntu 12.10 does not recognise working partitions"
date: 2013-02-03
forum: General Help
---

### Post by quailstorm on 2013-02-03
Hello guys! I'm back. [This]("http://ubuntuforums.org/showthread.php?t=2098322") was my previous issue. I solved it with dist-upgrading. Currently my system is stable and fast. Kernel 3.7 and nVidia driver 313.

But after upgrading, my computer was unable to boot anything. GRUB2 you know...
I've got 3 HDDs in my PC.
80GB: Ubuntu 12.10/Vista x64
1TB: data
500GB: XP/win7/data

The MBR was stored on the 80GB one, and the Windows MBR was on vista's partition. I use EasyBCD so I was able to get back to grub 1.99 from BOOTMGR.

After being unable to use my PC, I used a Lenovo repair disc for Win7. I got an MBR to the Win7's partition, and vista was working too. I added in EasyBCD on Win7 the XP and GRUB2 entries, and they work. Currently, my PC starts with BOOTMGR, and I can choose GRUB2 from here.

So what's my issue?

Ubuntu doesn't recognise the partitions of the 500GB HDD...
What can I do? XP and 7 works. All 3 installed types of windows knows what's on the HDD, but linux doesn't. I tryed to CHKDS /b the 3 partitions 500GB HDD but passed, success, and same again.

Here it is how GParted sees the situation:
[IMG]http://img685.imageshack.us/img685/562/notrecognisedpartition.png[/IMG]

I don't want to lose any data, it's important!

Please help me if you have any ideas.

---

### Post by oldfred on 2013-02-03
Better to use screen shots and attach with paperclip. Those with slower Internet may have issue with your large pictures.

Post this:

sudo fdisk -lu

Did you change partitions on sdd? 
Does one of the Windows partitions need chkdsk. I once had a working XP install but gparted would not show it. Ran chkdsk, gparted showed it and it booted XP a bit faster.

---

### Post by quailstorm on 2013-02-03
```
Disk /dev/sda: 82.3 GB, 82344050176 bytes
255 fej, 63 szektor, 10011 cilinder, összesen 160828223 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Lemezazonosító: 0xa8a8a8a8

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sda1   *        2048    74778623    37388288    7  HPFS/NTFS/exFAT
/dev/sda2        74778624    78778367     1999872   82  Linux lapozó / Solaris
/dev/sda3        78780414   160827391    41023489    5  Kiterjesztett
/dev/sda5        78780416   160827391    41023488   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000200658432 bytes
255 fej, 63 szektor, 121600 cilinder, összesen 1953516911 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Lemezazonosító: 0x97be5b6a

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sdc1   *          63  1023260174   511630056    7  HPFS/NTFS/exFAT
/dev/sdc2      1023260175  1953503999   465121912+   f  W95 kiterj. (LBA)
/dev/sdc5      1023260238  1534817969   255778866    7  HPFS/NTFS/exFAT
/dev/sdc6      1534818033  1953503999   209342983+   7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 fej, 63 szektor, 60801 cilinder, összesen 976771055 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Lemezazonosító: 0x49de49dd

Ez nem t&#369;nik partíciós táblának
Valószín&#369;leg nem a megfelel&#337; eszközt választotta ki.

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sdd1   ?          63   123138224    61569081    7  HPFS/NTFS/exFAT
/dev/sdd2       123138225   976751999   426806887+   f  W95 kiterj. (LBA)
/dev/sdd5       123138288   328416794   102639253+   7  HPFS/NTFS/exFAT
/dev/sdd6       328416858   976751999   324167571    7  HPFS/NTFS/exFAT

```

> Ez nem t&#369;nik partíciós táblának
Valószín&#369;leg nem a megfelel&#337; eszközt választotta ki.
This seems not to be a partition table, perhaps you choose the wrong device. (bad translation by me)

Partitions on sdd are the same for 2,5 years. So no change.
I ran chkdsk as I mentioned in the first post. With Win7, on the whole sdd.

The screenshot is 76kbytes, so I don't think it would be an issue...

Thanks for helping.

---

### Post by oldfred on 2013-02-03
I am not sure why it is saying that, usually it then does not show a partition table or it looks like random data parsed to be a table. Yours looks ok?

I might run chkdsk on each partition, not drive.

       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdd > PTsdd.txt


And post PTsdd.txt

---

### Post by quailstorm on 2013-02-04
```
# partition table of /dev/sdd
unit: sectors

/dev/sdd1 : start=       63, size=123138162, Id= 7
/dev/sdd2 : start=123138225, size=853613775, Id= f
/dev/sdd3 : start=        0, size=        0, Id= 0
/dev/sdd4 : start=        0, size=        0, Id= 0
/dev/sdd5 : start=123138288, size=205278507, Id= 7
/dev/sdd6 : start=328416858, size=648335142, Id= 7
```

You cannot run CHKDSK on a physical disk,(sdd) but on a driver with an available drive letter.
So I ran them (from the point of win7's view) on C:\, D:\, E:\
With: chkdsk e: /b

---

### Post by oldfred on 2013-02-04
I thought it was /r?

       chkdsk c: /r
    
       You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by quailstorm on 2013-02-04
[http://technet.microsoft.com/en-us/library/cc730714(v=ws.10).aspx]("http://technet.microsoft.com/en-us/library/cc730714(v=ws.10).aspx")

> /b
NTFS only: Clears the list of bad clusters on the volume and rescans all allocated and free clusters for errors. /b includes the functionality of /r. Use this parameter after imaging a volume to a new hard disk drive.

And /r includes /f. On XP U sed /x in the past, but that's OFF topic.
WINNT6.x has improved CHKDSK than WINNT5.1.

---

### Post by oldfred on 2013-02-04
Thanks for the update on chkdsk.  I only had XP and never booted with 7 or 8.


Back to original issue. Partition table still looks ok. Gparted screen is saying something about label. You you have a character that is not recognized? I know once I started using Linux I stopped using spaces, but you may have a foreign character that causes issues?

Post this to see labels also, post in code tags to preserve format:

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

    
I know in mounting partitions with fstab we suggest the windows_names option.
       UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by quailstorm on 2013-02-04
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    vista64  /media/vista64 06D3E71C4EBF8A22
/dev/sda2  swap             <swap>         0c968750-4553-4bc8-8220-cd45ba08bd50
/dev/sda5  ext4             /              9412058d-8553-4256-823e-c9bcb0578964
/dev/sdc1  ntfs    steamdata /media/steamdata D6B028FEB028E729
/dev/sdc5  ntfs    vista    /media/vista   BA0834350833EF4F
/dev/sdc6  ntfs    ubuntu   /media/ubuntu  822CE46B2CE45C23

```

I can't see any of the 500GB WD HDD's partitions...
The required labels are: none(UUID) for XP, Win7 for Windows7, data for the last one.
Here the two NTFS partitions called vista and ubuntu, were never used as OS storage. I filled them too quickly, so I had to install these operating systems to an another HDD...

Is there any partition repair tool on linux, like FSCK, but for NTFS? Maybe it could help if CHKDSK doesn't.
I ran MBR from Windows partitions before and had no problems on linux...

---

### Post by oldfred on 2013-02-04
There is or was ntfsfix, but it only does really minor things and sets the chkdsk flag. If flag is set or hibernation flag is set then Linux will not normally mount a NTFS partition.
Since drive is shown, I assume it is in BIOS. Have you looks with Disk Utility to see if drive has any issues.

fdisk did show sdd, and showed what looks like good partitions.

You can try this, just to see what fdisk does. Do not do w if it does not seem ok.
       this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sdd
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

---

### Post by quailstorm on 2013-02-04
```
Parancs (m = súgó): x

Szakért&#337;i parancs (m = súgó): f
Nincs teend&#337;. A sorrend már helyes.


Szakért&#337;i parancs (m = súgó): m
Parancs M&#369;velet
   b   az adatok elejének mozgatása egy partícióban
   c   a cilinderek számának módosítása
   d   a partíciós tábla nyers adatainak kiírása
   e   kiterjesztett partíciók felsorolása
   f   partíciósorrend javítása
   g   IRIX (SGI) partíciós tábla létrehozása
   h   a fejek számának módosítása
   i   a lemezazonosító módosítása
   m   ezen menü kiírása
   p   a partíciós tábla kiírása
   q   kilépés mentés nélkül
   r   vissza a f&#337;menübe
   s   a sávonkénti szektorok számának módosítása
   v   a partíciós tábla ellen&#337;rzése
   w   a tábla lemezre írása és kilépés

Szakért&#337;i parancs (m = súgó): f
Nincs teend&#337;. A sorrend már helyes.


Szakért&#337;i parancs (m = súgó): r

Parancs (m = súgó): p

Disk /dev/sdd: 500.1 GB, 500106780160 bytes
255 fej, 63 szektor, 60801 cilinder, összesen 976771055 szektor
Egység: szektorok 1 * 512 = 512 bájt
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Lemezazonosító: 0x49de49dd

Ez nem t&#369;nik partíciós táblának
Valószín&#369;leg nem a megfelel&#337; eszközt választotta ki.

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sdd1   ?          63   123138224    61569081    7  HPFS/NTFS/exFAT
/dev/sdd2       123138225   976751999   426806887+   f  W95 kiterj. (LBA)
/dev/sdd5       123138288   328416794   102639253+   7  HPFS/NTFS/exFAT
/dev/sdd6       328416858   976751999   324167571    7  HPFS/NTFS/exFAT

Parancs (m = súgó): v
Remaining 19241 unallocated 512-byte sectors

Parancs (m = súgó): w
A partíciós tábla módosítva!

ioctl() hívása a partíciós tábla újraolvasásához.
Adatok kiírása a lemezekre.
quail@STORMINTER-8:~$ sudo fdisk /dev/sdd

```

What does option W? Where does it writes the partition table. I heard usage on the 80GB HDD, but where is the output file?
What setting can be wrong in BIOS? I havent changed anything there ages ago...
We have to find out why it is bad for Ubuntu, that I used the repair disc. First time when I used it, it recognised Vista as windows 7, and MBR was on the same HDD as GRUB1.99. But now the situation is different you know...

> Nincs teend&#337;. A sorrend már helyes. Nothing to do, the order is correct.

---

### Post by oldfred on 2013-02-04
The f does reorder partitions if they are not in order on drive. In some cases that can cause issues where device like /dev/sda3 becomes /dev/sda2. But your partitions are in order so that command is not really even required.

You could just try the w to see if it writes. The backup you made with sfdisk would allow you to restore if it creates issues. 

Partition tables are in the MBR, near the end of the MBR as boot code is in the beginning.

       Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

    
But everything you show looks normal, so I do not understand errors either.

---

### Post by quailstorm on 2013-02-04
> quail@STORMINTER-8:~$ sudo ntfsfix /dev/sdd1
Failed to determine whether /dev/sdd1 is mounted: No such file or directory
Mounting volume... Failed to access '/dev/sdd1': No such file or directory
Error opening '/dev/sdd1': No such file or directory
FAILED
Attempting to correct errors... Failed to access '/dev/sdd1': No such file or directory
Error opening '/dev/sdd1': No such file or directory
FAILED
Failed to startup volume: No such file or directory
Failed to access '/dev/sdd1': No such file or directory
Error opening '/dev/sdd1': No such file or directory
Volume is corrupt. You should run chkdsk.


That's an advice... Also windows still works.

Tomorrow I will try CHKDSK again now with /f. It' really bad when you can't access to important data, and you wouldn't like to delete them...
I would like to use linux on PC, but errors everywhere. APT-GET, nVidia driver, and now GRUB and NTFS corruption...

---

### Post by quailstorm on 2013-02-05
Using Windows XP's CHKDSK with /r option didn't help...

---

### Post by quailstorm on 2013-02-05
Bad news. I installed partition wizard from the HDD with the damaged partition table, and it looks like it's really damaged...
What now? After two rounds of CHKDSK. Still, windows boots from the HDD...

[http://img687.imageshack.us/img687/9431/partitiony.jpg]("http://img687.imageshack.us/img687/9431/partitiony.jpg")

Now what?

---

### Post by quailstorm on 2013-02-05
Issue is [solved]("http://www.sevenforums.com/general-discussion/277221-corrupt-but-working-ntfs-partitions-ubuntu-doesnt-show-them-all.html#post2282053") by gregrocker on [sevenforums.com]("http://www.sevenforums.com/")

Partition Wizard Partition Recovery [did the work]("http://img688.imageshack.us/img688/8041/recovering2u.jpg") on Vista64.

---

### Post by oldfred on 2013-02-05
It is good to know that partition wizard works. 

I am still curious to what the real issue was, since some things said it was ok and others said it had issues. Gparted said it was Disk Label?

---

### Post by quailstorm on 2013-02-06
You can see in the thread staring post that it said: > Unrecognised disk label.

There were some fake EXT3 partitions on the disk, and also some remained NTLDR and BOOTMGR boot partitions. So somehow, the kernel couldn't decide where does a partition start, because in one real partitons physical space, there could be 6-8 fake partitons too.
I never used EXT3 on the disk... But after analysing with partition magic, I got around 15 20MB large ones near each other... plus some 8MB large BOOT partitions that were correct in the past, but I've deleted or moved them.
That's why I don't use windows tools for partitioning since I burned a GParted live CD.
So partition magic deleted the fake partition entries, and fixed the three NTFS volume's data.

---

