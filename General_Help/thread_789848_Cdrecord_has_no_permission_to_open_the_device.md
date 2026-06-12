---
title: "Cdrecord has no permission to open the device"
date: 2008-05-10
forum: General Help
---

### Post by DarkDancer on 2008-05-10
Is the error that I get every time I try to burn an audio cd. This is from k3b. Data cd's seem to work just fine. This is with k3b. Brassero says something about not having the correct codecs or something. I thought I had the problem licked, I made a change in System, Administration, Authorizations, Directly access optical drives, changed anyone to yes and it burnt a music cd for me. Now it won't do it again. Gnomebaker tried to burn 7 (of the 19) tracks, but failed at fixating.

Any Clues?

---

### Post by DarkDancer on 2008-05-11
Bump.

---

### Post by DarkDancer on 2008-05-12
bump...

---

### Post by DarkDancer on 2008-05-13
Bump....

---

### Post by DarkDancer on 2008-05-14
Bump...

---

### Post by DarkDancer on 2008-05-14
And in case this might help anyone....

cat /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9843c115-83b8-45a4-9c9e-998d9bfd41a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a962120f-b19b-4e66-b624-717852aa6eda /home           ext3    relatime        0       2
# /dev/sda5
UUID=ebab3cbd-66e4-46d7-9a9d-36493bafd54e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=2a57aceb-dfb9-9520-983a-e26dbbdc4b95 /media/LDSilver  ext3 defaults 0 2
# /dev/sdc1
UUID=c567bf10-ab7e-4680-ec92-fb06ed0d8029 /media/maarla   ext3 defaults 0 2

sudo fdisk -l:

> Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002cf0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2687    21583296    7  HPFS/NTFS
/dev/sda2            2688        5298    20972857+  83  Linux
/dev/sda3            5299       48641   348152647+   5  Extended
/dev/sda5            5299        5560     2104483+  82  Linux swap / Solaris
/dev/sda6            5561        8171    20972825   83  Linux
/dev/sda7            8172       19268    89136620    7  HPFS/NTFS
/dev/sda8           19269       48641   235938591   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa876a876

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30515   245111706   83  Linux

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5aa75df1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+  83  Linux


sudo blkid:

> /dev/sda1: UUID="124CAAD24CAAAFC1" TYPE="ntfs" 
/dev/sda2: UUID="9843c115-83b8-45a4-9c9e-998d9bfd41a0" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ebab3cbd-66e4-46d7-9a9d-36493bafd54e" 
/dev/sda6: UUID="a962120f-b19b-4e66-b624-717852aa6eda" TYPE="ext3" 
/dev/sda7: UUID="D91DEA0B4BE1DE89" LABEL="Windows Storage" TYPE="ntfs" 
/dev/sda8: UUID="a084b93e-ea9d-49e0-817d-25b7e2d7159d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="LDSilver" UUID="2a57aceb-dfb9-9520-983a-e26dbbdc4b95" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="maarla" UUID="c567bf10-ab7e-4680-ec92-fb06ed0d8029" SEC_TYPE="ext2" TYPE="ext3" 


---

### Post by DarkDancer on 2008-05-15
bump....

---

### Post by DarkDancer on 2008-05-17
Bump....

---

### Post by DarkDancer on 2008-05-22
Just when you thought it was safe to come back to the forums.....

Bump!

---

### Post by vanadium on 2008-05-22
It is indeed quite frustrating to have no reply for a quite obvious problem. Let us first try if you can burn from the command line. If you have some wav files ready to create an audio CD, then you can create one from the command line as following. Open a terminal and make sure your working directory is that one where the wavs are (i.e. "ls" on its own must list your wavs, and only the wavs that will be written on the audio cd should be there)

```

{
  echo "CD_DA"
  for file in *.wav ; do
    echo "TRACK AUDIO"
    # echo "PREGAP 00:02:00"  # insert a 2-second silent gap before each track
    echo "FILE \"$file\" 0"
  done
} > toc
cdrdao write toc

```

This creates a toc file and the last command will attempt to write the audio cd. Eventual error messages will show up in great detail.

If it is a permission problem, repeat burning as root.

sudo cdrdao write toc

If that works, you certainly have a user permission problem (you do not belong to the correct group). If it doesn't work, it will get trickier: hardware problem? some other error that hopefully can be identified from the error messages?

---

### Post by DarkDancer on 2008-05-22
Hmmm, I don't have any wav files around would have to convert......

---

### Post by andrew.46 on 2008-05-23
Using Vanadium's idea perhaps try copying an audio cd:

[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

and see what (if any) error messages crop up.

   Andrew

---

### Post by DarkDancer on 2008-05-24
Ok, I haven't managed to convert the mp3's to waves, but using the method that andrew.46 detailed, I copied an existing audio cd with no trouble. No errors and I am listening to it right now.....

---

### Post by andrew.46 on 2008-05-25
Hi,

Glad to hear that you have successfully copied an audio cd:

> **DarkDancer said:**
> Ok, I haven't managed to convert the mp3's to waves, but using the method that andrew.46 detailed, I copied an existing audio cd with no trouble. No errors and I am listening to it right now.....

But of course now the plot thickens as I believe that k3b uses cdrdao for its audio cd copying. This suggests there may be a problem with your k3b setup rather than any problem your hardware, which is good news. Unfortunately I do not use k3b as I am a fully registered command line junkie :-). Any k3b experts here?

             Andrew

---

### Post by Spike-X on 2008-05-26
This just worked for me:

Got to Settings>Configure k3b>Programs>User Parameters

Set cdrdao to use /usr/bin/cdrdao

---

### Post by DarkDancer on 2008-05-27
Hey Spike-X, I tried that, but k3b would not allow me to make any changes there. I clicked, double clicked and right clicked and nothing happened. I even tried it sudo'ed. Nothing.

---

### Post by Spike-X on 2008-05-27
Which bit were you clicking on? You need to single-click next to 'cdrdao' under where it says 'Parameters'.

---

### Post by maestrobwh1 on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=217472&highlight=k3b+cdrdao](http://ubuntuforums.org/showthread.php?t=217472&highlight=k3b+cdrdao)

---

### Post by DarkDancer on 2008-05-27
Spike-X,

Ok, I got the command in there and...it didn't work. I am about to try maestrobwh1's suggestion.

---

### Post by DarkDancer on 2008-05-27
And maestro, that didn't help either, still the same error, but thnaks....anyone else?

---

### Post by superyounan1 on 2008-05-27
ok, this might be a group permissions problem. Go to the K3b setup and find settings for the group, then try System > Administration > Users and Groups, and add all your users into that group and to the cdrom group

---

### Post by DarkDancer on 2008-05-28
I'm afraid I'm not sure where the k3b setup is.

---

### Post by skullmunky on 2008-05-29
I have the same, or similar problem - posted onto another thread and just realized that thread's in the archive so will probably not get any answers there, yes?  

Permissions are fine (I'm in the cdrom group), also chmod'd a+rw my cdrom device, still get the error.  This is when trying to copy or burn audio cd's.  What's weird is, it's not all the time - I can sometimes burn 10, 20, CD's in a row with no problems at all, then bam, it stops working.

Thanks in advance for any insights, I love K3B, it's my favorite burning software of all time so it's killing me that it's having troubles.

btw the same error comes up in Brasero also.

```

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-16-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-109 1.17 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-109 '
Revision       : '1.17'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Encoding speed : 271x (20312 sectors/s) for libedc from Heiko Eißfeldt
pregap1: -1
Track 01: audio  100 MB (09:57.36) no preemp copy
Track 02: audio   79 MB (07:54.84) no preemp copy pregapsize:   0
Track 03: audio   83 MB (08:13.68) no preemp copy pregapsize:   0
Track 04: audio   75 MB (07:27.73) no preemp copy pregapsize:   0
Track 05: audio   56 MB (05:38.44) no preemp copy pregapsize:   0
Track 06: audio   66 MB (06:33.02) no preemp copy pregapsize:   0
Track 07: audio  112 MB (11:09.85) no preemp copy pregapsize:   0
Track 08: audio   67 MB (06:43.61) no preemp copy pregapsize:   0
Track 09: audio   90 MB (08:56.20) no preemp copy pregapsize:   0
Total size:      732 MB (72:34.74) = 326606 sectors
Lout start:      732 MB (72:36/56) = 326606 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Speed set to 5644 KB/s
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 33240
Starting to write CD/DVD at speed  32.0 in real RAW/RAW96R mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/wodim: WARNING: Drive returns wrong startsec (-150) using -11634 from ATIP
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF E6 5C 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 98 32 21 0E 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 9974305 (not valid) 
cmd finished after 0.001s timeout 40s
/usr/bin/wodim: Could not write Lead-in.
Writing lead-in at sector -11634
write leadin data: error after 12411360 bytes
Writing  time:   33.249s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=32 -raw96r driveropts=burnfree -eject -overburn -text -useinfo -audio -shorttrack /tmp/k3bCdCopy0/Track01.wav /tmp/k3bCdCopy0/Track02.wav /tmp/k3bCdCopy0/Track03.wav /tmp/k3bCdCopy0/Track04.wav /tmp/k3bCdCopy0/Track05.wav /tmp/k3bCdCopy0/Track06.wav /tmp/k3bCdCopy0/Track07.wav /tmp/k3bCdCopy0/Track08.wav /tmp/k3bCdCopy0/Track09.wav

```

---

### Post by andrew.46 on 2008-05-29
Hi,

Is there an easy way of using Jorg Schilling's cdrecord rather than wodim? I have had a good look at the Hardy Repository and it does not appear to be there. I am more used to cdrecord's close to perfect running on another distro and I would be interested to see if some of the errors would disappear if wodim was *not* used.

    Andrew

---

### Post by DarkDancer on 2008-06-02
bump

---

### Post by DarkDancer on 2008-06-06
Bump.

---

### Post by DarkDancer on 2008-06-22
bump....

---

### Post by DarkDancer on 2008-06-23
Just in case anyone is interested, I just tried to burn a cd of Ubuntu, and I have no permission. Will have to boot into Winders to burn the Ubuntu cd...that's just wrong....

---

### Post by VMC on 2008-06-23
DarkDancer,

I know how frustrated you may be. Thanks for hanging in there. I don't use K3B on much of anything. 

Your problem is K3B burns data correcly, but won't burn musci or audio. Is that correct?
Have you tried just uninstall K3B and then re-installing it? I have tons of mp3 files. I will see if it burns on mine.

---

### Post by DarkDancer on 2008-07-17
Well, I can try that, but we kind of have gotten away from the real problem, that no program will burn audio, or apprenmtly .isos.....

---

### Post by kaoticorder on 2008-07-21
You aren't the only person suffering from this problem...  I was reading a few other threads and one of them suggested examining your cd-rom via the command "lshw -C disk"  and seeing if one of the logical entries listed matches your cd-rom device under /etc/fstab.  

Thinking about it logically, I'm not sure why both of us can write a small handful of tracks yet not the entire CD.  Doesn't really follow that it loses permission halfway through the process.


I'll let you know if I discover anything relevant during my perusal of the forums...

Kaotic


Here are the links that I found the relevant information at:
    [http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount](http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount)
    [http://ubuntuforums.org/showthread.php?t=841940&highlight=k3b+error&page=3](http://ubuntuforums.org/showthread.php?t=841940&highlight=k3b+error&page=3)


I've tried following the advice and changing my cd-rom listing under /etc/fstab to /dev/cdrom0 instead of whatever it was... I'll let you know if it works on next reboot.

---

### Post by kaoticorder on 2008-07-21
Nope... Still nothing.  This means that I have more research to do.  I'll let you know if I find anything promising.

Kaotic

BTW-  Changing the permissions through CHMOD has no affect on any of the relevant programs (cdrecord, cdrdao, or wodim)

---

### Post by skullmunky on 2008-08-20
hi everyone,

no solution yet, but figured out some new elements of the problem.  i looked in dmesg and what was actually happening was NOT a permission problem, but a device timeout and errors of some kind which then led to the drive being unregistered as if it were just yanked out completely.  hence no permissions - the device doesn't exist anymore!  

i figured this out at a time i had no internet, so next time it happens i'll post the actual errors which'll be more helpful.

in the meanwhile, i can burn video DVD's as much as i like.  weird.

---

### Post by editrix on 2008-08-21
There's at least one serious bug with CD burning, and maybe more. You might want to check out my post [http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700) which gives a workaround, and also a link to the bug.

---

### Post by hpp3 on 2009-04-30
My solution to this is posted here:
[http://ubuntuforums.org/showthread.php?t=782644&highlight=cdrecord&page=4](http://ubuntuforums.org/showthread.php?t=782644&highlight=cdrecord&page=4)
Hope it helps...

---

