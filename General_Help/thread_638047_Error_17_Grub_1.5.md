---
title: "Error 17 Grub 1.5"
date: 2007-12-11
forum: General Help
---

### Post by kotak07 on 2007-12-11
Yeah when i restarted my computer after a update my ubuntu wont start up. It says Grub error 17. But now my Live CD wont boot. Well i looked at the other threads and they boot up so i decided to use a live CD. i have 7.04 installed but i have the 7.10 cd..i used that..no luck i got something close to this error. 
```
 Buffer I/O error on device sda2, logical block 0
 Buffer I/O error on device sda2, logical block 1
 Buffer I/O error on device sda2, logical block 2
 Buffer I/O error on device sda2, logical block 3
 Buffer I/O error on device sda2, logical block 4
 Buffer I/O error on device sda2, logical block 5
 Buffer I/O error on device sda2, logical block 6
 Buffer I/O error on device sda2, logical block 7
``` 
this is when i use the start or install option. So then i decided to use the 7.04 live Cd but that didnt work either. The same thing ends up happening. I dont know what to do anymore. i have so much stuff saved up on there and i want to back up all my files before. If i could just get it to start and get into terminal or start terminal from the Live CD's  then i might be able to fix grub.
Thanks. Kotak

---

### Post by pieisgood4589 on 2007-12-11
OK, here's what you got to do. Before booting up the LiveCD, use the Zenwalk installation CD and do the auto-partition, and stop the install right after the partition is done. Then, the partition table will be OK for Ubuntu to bootup with. Boot it up using the 7.04 install CD, NOT the 7.10 and install.

---

### Post by kotak07 on 2007-12-11
i got the live CD but i looked up autopartiton on google for zenwalk and i had a question..will it erase everything? is there an easier way? without having to auto partiton. what if it does erase everything?

---

### Post by kotak07 on 2007-12-11
ok so it wasnt the live cd. i used the regular CD and i did auto partition but it says that it would erase everything. so i decided not to do it. I want to make it clear that i dont want any of my stuff erased. i just want grub back. for some reason the ubuntu live cd isnt working.

---

### Post by kotak07 on 2007-12-11
anyone? please i need help fast. all my schoolwork and such is on there. thanks agaiin

* i also used super grub bootloader to no effect. just led me to another error..error 15. Anyone can help me off that or just give me a solution. as far as i know the ubuntu live cd still doesnt boot up. but the zenwalk one does.

---

### Post by kotak07 on 2007-12-12
bump. anyone have any solutions?

---

### Post by kotak07 on 2007-12-12
no one has any solutions to my problem? or am i being ignored.

---

### Post by psusi on 2007-12-12
I am confused.  When yous say "boot the livecd" do you mean choose the option to boot from the first hard disk, or just run Ubuntu from the livecd?  The error your pasted looks like something is trying to read your hard disk and failing.  How did you come by those messages?  You should be able to boot up the livecd and get to a working desktop no matter what state your hard disk is in.

---

### Post by kotak07 on 2007-12-12
when i mean boot the live cd i mean like just run ubuntu from the live CD. I come by those error messages when i click the option "Start or Install Ubuntu" it gives me that error. thats the problem i dont know why its not booting up the live CD. like i said before it boots up like Gparted live cd and then zenwalk live CD but not the ubuntu Live CD.

---

### Post by kotak07 on 2007-12-12
woooooo! i got the live CD working. now i need help. how do i fix error 17? can i get help in that?

---

### Post by kotak07 on 2007-12-12
ok so i tried this [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

but for some reason it doesnt work. like i get stuck at ```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/ubuntu 
``` that step. i dont know whats wrong. this is what comes up. 
```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/ubuntu 
mount: special device /dev/sda2 does not exist

```
*sda2 is where my linux is located.

and without that i cant get the 2 files i need ```
# /boot/grub/menu.lst
# /etc/fstab
# /etc/X11/xorg.conf
```

but here is my sudo fdisk -lu
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2         1172745    78140159    38483707+  83  Linux
/dev/sda3              63     1172744      586341   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by kotak07 on 2007-12-12
anyone? i posted everything i can so far and described my problem now all i need to do is fix error 17. i checked all the threads but nothing seems to be helping me. Please i need help. Thanks in advance again

---

### Post by confused57 on 2007-12-12
> **kotak07 said:**
> anyone? i posted everything i can so far and described my problem now all i need to do is fix error 17. i checked all the threads but nothing seems to be helping me. Please i need help. Thanks in advance again
You might try running a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
The Gparted live cd would be the easiest way, but I think you could use the Ubuntu live cd.

If you have access to another computer, you might try burning a Knoppix live cd...with Knoppix, you can right-click the partition to mount it.

Added:  If you're getting a grub boot menu, you could try highlighting your Ubuntu entry, press "e", then highlight the line with root,press "e" again, change root from (hd0,0) to (hd0,1)...or if it is already (hd0,1), change it to (hd0,0), press "enter", then "b" to boot...may not work, but should be worth trying.

---

### Post by torgrot on 2007-12-12
Something looks funny about your partitions.  Did you delete sda1 partition?  Take a look at this page, it has some trouble shooting steps for error 17  [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)  My guess would be that grub has the wrong geometry or the geometry has changed.  With that partition table grub should be looking at hd0,1 for root.  I don't think I have every seen a drive that starts it's partition table with the second partition.  The only way I can think to get that would be with and extended partition without a primary partition.  I am no expert on grub, but the link has some ideas for fixing what ails you.

torgrot

---

### Post by psusi on 2007-12-13
Check the output of dmesg for errors and check that the drive isn't failing:

sudo apt-get install smartmontools
sudo smartctl -A /dev/sda

---

### Post by kotak07 on 2007-12-13
for confused57 for the right click to mount the partition how do i do that? yeah idk but it seems that my partition isnt mounted. but when i start Gpaarted from knoppix it says /dev/hda2 with an exclamation mark and it says unknown filesystem. and when i try and mount it from terminal root it says mount : special device /dev/hda2 does not exist..i used hda2 because thats what it says in Gparted. i also tried sda2 but same thing came up.

---

### Post by kotak07 on 2007-12-13
i ran those commands in gparted but it says no such file or directory while trying to open /dev/hda2

---

### Post by kotak07 on 2007-12-13
This problem happened like it was updating some software and it froze so i hard shutdown'd it. and then rebooted it back up and i got that problem. 
```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   058   056   034    Pre-fail  Always       -       179091207
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       1017
  5 Reallocated_Sector_Ct   0x0033   093   093   036    Pre-fail  Always       -       300
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       184292027
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       9260
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1015
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1018
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       235770
194 Temperature_Celsius     0x0022   044   066   000    Old_age   Always       -       44 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   058   056   000    Old_age   Always       -       179091207
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       24
198 Offline_Uncorrectable   0x0010   099   099   000    Old_age   Offline      -       24
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

```

thats what i got. i dont think my drive is failing. everytime i try and put in a command or something to fix it like e2fsck it says /dev/hda2 theres no such thing or its not present and in gparted it says unknown file system or it sometimes says '/dev/sda2' not present. Yeah i need help fast. i cant keep using the live CD and i dont want to restore everything because i have important files on this laptop. id be willing to restore all of it if i could back up all my files that i have on there. and maybe this [http://ubuntuforums.org/showthread.php?t=364564](http://ubuntuforums.org/showthread.php?t=364564) thread might help me. if i need similar directions?

---

### Post by torgrot on 2007-12-13
There is still something wrong with your partition table.  There is a whopping chunk of disk space missing at the beginning of the disk.  Where is sda1?  Is sda2 and extended partition?  If it is, you can't boot from it.  sda3 your swap partition appears to be at the front of the disk.  There is something truly whacked with the way that disk is layed out.  I don't know if you can back it up that way.

torgrot

---

### Post by kotak07 on 2007-12-13
yeah when i set it up in the beginning when i got ubuntu like 3-4 months ago thats how i set it up. i wanted to dual boot it with xp but then i changed my mind so i just used gparted and put the partition i had made and increased it into ubuntu. it didnt seem to be a problem. sda2 is not an extended partiton. its where my ubuntu system is. sda3 is the swap memory and sda3 is in the front of my disk. its the only place where i could put it to make ubuntu work

---

### Post by kotak07 on 2007-12-13
i tried some other stuff but nothing helps me. i cant mount the partition in the first place. i dont think theres anything wrong with it since it worked before. I think the thread that i posted 2 posts above might help me but then again i dont know what to do. maybe if i can get it to mount then it would work. everytime i try and mount it says theres no such thing as sda2 even tho as u can see fdisk -l begs to differ.

---

### Post by torgrot on 2007-12-13
From the link I gave earlier about error 17.
Something else that can definitely cause the mix up is when someone changes their hard disk Boot Priority in their BIOS. Make sure your hard disks are properly detected in your BIOS and set to AUTO, (not LBA, large or normal). 

If you have used hard disk partitioning software recently and you have copied and pasted your partition that contains GRUB, it probably has a different partition number now than it had before. You can use Super GRUB Disk to re-install GRUB. You will also need to edit /etc/fstab if your partition numbers have changed.
If you tried the solutions above and it does nothing helped, try this solution posted in to Ubuntu Web Forums by AmericanYellow, here is the link, Grub error 17
(Make sure your hard disks are properly detected in your BIOS and set to AUTO, (not LBA, large or normal). Thanks AmericanYellow for that information.

redenex, also in the same thread, solved his GRUB error 17 problem with a file system check.

The link he refers to is here [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

I wish you the best of luck.

torgrot

---

### Post by kotak07 on 2007-12-13
That was one of the first threads i looked at. My Bios isnt a problem and i dont have the option of changing my hard disks to auto, lba, large or normal. I havent used a partitioning software recently. this happened in the middle of a software being updated. the computer froze and hard rebooted it and thats when i got error 17. 

i have to make this clear. **When ever i try and mount sda2...my supposdly ubuntu OS. It Doesnt work.** 
[B]This is what i get.
```

root@ubuntu:~# mount /dev/sda2 /ubuntu
mount: special device /dev/sda2 does not exist

```[/B]

Thats what always happens. i can never mount the system. In Gparted it lists it as unknown. If i could** figure out a way to mount it** then maybe i can go on from there.

---

### Post by jdackle on 2007-12-13
I'm sorry to tell you this, kotak07, but it seems possible to me that the hard reboot you made (if I understood correctly, you pressed the reboot buttonh on you computer...?), that may have caused physical damage to your disk... :(
I know it's unlikely and ext3's journaling system makes these events inocuous in most cases (hey, I had two power failures with the computer on just yesterday, checked the drive for errors afterwards and it came as clean as could be! :) ). Guess you were just unlucky... If indeed that is what happened.

Before going into panic-mode, two notes:

1. The disk may not have been physically damaged but just have had some (soft) data corruption to a critical area - how to solve this or even just test for it I have no idea. But it's a thought... I guess.

2. Even if the disk was physically damaged, it may be that some parts weren't - hopefully, the parts where the data you want to retrieve is placed might still be intact.
In this case, you might want to try and save that data to some other medium. There are tools for both Linux and Windows (do you still have Windows installed and working?) to make raw copies of hard-disk data to some other medium. I never used one such program but you can look around.

I know it's not what you wanted but, hey, sh*t does happen! :(

You might want to go and find some profissional hardware help with your PC and see what they can do...

Best luck!

---

### Post by confused57 on 2007-12-13
> **kotak07 said:**
> for confused57 for the right click to mount the partition how do i do that? yeah idk but it seems that my partition isnt mounted. but when i start Gpaarted from knoppix it says /dev/hda2 with an exclamation mark and it says unknown filesystem. and when i try and mount it from terminal root it says mount : special device /dev/hda2 does not exist..i used hda2 because thats what it says in Gparted. i also tried sda2 but same thing came up.
After you booted up the Knoppix live cd, was there an icon on your desktop for your Ubuntu partition?  If there was, you would just right-click the icon then select "Mount".

I'm typing this using Iceweasel browser on the Knoppix live cd...all of the partitions on my 3 hard drives have an icon on the desktop that I can right-click and select to "Mount".

Maybe your IDE cable to your hard drive has gone bad?  I really don't know why your root partition isn't being recognized.  Since nothing else is working, you could possibly try using Gnome Partition Editor on the Ubuntu live cd  and resize your root partition(maybe make it 1-2 Gb smaller than it is)...you may not be able to, but it may be worth trying.

---

### Post by kotak07 on 2007-12-13
wow this sucks balls. 

to jdackle. i dont have windows installed. i never did. i was considering to have it dual booted but went against it. 
And to confused 57 knoppix didnt recognize my partition. there was no icon. of all the things to happen...im still open to suggestion. i doubt my hard drive is failing. or corrupted or something. this laptop is only a couple years old. i wouldnt mind more ideas pouring in...right now ill do just about anything. if anyone also has a name of any programs like what jdackle was talkin about. something to still recover data from a corrupted partiton. id like to know. or even better if i still have a chance of recovering the system.

---

### Post by confused57 on 2007-12-13
I've never used Test Disk, but it may be worth looking into:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by torgrot on 2007-12-13
Another option to try and save some of the data would be Acronis True Image Home.  It has a bootable CD and can backup ext3 partitions.  You may be able to use that to get the data off and if it has a recognizable file system on it you could restore the files one at a time.  Bad part is that it isn't free.  Generally available for about $50US.

torgrot

---

### Post by psusi on 2007-12-14
Check dmesg for errors about why there is no sda2 when there should be.  And I am also wondering why the heck there is no sda1.

---

### Post by kotak07 on 2007-12-14
```
[52348.108000] ata1: soft resetting port
[52348.420000] ata1.01: revalidation failed (errno=-2)
[52348.420000] ata1: failed to recover some devices, retrying in 5 secs
[52353.424000] ata1: soft resetting port
[52353.768000] ata1.00: configured for UDMA/100
[52353.940000] ata1.01: configured for MWDMA2
[52353.940000] ata1: EH complete
[52383.940000] ata1.00: limiting speed to UDMA/66:PIO4
[52383.940000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52383.940000] ata1.00: cmd 35/00:00:17:7e:00/00:04:00:00:00/e0 tag 0 cdb 0x28 data 524288 out
[52383.940000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52388.980000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52393.964000] ata1: device not ready (errno=-16), forcing hardreset
[52393.964000] ata1: soft resetting port
[52394.308000] ata1.00: configured for UDMA/66
[52394.480000] ata1.01: configured for MWDMA2
[52394.480000] ata1: EH complete
[52424.480000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52424.480000] ata1.00: cmd 35/00:00:17:7e:00/00:04:00:00:00/e0 tag 0 cdb 0x28 data 524288 out
[52424.480000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52429.520000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52434.504000] ata1: device not ready (errno=-16), forcing hardreset
[52434.504000] ata1: soft resetting port
[52434.824000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52434.824000] ata1.01: revalidation failed (errno=-19)
[52434.824000] ata1.01: limiting speed to MWDMA2:PIO2
[52434.824000] ata1: failed to recover some devices, retrying in 5 secs
[52439.828000] ata1: soft resetting port
[52440.172000] ata1.00: configured for UDMA/66
[52440.344000] ata1.01: configured for MWDMA2
[52440.344000] ata1: EH complete
[52470.344000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52470.344000] ata1.00: cmd 35/00:00:17:7e:00/00:04:00:00:00/e0 tag 0 cdb 0x28 data 524288 out
[52470.344000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52475.384000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52480.368000] ata1: device not ready (errno=-16), forcing hardreset
[52480.368000] ata1: soft resetting port
[52480.712000] ata1.00: configured for UDMA/66
[52480.884000] ata1.01: configured for MWDMA2
[52480.884000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[52480.884000] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[52480.884000] Descriptor sense data with sense descriptors (in hex):
[52480.884000]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[52480.884000]         00 11 e5 0a 
[52480.884000] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[52480.884000] end_request: I/O error, dev sda, sector 32279
[52480.884000] Write-error on swap-device (8:0:32287)
[52480.884000] Write-error on swap-device (8:0:32295)
[52480.884000] Write-error on swap-device (8:0:32303)
[52480.884000] Write-error on swap-device (8:0:32311)
[52480.884000] Write-error on swap-device (8:0:32319)
[52480.884000] Write-error on swap-device (8:0:32327)
[52480.884000] Write-error on swap-device (8:0:32335)
[52480.884000] Write-error on swap-device (8:0:32343)
[52480.884000] Write-error on swap-device (8:0:32351)
[52480.884000] Write-error on swap-device (8:0:32359)
[52480.884000] Write-error on swap-device (8:0:32367)
[52480.884000] Write-error on swap-device (8:0:32375)
[52480.884000] Write-error on swap-device (8:0:32383)
[52480.884000] Write-error on swap-device (8:0:32391)
[52480.884000] Write-error on swap-device (8:0:32399)
[52480.884000] Write-error on swap-device (8:0:32407)
[52480.884000] Write-error on swap-device (8:0:32415)
[52480.884000] Write-error on swap-device (8:0:32423)
[52480.884000] Write-error on swap-device (8:0:32431)
[52480.884000] Write-error on swap-device (8:0:32439)
[52480.884000] Write-error on swap-device (8:0:32447)
[52480.884000] Write-error on swap-device (8:0:32455)
[52480.884000] Write-error on swap-device (8:0:32463)
[52480.884000] Write-error on swap-device (8:0:32471)
[52480.884000] Write-error on swap-device (8:0:32479)
[52480.884000] Write-error on swap-device (8:0:32487)
[52480.884000] Write-error on swap-device (8:0:32495)
[52480.884000] Write-error on swap-device (8:0:32503)
[52480.884000] Write-error on swap-device (8:0:32511)
[52480.884000] Write-error on swap-device (8:0:32519)
[52480.884000] Write-error on swap-device (8:0:32527)
[52480.884000] Write-error on swap-device (8:0:32535)
[52480.884000] Write-error on swap-device (8:0:32543)
[52480.884000] Write-error on swap-device (8:0:32551)
[52480.884000] Write-error on swap-device (8:0:32559)
[52480.884000] Write-error on swap-device (8:0:32567)
[52480.884000] Write-error on swap-device (8:0:32575)
[52480.884000] Write-error on swap-device (8:0:32583)
[52480.884000] Write-error on swap-device (8:0:32591)
[52480.884000] Write-error on swap-device (8:0:32599)
[52480.884000] Write-error on swap-device (8:0:32607)
[52480.884000] Write-error on swap-device (8:0:32615)
[52480.884000] Write-error on swap-device (8:0:32623)
[52480.884000] Write-error on swap-device (8:0:32631)
[52480.884000] Write-error on swap-device (8:0:32639)
[52480.884000] Write-error on swap-device (8:0:32647)
[52480.884000] Write-error on swap-device (8:0:32655)
[52480.884000] Write-error on swap-device (8:0:32663)
[52480.884000] Write-error on swap-device (8:0:32671)
[52480.884000] Write-error on swap-device (8:0:32679)
[52480.884000] Write-error on swap-device (8:0:32687)
[52480.884000] Write-error on swap-device (8:0:32695)
[52480.884000] Write-error on swap-device (8:0:32703)
[52480.884000] Write-error on swap-device (8:0:32711)
[52480.884000] Write-error on swap-device (8:0:32719)
[52480.884000] Write-error on swap-device (8:0:32727)
[52480.884000] Write-error on swap-device (8:0:32735)
[52480.884000] Write-error on swap-device (8:0:32743)
[52480.884000] Write-error on swap-device (8:0:32751)
[52480.884000] Write-error on swap-device (8:0:32759)
[52480.884000] Write-error on swap-device (8:0:32767)
[52480.884000] Write-error on swap-device (8:0:32775)
[52480.884000] Write-error on swap-device (8:0:32783)
[52480.884000] Write-error on swap-device (8:0:32791)
[52480.884000] Write-error on swap-device (8:0:32799)
[52480.884000] Write-error on swap-device (8:0:32807)
[52480.884000] Write-error on swap-device (8:0:32815)
[52480.884000] Write-error on swap-device (8:0:32823)
[52480.884000] Write-error on swap-device (8:0:32831)
[52480.884000] Write-error on swap-device (8:0:32839)
[52480.884000] Write-error on swap-device (8:0:32847)
[52480.884000] Write-error on swap-device (8:0:32855)
[52480.884000] Write-error on swap-device (8:0:32863)
[52480.884000] Write-error on swap-device (8:0:32871)
[52480.884000] Write-error on swap-device (8:0:32879)
[52480.884000] Write-error on swap-device (8:0:32887)
[52480.884000] Write-error on swap-device (8:0:32895)
[52480.884000] Write-error on swap-device (8:0:32903)
[52480.884000] Write-error on swap-device (8:0:32911)
[52480.884000] Write-error on swap-device (8:0:32919)
[52480.884000] Write-error on swap-device (8:0:32927)
[52480.884000] Write-error on swap-device (8:0:32935)
[52480.884000] Write-error on swap-device (8:0:32943)
[52480.884000] Write-error on swap-device (8:0:32951)
[52480.884000] Write-error on swap-device (8:0:32959)
[52480.884000] Write-error on swap-device (8:0:32967)
[52480.884000] Write-error on swap-device (8:0:32975)
[52480.884000] Write-error on swap-device (8:0:32983)
[52480.884000] Write-error on swap-device (8:0:32991)
[52480.884000] Write-error on swap-device (8:0:32999)
[52480.884000] Write-error on swap-device (8:0:33007)
[52480.884000] Write-error on swap-device (8:0:33015)
[52480.884000] Write-error on swap-device (8:0:33023)
[52480.884000] Write-error on swap-device (8:0:33031)
[52480.884000] Write-error on swap-device (8:0:33039)
[52480.884000] Write-error on swap-device (8:0:33047)
[52480.884000] Write-error on swap-device (8:0:33055)
[52480.884000] Write-error on swap-device (8:0:33063)
[52480.884000] Write-error on swap-device (8:0:33071)
[52480.884000] Write-error on swap-device (8:0:33079)
[52480.884000] Write-error on swap-device (8:0:33087)
[52480.884000] Write-error on swap-device (8:0:33095)
[52480.884000] Write-error on swap-device (8:0:33103)
[52480.884000] Write-error on swap-device (8:0:33111)
[52480.884000] Write-error on swap-device (8:0:33119)
[52480.884000] Write-error on swap-device (8:0:33127)
[52480.884000] Write-error on swap-device (8:0:33135)
[52480.884000] Write-error on swap-device (8:0:33143)
[52480.884000] Write-error on swap-device (8:0:33151)
[52480.884000] Write-error on swap-device (8:0:33159)
[52480.884000] Write-error on swap-device (8:0:33167)
[52480.884000] Write-error on swap-device (8:0:33175)
[52480.884000] Write-error on swap-device (8:0:33183)
[52480.884000] Write-error on swap-device (8:0:33191)
[52480.884000] Write-error on swap-device (8:0:33199)
[52480.884000] Write-error on swap-device (8:0:33207)
[52480.884000] Write-error on swap-device (8:0:33215)
[52480.884000] Write-error on swap-device (8:0:33223)
[52480.884000] Write-error on swap-device (8:0:33231)
[52480.884000] Write-error on swap-device (8:0:33239)
[52480.884000] Write-error on swap-device (8:0:33247)
[52480.884000] Write-error on swap-device (8:0:33255)
[52480.884000] Write-error on swap-device (8:0:33263)
[52480.884000] Write-error on swap-device (8:0:33271)
[52480.884000] Write-error on swap-device (8:0:33279)
[52480.884000] Write-error on swap-device (8:0:33287)
[52480.884000] Write-error on swap-device (8:0:33295)
[52480.884000] Write-error on swap-device (8:0:33303)
[52480.884000] ata1: EH complete
[52480.888000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52480.888000] sd 0:0:0:0: [sda] Write Protect is off
[52480.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52480.888000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52480.888000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52480.888000] sd 0:0:0:0: [sda] Write Protect is off
[52480.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52483.356000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52513.356000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52513.356000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52513.356000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52518.396000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52523.380000] ata1: device not ready (errno=-16), forcing hardreset
[52523.380000] ata1: soft resetting port
[52523.724000] ata1.00: configured for UDMA/66
[52523.896000] ata1.01: configured for MWDMA2
[52523.896000] ata1: EH complete
[52553.896000] ata1.00: limiting speed to UDMA/33:PIO4
[52553.896000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52553.896000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52553.896000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52558.936000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52563.920000] ata1: device not ready (errno=-16), forcing hardreset
[52563.920000] ata1: soft resetting port
[52564.240000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52564.240000] ata1.01: revalidation failed (errno=-19)
[52564.240000] ata1.01: limiting speed to MWDMA2:PIO1
[52564.240000] ata1: failed to recover some devices, retrying in 5 secs
[52569.244000] ata1: soft resetting port
[52569.588000] ata1.00: configured for UDMA/33
[52569.760000] ata1.01: configured for MWDMA2
[52569.760000] ata1: EH complete
[52599.760000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52599.760000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52599.760000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52604.800000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52609.784000] ata1: device not ready (errno=-16), forcing hardreset
[52609.784000] ata1: soft resetting port
[52610.104000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52610.104000] ata1.01: revalidation failed (errno=-19)
[52610.104000] ata1.01: limiting speed to MWDMA2:PIO0
[52610.104000] ata1: failed to recover some devices, retrying in 5 secs
[52615.108000] ata1: soft resetting port
[52615.452000] ata1.00: configured for UDMA/33
[52615.624000] ata1.01: configured for MWDMA2
[52615.624000] ata1: EH complete
[52645.624000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52645.624000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52645.624000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52650.664000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52655.648000] ata1: device not ready (errno=-16), forcing hardreset
[52655.648000] ata1: soft resetting port
[52655.968000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52655.968000] ata1.01: revalidation failed (errno=-19)
[52655.968000] ata1: failed to recover some devices, retrying in 5 secs
[52660.972000] ata1: soft resetting port
[52661.316000] ata1.00: configured for UDMA/33
[52661.488000] ata1.01: configured for MWDMA2
[52661.488000] ata1: EH complete
[52691.488000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52691.488000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52691.488000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52696.528000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52701.512000] ata1: device not ready (errno=-16), forcing hardreset
[52701.512000] ata1: soft resetting port
[52701.832000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52701.832000] ata1.01: revalidation failed (errno=-19)
[52701.832000] ata1: failed to recover some devices, retrying in 5 secs
[52706.836000] ata1: soft resetting port
[52707.180000] ata1.00: configured for UDMA/33
[52707.352000] ata1.01: configured for MWDMA2
[52707.352000] ata1: EH complete
[52737.352000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52737.352000] ata1.00: cmd 35/00:00:17:82:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52737.352000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52742.392000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52747.376000] ata1: device not ready (errno=-16), forcing hardreset
[52747.376000] ata1: soft resetting port
[52747.696000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52747.696000] ata1.01: revalidation failed (errno=-19)
[52747.696000] ata1: failed to recover some devices, retrying in 5 secs
[52752.700000] ata1: soft resetting port
[52753.044000] ata1.00: configured for UDMA/33
[52753.216000] ata1.01: configured for MWDMA2
[52753.216000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[52753.216000] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[52753.216000] Descriptor sense data with sense descriptors (in hex):
[52753.216000]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[52753.216000]         00 11 e5 0a 
[52753.216000] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[52753.216000] end_request: I/O error, dev sda, sector 33303
[52753.216000] Write-error on swap-device (8:0:33311)
[52753.216000] Write-error on swap-device (8:0:33319)
[52753.216000] Write-error on swap-device (8:0:33327)
[52753.216000] Write-error on swap-device (8:0:33335)
[52753.216000] Write-error on swap-device (8:0:33343)
[52753.216000] Write-error on swap-device (8:0:33351)
[52753.216000] Write-error on swap-device (8:0:33359)
[52753.216000] Write-error on swap-device (8:0:33367)
[52753.216000] Write-error on swap-device (8:0:33375)
[52753.216000] Write-error on swap-device (8:0:33383)
[52753.216000] Write-error on swap-device (8:0:33391)
[52753.216000] Write-error on swap-device (8:0:33399)
[52753.216000] Write-error on swap-device (8:0:33407)
[52753.216000] Write-error on swap-device (8:0:33415)
[52753.216000] Write-error on swap-device (8:0:33423)
[52753.216000] Write-error on swap-device (8:0:33431)
[52753.216000] Write-error on swap-device (8:0:33439)
[52753.216000] Write-error on swap-device (8:0:33447)
[52753.216000] Write-error on swap-device (8:0:33455)
[52753.216000] Write-error on swap-device (8:0:33463)
[52753.216000] Write-error on swap-device (8:0:33471)
[52753.216000] Write-error on swap-device (8:0:33479)
[52753.216000] Write-error on swap-device (8:0:33487)
[52753.216000] Write-error on swap-device (8:0:33495)
[52753.216000] Write-error on swap-device (8:0:33503)
[52753.216000] Write-error on swap-device (8:0:33511)
[52753.216000] Write-error on swap-device (8:0:33519)
[52753.216000] Write-error on swap-device (8:0:33527)
[52753.216000] Write-error on swap-device (8:0:33535)
[52753.216000] Write-error on swap-device (8:0:33543)
[52753.216000] Write-error on swap-device (8:0:33551)
[52753.216000] Write-error on swap-device (8:0:33559)
[52753.216000] Write-error on swap-device (8:0:33567)
[52753.216000] Write-error on swap-device (8:0:33575)
[52753.216000] Write-error on swap-device (8:0:33583)
[52753.216000] Write-error on swap-device (8:0:33591)
[52753.216000] Write-error on swap-device (8:0:33599)
[52753.216000] Write-error on swap-device (8:0:33607)
[52753.216000] Write-error on swap-device (8:0:33615)
[52753.216000] Write-error on swap-device (8:0:33623)
[52753.216000] Write-error on swap-device (8:0:33631)
[52753.216000] Write-error on swap-device (8:0:33639)
[52753.216000] Write-error on swap-device (8:0:33647)
[52753.216000] Write-error on swap-device (8:0:33655)
[52753.216000] Write-error on swap-device (8:0:33663)
[52753.216000] Write-error on swap-device (8:0:33671)
[52753.216000] Write-error on swap-device (8:0:33679)
[52753.216000] Write-error on swap-device (8:0:33687)
[52753.216000] Write-error on swap-device (8:0:33695)
[52753.216000] Write-error on swap-device (8:0:33703)
[52753.216000] Write-error on swap-device (8:0:33711)
[52753.216000] Write-error on swap-device (8:0:33719)
[52753.216000] Write-error on swap-device (8:0:33727)
[52753.216000] Write-error on swap-device (8:0:33735)
[52753.216000] Write-error on swap-device (8:0:33743)
[52753.216000] Write-error on swap-device (8:0:33751)
[52753.216000] Write-error on swap-device (8:0:33759)
[52753.216000] Write-error on swap-device (8:0:33767)
[52753.216000] Write-error on swap-device (8:0:33775)
[52753.216000] Write-error on swap-device (8:0:33783)
[52753.216000] Write-error on swap-device (8:0:33791)
[52753.216000] Write-error on swap-device (8:0:33799)
[52753.216000] Write-error on swap-device (8:0:33807)
[52753.216000] Write-error on swap-device (8:0:33815)
[52753.216000] Write-error on swap-device (8:0:33823)
[52753.216000] Write-error on swap-device (8:0:33831)
[52753.216000] Write-error on swap-device (8:0:33839)
[52753.216000] Write-error on swap-device (8:0:33847)
[52753.216000] Write-error on swap-device (8:0:33855)
[52753.216000] Write-error on swap-device (8:0:33863)
[52753.216000] Write-error on swap-device (8:0:33871)
[52753.216000] Write-error on swap-device (8:0:33879)
[52753.216000] Write-error on swap-device (8:0:33887)
[52753.216000] Write-error on swap-device (8:0:33895)
[52753.216000] Write-error on swap-device (8:0:33903)
[52753.216000] Write-error on swap-device (8:0:33911)
[52753.216000] Write-error on swap-device (8:0:33919)
[52753.216000] Write-error on swap-device (8:0:33927)
[52753.216000] Write-error on swap-device (8:0:33935)
[52753.216000] Write-error on swap-device (8:0:33943)
[52753.216000] Write-error on swap-device (8:0:33951)
[52753.216000] Write-error on swap-device (8:0:33959)
[52753.216000] Write-error on swap-device (8:0:33967)
[52753.216000] Write-error on swap-device (8:0:33975)
[52753.216000] Write-error on swap-device (8:0:33983)
[52753.216000] Write-error on swap-device (8:0:33991)
[52753.216000] Write-error on swap-device (8:0:33999)
[52753.216000] Write-error on swap-device (8:0:34007)
[52753.216000] Write-error on swap-device (8:0:34015)
[52753.216000] Write-error on swap-device (8:0:34023)
[52753.216000] Write-error on swap-device (8:0:34031)
[52753.216000] Write-error on swap-device (8:0:34039)
[52753.216000] Write-error on swap-device (8:0:34047)
[52753.216000] Write-error on swap-device (8:0:34055)
[52753.216000] Write-error on swap-device (8:0:34063)
[52753.216000] Write-error on swap-device (8:0:34071)
[52753.216000] Write-error on swap-device (8:0:34079)
[52753.216000] Write-error on swap-device (8:0:34087)
[52753.216000] Write-error on swap-device (8:0:34095)
[52753.216000] Write-error on swap-device (8:0:34103)
[52753.216000] Write-error on swap-device (8:0:34111)
[52753.216000] Write-error on swap-device (8:0:34119)
[52753.216000] Write-error on swap-device (8:0:34127)
[52753.216000] Write-error on swap-device (8:0:34135)
[52753.216000] Write-error on swap-device (8:0:34143)
[52753.216000] Write-error on swap-device (8:0:34151)
[52753.216000] Write-error on swap-device (8:0:34159)
[52753.216000] Write-error on swap-device (8:0:34167)
[52753.216000] Write-error on swap-device (8:0:34175)
[52753.216000] Write-error on swap-device (8:0:34183)
[52753.216000] Write-error on swap-device (8:0:34191)
[52753.216000] Write-error on swap-device (8:0:34199)
[52753.216000] Write-error on swap-device (8:0:34207)
[52753.216000] Write-error on swap-device (8:0:34215)
[52753.216000] Write-error on swap-device (8:0:34223)
[52753.216000] Write-error on swap-device (8:0:34231)
[52753.216000] Write-error on swap-device (8:0:34239)
[52753.216000] Write-error on swap-device (8:0:34247)
[52753.216000] Write-error on swap-device (8:0:34255)
[52753.216000] Write-error on swap-device (8:0:34263)
[52753.216000] Write-error on swap-device (8:0:34271)
[52753.216000] Write-error on swap-device (8:0:34279)
[52753.216000] Write-error on swap-device (8:0:34287)
[52753.216000] Write-error on swap-device (8:0:34295)
[52753.216000] Write-error on swap-device (8:0:34303)
[52753.216000] Write-error on swap-device (8:0:34311)
[52753.216000] Write-error on swap-device (8:0:34319)
[52753.216000] Write-error on swap-device (8:0:34327)
[52753.216000] ata1: EH complete
[52753.216000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52753.220000] sd 0:0:0:0: [sda] Write Protect is off
[52753.220000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52753.220000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52753.220000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52753.220000] sd 0:0:0:0: [sda] Write Protect is off
[52753.220000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52755.600000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52785.892000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52785.892000] ata1.00: cmd 35/00:00:17:86:00/00:04:00:00:00/e0 tag 0 cdb 0x28 data 524288 out
[52785.892000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52790.932000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52795.916000] ata1: device not ready (errno=-16), forcing hardreset
[52795.916000] ata1: soft resetting port
[52796.236000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[52796.236000] ata1.01: revalidation failed (errno=-19)
[52796.236000] ata1: failed to recover some devices, retrying in 5 secs
[52801.240000] ata1: soft resetting port
[52801.584000] ata1.00: configured for UDMA/33
[52801.756000] ata1.01: configured for MWDMA2
[52801.756000] ata1: EH complete
[52820.132000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52822.528000] sd 0:0:0:0: [sda] Write Protect is off
[52822.528000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52822.540000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52822.540000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52822.560000] sd 0:0:0:0: [sda] Write Protect is off
[52822.560000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52822.608000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52858.548000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52858.548000] ata1.00: cmd 35/00:00:c7:ca:00/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[52858.548000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52863.588000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52868.572000] ata1: device not ready (errno=-16), forcing hardreset
[52868.572000] ata1: soft resetting port
[52868.932000] ata1.00: configured for UDMA/33
[52869.104000] ata1.01: configured for MWDMA2
[52869.104000] ata1: EH complete
[52890.528000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52892.860000] sd 0:0:0:0: [sda] Write Protect is off
[52892.860000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52892.864000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52892.868000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52892.884000] sd 0:0:0:0: [sda] Write Protect is off
[52892.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52893.132000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52925.972000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[52925.972000] ata1.00: cmd 35/00:00:17:ee:00/00:04:00:00:00/e0 tag 0 cdb 0x28 data 524288 out
[52925.972000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[52931.012000] ata1: port is slow to respond, please be patient (Status 0xd0)
[52935.996000] ata1: device not ready (errno=-16), forcing hardreset
[52935.996000] ata1: soft resetting port
[52936.340000] ata1.00: configured for UDMA/33
[52936.512000] ata1.01: configured for MWDMA2
[52936.512000] ata1: EH complete
[52961.780000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52964.060000] sd 0:0:0:0: [sda] Write Protect is off
[52964.060000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52964.080000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[52964.084000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[52964.124000] sd 0:0:0:0: [sda] Write Protect is off
[52964.124000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[52964.768000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[53000.168000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53000.168000] ata1.00: cmd 35/00:00:4f:1a:01/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[53000.168000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[53005.208000] ata1: port is slow to respond, please be patient (Status 0xd0)
[53010.192000] ata1: device not ready (errno=-16), forcing hardreset
[53010.192000] ata1: soft resetting port
[53010.512000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[53010.512000] ata1.01: revalidation failed (errno=-19)
[53010.512000] ata1: failed to recover some devices, retrying in 5 secs
[53015.516000] ata1: soft resetting port
[53015.860000] ata1.00: configured for UDMA/33
[53016.032000] ata1.01: configured for MWDMA2
[53016.032000] ata1: EH complete
[53046.032000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53046.032000] ata1.00: cmd 35/00:00:4f:1a:01/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[53046.032000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[53051.072000] ata1: port is slow to respond, please be patient (Status 0xd0)
[53056.056000] ata1: device not ready (errno=-16), forcing hardreset
[53056.056000] ata1: soft resetting port
[53056.376000] ata1.01: model number mismatch 'HL-DT-STCD-RW/DVD DRIVE GCC-4244N' != 'H'
[53056.376000] ata1.01: revalidation failed (errno=-19)
[53056.376000] ata1: failed to recover some devices, retrying in 5 secs
[53061.380000] ata1: soft resetting port
[53061.724000] ata1.00: configured for UDMA/33
[53061.896000] ata1.01: configured for MWDMA2
[53061.896000] ata1: EH complete
[53091.896000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[53091.896000] ata1.00: cmd 35/00:00:4f:1a:01/00:04:00:00:00/e0 tag 0 cdb 0x0 data 524288 out
[53091.896000]          res 40/00:07:0a:e5:11/00:00:00:00:00/e0 Emask 0x4 (timeout)
[53095.648000] ata1: soft resetting port
[53096.048000] ata1.00: configured for UDMA/33
[53096.220000] ata1.01: configured for MWDMA2
[53096.220000] ata1: EH complete
[53120.812000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[53120.812000] sd 0:0:0:0: [sda] Write Protect is off
[53120.812000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[53123.184000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[53123.188000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[53123.188000] sd 0:0:0:0: [sda] Write Protect is off
[53123.188000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[53123.196000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Thats all of dmesg that comes up. i dont know how to interpret that and that dmesg was too long so some of it or alot of it might be cut off. but its usually the same repeating message?

---

### Post by psusi on 2007-12-14
Wow something is royally hosed up there.  It could be you have a bad IDE cable, but let's try asking the drive what's wrong.  

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

---

### Post by kotak07 on 2007-12-14
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 4200.2 Series
Device Model:     ST9402113A
Serial Number:    3LE15JDG
Firmware Version: 3.02
User Capacity:    40,007,761,920 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sat Dec 15 00:14:02 2007 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline 
data collection:                 ( 426) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  55) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   058   056   034    Pre-fail  Always       -       179359907
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       1017
  5 Reallocated_Sector_Ct   0x0033   090   090   036    Pre-fail  Always       -       431
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       184562661
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       9303
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       1015
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1018
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       235799
194 Temperature_Celsius     0x0022   055   066   000    Old_age   Always       -       55 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   058   056   000    Old_age   Always       -       179359907
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       24
198 Offline_Uncorrectable   0x0010   099   099   000    Old_age   Offline      -       24
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 5350 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 5350 occurred at disk power-on lifetime: 9265 hours (386 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 0a e5 11 e0  Error: UNC 7 sectors at LBA = 0x0011e50a = 1172746

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 0a e5 11 e0 00      02:20:49.988  READ DMA
  ec 00 00 00 00 00 a0 02      02:20:49.969  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      02:20:49.964  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      02:20:43.742  IDENTIFY DEVICE
  c8 00 07 0a e5 11 e0 00      02:20:43.551  READ DMA

Error 5349 occurred at disk power-on lifetime: 9265 hours (386 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 0a e5 11 e0  Error: UNC 7 sectors at LBA = 0x0011e50a = 1172746

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 0a e5 11 e0 00      02:20:49.988  READ DMA
  ec 00 00 00 00 00 a0 02      02:20:49.969  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      02:20:49.964  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      02:20:43.742  IDENTIFY DEVICE
  c8 00 07 0a e5 11 e0 00      02:20:43.551  READ DMA

Error 5348 occurred at disk power-on lifetime: 9265 hours (386 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 0a e5 11 e0  Error: UNC 7 sectors at LBA = 0x0011e50a = 1172746

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 0a e5 11 e0 00      02:20:24.426  READ DMA
  ec 00 00 00 00 00 a0 02      02:20:24.246  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      02:20:24.234  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      02:20:43.742  IDENTIFY DEVICE
  c8 00 07 0a e5 11 e0 00      02:20:43.551  READ DMA

Error 5347 occurred at disk power-on lifetime: 9265 hours (386 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 0a e5 11 e0  Error: UNC 7 sectors at LBA = 0x0011e50a = 1172746

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 0a e5 11 e0 00      02:20:24.426  READ DMA
  ec 00 00 00 00 00 a0 02      02:20:24.246  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      02:20:24.234  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      02:20:24.227  IDENTIFY DEVICE
  c8 00 07 0a e5 11 e0 00      02:20:18.003  READ DMA

Error 5346 occurred at disk power-on lifetime: 9265 hours (386 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 0a e5 11 e0  Error: UNC 7 sectors at LBA = 0x0011e50a = 1172746

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 0a e5 11 e0 00      02:20:24.426  READ DMA
  ec 00 00 00 00 00 a0 02      02:20:24.246  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      02:20:24.234  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      02:20:24.227  IDENTIFY DEVICE
  c8 00 07 0a e5 11 e0 00      02:20:18.003  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      9253         1172745
# 2  Short offline       Completed: read failure       90%      9252         1172745
# 3  Short offline       Completed: read failure       90%      9252         1172745

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```
aright.

---

### Post by kotak07 on 2007-12-14
if there is positvly nothing that i can do to fix this someone tell me this very quickly because im keeping a little hope that it isnt. but yeah just smack the truth on me.

---

### Post by kotak07 on 2007-12-14
.............................bumppp

---

### Post by TransitMan on 2007-12-15
It looks like you lost your sda1 partition, hence the problem of Grub error 17.
You need to get another Live CD distro and have a look at the disc and contents to see what is salvagable. After that, it looks like a complete wip and restore.

---

### Post by psusi on 2007-12-15
The drive is physically damaged.  If it is still under warranty, RMA it.  As for your data, it most likely is beyond hope.

---

### Post by jdackle on 2007-12-16
kotak07,

I don't know smartctl myself but it did give you a read error on your disk. :(

Anyways, I did a couple searches in synaptic and founda  couple packages that might be helpful (not really the ones I accidentally found a long time ago but you might want to check these out anyways or look for it your self. I used the following search expressions in "Name AND DESCRIPTION":
corrupt data
corrupt repair
damage filesystem
recover filesystem):

* Package: **gpart** (NOT gpartED!):
Description:
Guess PC disk partition table, find lost partitions
Gpart is a tool which tries to guess the primary partition table of a
PC-type disk in case the primary partition table in sector 0 is
damaged, incorrect or deleted.

It is also good at finding and listing the types, locations, and
sizes of inadvertently-deleted partitions, both primary and logical.
It gives you the information you need to manually re-create them
(using fdisk, cfdisk, sfdisk, etc.).

The guessed table can also be written to a file or (if you firmly
believe the guessed table is entirely correct) directly to a disk
device.

Supported (guessable) filesystem or partition types:

 * BeOS filesystem type.
 * FreeBSD/NetBSD/386BSD disklabel sub-partitioning
   scheme used on Intel platforms.
 * Linux second extended filesystem.
 * MS-DOS FAT12/16/32 "filesystems".
 * IBM OS/2 High Performance filesystem.
 * Linux LVM physical volumes (LVM by Heinz Mauelshagen).
 * Linux swap partitions (versions 0 and 1).
 * The Minix operating system filesystem type.
 * MS Windows NT/2000 filesystem.
 * QNX 4.x filesystem.
 * The Reiser filesystem (version 3.5.X, X > 11).
 * Sun Solaris on Intel platforms uses a sub-partitioning
   scheme on PC hard disks similar to the BSD disklabels.
 * Silicon Graphics' journalling filesystem for Linux.

Other types may be added relatively easily, as separately compiled modules.

* Package: **magicrescue** (do you have access to a /dev/sda2 file? I don't remember now but I guees you'll need to to use this one - not a primary tool for the job but might come in handy):
Description:
recovers files by looking for magic bytes
Magic Rescue scans a block device for file types it knows how to recover
and calls an external program to extract them. It looks at "magic bytes"
in file contents, so it can be used both as an undelete utility and for
recovering a corrupted drive or partition. As long as the file data is
there, it will find it.

 Homepage: [http://jbj.rapanden.dk/magicrescue/](http://jbj.rapanden.dk/magicrescue/)

---

