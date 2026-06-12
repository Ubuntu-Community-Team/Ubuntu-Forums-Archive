---
title: "Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart"
date: 2007-05-25
forum: General Help
---

### Post by dropkickfitz on 2007-05-25
Error: cannot find GRLDR in all drives
Unable to get past the boot menu.

This text comes up:

Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart.

No idea what a GRLDR is.

Can you help?

Thanks

---

### Post by bean123 on 2007-05-25
This is due to the limitation of NTFS boot code. i see you have a fat16 partition, move grldr there, and it should be fine.

---

### Post by tinybit on 2007-05-26
bean, the FAT16 might be dell's utility partition and with id "0xDE". It cannot be accessed in a normal way.

Yes, one can place grldr in a Dell UTIL-partition, but this must be done thru an unusual way.

The error "NTFS5: 3" should be clarified. And the code should be updated to fix the issue.

---

### Post by jharek on 2007-05-26
cant even get the bloody thing to install , all i get is some nonsense about grldr 

i see other people have this problem and their suggestion is to use a FAT16 partition? ARE YOU KIDDING ?

FAT16? ten years ago that wouldv'e been fine 

however it is now 2007, you'd think linux wouldve progressed beyond requiring ten year old formats, and displaying useless error messages.

seriously, how do you expect people like myself who hear such great things about linux, and think i'll check it out, see what the fuss is, maybe i'll switch to linux instead of buying vista , IF THE BLOODY THING WONT EVEN INSTALL , ill stick to XP thanks, at least that will install EVERY TIME ON ANY MACHINE and doesn't require some bodge-it-and-scarper ancient file system

---

### Post by tinybit on 2007-05-26
This is a problem on NTFS. I mean, this is a bug in grldr/grldr.mbr

I think the problem will be solved as soon as possible.

And at this moment, you may place a copy of grldr and menu.lst in the root dir of a FAT16/FAT32/EXT2/EXT3 partition or another NTFS partition.

---

### Post by robbielink on 2007-05-26
Yes - this is the Dell utility/recovery partition - I believe for the original poster and for myself. 
Can anyone explain how to put grldr in this partition - if that is actually the fix (is it?)

---

### Post by tinybit on 2007-05-26
You may firstly install grldr to a floppy, or using grub.exe to enter grub4dos.

Secondly, map dell's partition as floppy 1, i.e., drive B:

map (hd0,0)+1 (fd1)
map --hook

Then thirdly, boot to DOS in your drive A:

chainloader (fd0)/io.sys
boot

At last, at the DOS prompt, copy GRLDR and menu.lst from A: to B:

copy   A:\grldr   B:
copy   A:\menu.lst     B:

Note that the drive B: is exactly you Dell UTIL-Partition.

Eject your floppy and reboot. Should be OK.

---

### Post by jharek on 2007-05-27
thanks man, i've chilled out a bit now !!

 i put the grldr and menu.lst on my E:\ partition 

now when i choose ubuntu from the boot menu , the grub program runs 

but now it is telling me this :

Warning MBR Cylinders (38914) is greater than the BIOS (625192446) 

Some buggy BIOSes can hang when you access sectors exceeding the BIOS limit

find --set-root--ignore-floppies /wubi/boot/grub/menu.lst 

ERROR 17: file not found 


i can access the GRUB command line, but i dont know exactly what its trying to tell me or what to do about it 

any help would be appreciated 

incidentally i did try a livecd of pclinuxos , which seemed to work fine , even detecting my sound card which i was amazed at since the vista beta did not , and connecting to the internet with it was real easy, in stark contrast to the last time i tried linux (red hat 5) which involved searching for some seemingly random named help file in /usr/bla/what/ever/bla/bla/bla/bla/bla/../hidden/screw/you/wont/work/anywyz

atm tho i dont want to go through the hassle of altering the partitions of my hard drive for a proper install of linux(my xp is running about as good as its ever been), which is why i am interested in the Wubi/linux-as-a-file-on-ntfs, so i can experiment without screwing up my existing setup which is in constant use

---

### Post by tinybit on 2007-05-27
try to replace grldr with the latest build that can be found here:

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

At the moment of writing, it is:

[http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-26.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-26.zip)

---

### Post by robbielink on 2007-05-27
Thanks for the reply. 
Remembering that Wubi has the possibility of bringing non-technically minded windows users to Linux with an easy to install dual boot system that allows new users to try out Linux without mucking around with their Windows installation and making changes to their system - you will probably encounter more folks like me who "don't have a clue" about this but really want to make it work.
That said, I do have some small understanding of your directions but if you or anyone else can elaborate that would be most helpful. Here's what I do/don't understand:

> **tinybit said:**
> You may firstly install grldr to a floppy, or using grub.exe to enter grub4dos.

Does this mean to copy grldr to a floppy? Don't you also need menu.1st on the same floppy?
What if my system does not have a floppy drive - can I copy these to a CD?
> 
Secondly, map dell's partition as floppy 1, i.e., drive B:

map (hd0,0)+1 (fd1)
map --hook
"map" is not recognized as a command on my XP system using the command prompt. Am I supposed to be running grub to execute this command? How do I run grub? Trying to run grub from the command.com gives me this error:
"16 bit MS-DOS Subsystem
the NTVDM CPU has encountered an illegal instruction"
choosing either "close" or "ignore" terminates the application and closes the command window.
What is the correct method for running grub?


> Then thirdly, boot to DOS in your drive A:

chainloader (fd0)/io.sys
boot

At last, at the DOS prompt, copy GRLDR and menu.lst from A: to B:

copy   A:\grldr   B:
copy   A:\menu.lst     B:

Note that the drive B: is exactly you Dell UTIL-Partition.

Eject your floppy and reboot. Should be OK.
I'm assuming the rest of this is also run from grub so if that is the case I need help running grub.

Thanks for your patience.

---

### Post by tinybit on 2007-05-28
> **robbielink said:**
> Thanks for the reply. 
Does this mean to copy grldr to a floppy? Don't you also need menu.1st on the same floppy?
What if my system does not have a floppy drive - can I copy these to a CD?


You may first install grldr boot record onto the boot sector of your floppy, by running

bootlace.com --floppy --chs 0x00

And then place grldr and menu.lst in the root dir of your floppy.

You can also make a bootable cd using grldr. See readme for details.

> 
"map" is not recognized as a command on my XP system using the command prompt. Am I supposed to be running grub to execute this command? How do I run grub? Trying to run grub from the command.com gives me this error:
"16 bit MS-DOS Subsystem
the NTVDM CPU has encountered an illegal instruction"
choosing either "close" or "ignore" terminates the application and closes the command window.
What is the correct method for running grub?


"map" is a GRUB command, not a DOS command. 

GRUB.EXE cannot run from XP. It runs from a real DOS environment. Boot your system into DOS from your floppy(I assume you know about how to build a DOS bootable floppy and copy grldr, grub.exe and menu.lst to the floppy), and you can run GRUB.EXE there.

> 
I'm assuming the rest of this is also run from grub so if that is the case I need help running grub.


Yes. But the copy command should be run from DOS. Or you can copy files under your Windows or Linux if you'd like.

Note: bootlace.com is a utility of GRUB4DOS. you may download a latest grub4dos build at [http://grub4dos.jot.com/](http://grub4dos.jot.com/)

---

### Post by tuxcantfly on 2007-05-28
merged in the other thread about the "cannot find grldr in all drives" error

---

### Post by jharek on 2007-05-29
my saga continues :((

i downloaded the newer GRUB and placed it in both c:\ and e:\ partitions

this time kubuntu installed, rebooted, halfway through loading, something called SUPERCHECK said there was errors in the filesystem and fixed them, rebooted, Black screen with mouse cursor appeared, and PC froze there , after 10 minutes i decided it wasnt doing anything so 

booted back to XP, redownloaded wubi kubuntu , reinstalled like before, Supercheck came up like before, this time Kubuntu came up with the login/password screen, i logged in 

i wondered why kubuntu hadnt asked me for my internet details like the livecd of pclinuxos, so i assumed it would when i ran Konqueror, clicked on Konqueror, PC froze 

rebooted, loading dropped into bash console and told me 'apt-get' was missing , and to install it with command 'apt-get install' , so i did that and got told 'apt-get not found' , pressed enter, it tried to load and told me 'Kstartup' was missing

so i rebooted, bash console came up and told me 'Fschk' or something had found errors, run it manually

so i did only to be told runing 'Fsck' run on  a mounted filesystem could cause SEVERE errors' 

i ran it anywayz, rebooted, got told 'couldnt mount /proc' 

what the frak is going on? Is this Supercheck thing normal? Why didn't kubunti ask me for my internet details the one time it did actually appear to work? Why was apt-get missing and what the hell is it anyway? Why does it keep freezing? Why does rebooting appear to cause additional problems every time ? 

To say im not overly impressed would be something of an understatement, i'm really trying here to make the leap to linux but i keep getting problems even windows 3.11 would be proud of, any hints/help/ideas would be appreciated thanks

---

### Post by ago on 2007-05-29
Did you reboot cleanly or hard-reboot (shutting down the hard way)? In the second case you can cause file system corruption. You'd be better off to try the latest minefield anyway.

---

### Post by jharek on 2007-05-29
when pc is frozen , there is only one way to reboot 

what is minefield ?

---

### Post by ago on 2007-05-30
> **jharek said:**
> when pc is frozen , there is only one way to reboot 

[http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html](http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html)

---

### Post by jharek on 2007-05-30
i'm going to assume for a moment that youre not just taking the piss

even assuming that i wouldv'e even have known about this, i've got to manually edit a file (without knowing even how to edit a file in the console), (and if i tried 'edit' i would probably get told i have to 'apt-get edit' and 'apt-get not found' , then choose one from 20 options none of which are relevant to the symptoms, and without any kind of helpful info from linux and then do this sequence

Alt+SysRq+s - sync the disk
Alt+SysRq+e - try to nicely kill processes
(wait a little bit here)
Alt+SysRq+i - no more mister nice guy
Alt+SysRq+u - unmount disks
(wait a bit here, too)
Alt+SysRq+b - reboot

just to REBOOT!!! 

lmao, i can hard reboot XP all year long and nothing ever goes wrong with one flick of the power switch and here was i thinking linux was alledgedly a  more robust o/s 

still doesnt explain why it screwed up in the first place, i understand wubi is beta so wasn't expecting miracles but i can't understand why it has so many problems even performing a basic install

---

### Post by miketowninc on 2007-05-30
CAnt some one put this in the new version? how long will that take?

---

### Post by ecology2007 on 2007-05-30
All your problems are due to the abuse of hard reboots.
That ended up  corruption on the wubi filesystem.
You may have corrupted your windows drive filesystem too, as you would have doing the same thing under windows.

They have nothing related with this thread, which is an harmless warning error.
[Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart]("http://ubuntuforums.org/showthread.php?t=455078")

Uninstall wubi.
Run a file system check on all your drives inside windows.
Run defrag on all your drives.
Install wubi.

If you still have problems make a new thread with exact error message and an exhaustive description of your system.

---

### Post by miketowninc on 2007-05-30
Then why does it only happen on dells? I have dell and so does the guy that started the topic

---

### Post by tinybit on 2007-05-30
Dell's utility partition is a good place for startup files like GRLDR, MENU.LST,vmlinuz and initrd.

---

### Post by miketowninc on 2007-05-31
> **ecology2007 said:**
> All your problems are due to the abuse of hard reboots.
That ended up  corruption on the wubi filesystem.
You may have corrupted your windows drive filesystem too, as you would have doing the same thing under windows.

They have nothing related with this thread, which is an harmless warning error.
[Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart]("http://ubuntuforums.org/showthread.php?t=455078")

Uninstall wubi.
Run a file system check on all your drives inside windows.
Run defrag on all your drives.
Install wubi.

If you still have problems make a new thread with exact error message and an exhaustive description of your system.



Do you mean CHKDSk? or something else?

---

### Post by miketowninc on 2007-05-31
I ran the ckdsk and i did disk defrag and i still get the same error message!!

I have a dell inspiron 1150
2.40 GHZ
256 Ram
celeron
XP
what else?

thanks

---

### Post by jharek on 2007-05-31
Well , i gave up on wubi 

and download pclinuxos 2007 final 

backed up important stuff on my hard drive, ran livecd , internet worked fine straight away, so i followed online instructions to partition and install 

works fantastic cant say enough good things about pclinuxos

---

### Post by rnelson on 2007-05-31
Both Ubuntu and Kubuntu worked on a new Toshiba laptop A105. 

Wubi test2 and test 3 wanted to run in compatability mode on the Toshiba. 

Test2 was quite fussy. Test3 worked well

Both worked on a generic desktop, about two years old.

Everything fails with 

cannot find GRLDR in all drive. CTRL+ALT+DEL to restart

on a Compaq Presario 2100 Laptop - there are no utility partitions on the 60 gig drive that has been defragged.

I can't find any thing to do next.



r

---

### Post by tadinho on 2007-06-01
lol-me too. i've been frantically reading forums pretty much all day long but no to avail. However, i've managed to somehow get into GRUB but i don't know what to do next..
Can anybody help plz?!
Many thanks in advance!!

btw, I have a Dell Inspiron E1505 that has a Dell Util-part, 2 NTFS part., and FAT32 Recovery part.

---

### Post by ago on 2007-06-01
> **tadinho said:**
> lol-me too. i've been frantically reading forums pretty much all day long but no to avail. However, i've managed to somehow get into GRUB but i don't know what to do next..

did you have the "cannot find GRLDR in all drive. CTRL+ALT+DEL to restart " error? how did you get into grub? what do you see in the grub menu?

can you guys try a different grldr version from [http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/) and see if you still have the same issue (unzip and replace grldr)?

Also try to place c:\wubi\boot\grub\menu.lst in the same folder where you have ntldr.

---

### Post by tinybit on 2007-06-01
XP users may try the grldr with grub4dos 0.4.2 final,  which can be found here: 

[http://grub4dos.jot.com/](http://grub4dos.jot.com/)

Note: VISTA was not supported as with grub4dos 0.4.2 final.

---

### Post by bean123 on 2007-06-01
Please try the new grldr.mbr, it should fix the problem.

Download grldr.mbr, place it in C:\, then

In XP/2003, modify boot.ini:

C:\grldr.mbr="GRUB"

In Vista, use bcdedit.

Don't need to change grldr.

---

### Post by miketowninc on 2007-06-01
that didnt help did it really work with you?

---

### Post by bean123 on 2007-06-01
Please run fstest.bat to get debug information.

---

### Post by miketowninc on 2007-06-02
heres ftest.bat


------------------------------------------------------------------- 
fstest info C:\ 
------------------------------------------------------------------- 
part_start: 0x17886
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000
------------------------------------------------------------------- 
fstest inode C:\$MFT 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (r,sz=160)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=100204544)
    6291456+32
  $BITMAP (0xB0) (nr,sz=12232)
    6291448+8,18322600+16
Attr List:
  $STANDARD_INFORMATION (0x10) (r,mft=0x0,sz=72)
  $FILENAME (0x30) (r,mft=0x0,sz=74)
    $MFT
  $DATA (0x80) (nr,mft=0x0,vcn=0x0,sz=100204544)
  $DATA (0x80) (nr,mft=0xF,vcn=0x4,sz=97452032)
  $BITMAP (0xB0) (nr,mft=0x0,vcn=0x0,sz=12232)
------------------------------------------------------------------- 
fstest inode C:\. 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $SECURITY_DESCRIPTOR (0x50) (nr,sz=4144)
    29246416+16
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=272)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=12288)
    6378880+24
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list C:\ 
------------------------------------------------------------------- 
00000C05             0  [DOCUME~1]
00000BE1        250032  ntldr
00002EAE             0  [4452c010af3b070b6e7ee486c0]
00002EAE             0  [4452C0~1]
0000BF9F             0  [Alien Arena 2007]
0000BF9F             0  [ALIENA~1]
000015C8             0  AUTOEXEC.BAT
00000BFF           251  boot.ini
0000FEEA             0  bvpcn.exe
0000FEE9             0  cijvsusf.exe
000029AD          8774  ComboFix.txt
000015C7             0  CONFIG.SYS
0000C10F             0  [Converted]
0000C10F             0  [CONVER~1]
00002EB0             0  [d02f6c20829783538a]
00002EB0             0  [D02F6C~1]
00002685             0  [DBBackup]
00000A81             0  [DELL]
0000D530             0  [Dev-C++]
0000D530             0  [DEV-C_~1]
00000C05             0  [Documents and Settings]
00012857             0  [DriveKey]
00008FEF          1288  DVDBurner.log
00008FEF          1288  DVDBUR~1.LOG
0000C6FD          3080  egd.txt
0000897A            10  ggxvte.ufx
0000FF56        178469  grldr
00007E93          8192  grldr.mbr
0000FEEC             0  hbvoqwep.exe
00004F50     266756096  hiberfil.sys
0000FEED             0  houkyvyc.exe
00012EF1             0  [ijji]
000120D7        230424  img1-001.raw
00001A50             0  IO.SYS
00003ACC           125  ioSpecial.ini
00003ACC           125  IOSPEC~1.INI
0000A5FA             0  [KPCMS]
00008842           777  log.txt
0000B840           649  logdll.txt
00002851             0  [Mathadv]
0000927B          9528  mediamp3.dat
00001A51             0  MSDOS.SYS
00003AF6             0  [MSOCache]
000094B3             0  [My Music]
000039F4             0  [My Shared Folder]
000094B3             0  [MYMUSI~1]
000039F4             0  [MYSHAR~1]
00000BE5         47564  NTDETECT.COM
00008863             0  [OLDDRIVR]
00003BDC           114  omginst.txt
00016CDC     400031744  pagefile.sys
00000DAD             0  [Program Files]
00000DAD             0  [PROGRA~1]
00002E97             0  [QooBox]
00004645          1309  rapport.txt
000028E7             0  [RECYCLER]
00002F1F             0  [rvrcache]
0000886D             0  [sstfrdlx]
0000233A             0  [System Volume Information]
0000233A             0  [SYSTEM~1]
0000C6DD             0  [Temp]
00003316             0  [usa_mcc]
0000DD25          1246  VoxLibAudioWatchDog_log.txt
0000DD25          1246  VOXLIB~1.TXT
00002A1C             0  [VundoFix Backups]
00002A21           191  VundoFix.txt
00002A1C             0  [VUNDOF~1]
0000001C             0  [WINDOWS]
0000FB6D             0  [wubi]
000042BC             0  [WUTemp]
------------------------------------------------------------------- 
fstest inode C:\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    10998456+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list C:\wubi\ 
------------------------------------------------------------------- 
0000FBD9             0  [boot]
0000FBE3         17989  COPYING
0000FB70             0  [disks]
0000FB74             0  [docs]
0000FBD8             0  [install]
0000FBDC         18326  license.txt
0000FBE4          2968  README.txt
0000FB75             0  [tools]
0000FC83         78744  Uninstall.exe
0000FC83         78744  UNINST~1.EXE
------------------------------------------------------------------- 
fstest inode C:\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)
------------------------------------------------------------------- 
fstest list C:\wubi\boot\ 
------------------------------------------------------------------- 
0000FBDA             0  [grub]
0000FBDD       7919247  initrd
0000FBDE       1745100  linux
0000FBDB             0  [winboot]
------------------------------------------------------------------- 
fstest comp C:\grldr 
------------------------------------------------------------------- 
File size : 178469
Comparing 
Succeed
------------------------------------------------------------------- 
fstest comp C:\wubi\boot\linux 
------------------------------------------------------------------- 
File size : 1745100
Comparing .
Succeed
------------------------------------------------------------------- 
fstest comp C:\wubi\boot\initrd 
------------------------------------------------------------------- 
File size : 7919247
Comparing .......
Succeed
------------------------------------------------------------------- 
You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965"

---

### Post by sp0rk on 2007-06-02
I saw a few other threads about this, but my error is slightly different.  I only have one harddrive installed with no other partitions.  No floppy drive either.  But I get this error after I've installed Wubi:

TRY (hd0,0) NTFS5 :3
Try (hd0,1) invalid or null
Try (hd0,2) invalid or null
Try (hd0,3) invalid or null
Try (fd0) invalid or null
Error: cannot find GRLDR in all devices
Press ctrl+alt+del to restart.

I tried defragmenting the drive and updating GRUB4DOS.  Any other suggestions?

Thanks.

---

### Post by sba99jpd on 2007-06-02
If it's of any use I'm also having the same problem on a Packard Bell laptop.

---

### Post by bean123 on 2007-06-02
maybe there is still some bug, let me check.

by the way, have you changed boot.ini to use grldr.mbr instead of grldr ?

---

### Post by miketowninc on 2007-06-02
let me look

---

### Post by miketowninc on 2007-06-02
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\grldr.mbr="GRUB"
c:\grldr="Ubuntu"



is that right? that is how i had it.

---

### Post by miketowninc on 2007-06-02
or c:\grldr.mbr="Ubuntu"

---

### Post by rnelson on 2007-06-02
I tried the glder_mbr.zip and still get this same error.

Here is the result of the ftest.bat

------------------------------------------------------------
fstest info C:\ 
------------------------------------------------------------------- 
blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x30
------------------------------------------------------------------- 
fstest inode C:\$MFT 
------------------------------------------------------------------- 
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (r,sz=192)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=229729280)
    48+32
  $BITMAP (0xB0) (nr,sz=28048)
    16+32,101389592+8,73258088+8,51646688+8
Attr List:
  $STANDARD_INFORMATION (0x10) (r,mft=0x0,sz=72)
  $FILENAME (0x30) (r,mft=0x0,sz=74)
    $MFT
  $DATA (0x80) (nr,mft=0x0,vcn=0x0,sz=229729280)
  $DATA (0x80) (nr,mft=0xF,vcn=0x4,sz=190279680)
  $DATA (0x80) (nr,mft=0x10,vcn=0xBC3F,sz=0)
  $BITMAP (0xB0) (nr,mft=0x0,vcn=0x0,sz=28048)
------------------------------------------------------------------- 
fstest inode C:\wubi 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    wubi
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
    47821400+8
  $BITMAP (0xB0) (r,nm=$I30,sz=8)
------------------------------------------------------------------- 
fstest list C:\wubi\ 
------------------------------------------------------------------- 
000003AA             0  [boot]
00000E8A         17989  COPYING
0000039D             0  [disks]
0000039E             0  [docs]
000003A9             0  [install]
000003AE         18326  license.txt
00000E8F          2968  README.txt
0000039F             0  [tools]
00000EC7         78780  Uninstall.exe
00000EC7         78780  UNINST~1.EXE
------------------------------------------------------------------- 
fstest inode C:\wubi\boot 
------------------------------------------------------------------- 
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    boot
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=536)
------------------------------------------------------------------- 
fstest list C:\wubi\boot\ 
------------------------------------------------------------------- 
000003AB             0  [grub]
00000593       7922766  initrd
000005CE       1745100  linux
00000392          4130  menu.lst
000003AD             0  [winboot]
------------------------------------------------------------------- 
You can post the results here : "http://ubuntuforums.org/showthread.php?t=439965" 



-------------


I didn't change the boot.ini myself. The installer may have, but I don't know yet.

I'll try that right now.


r

---

### Post by rnelson on 2007-06-02
That is the same error I get on the Compaq Presario 2100 with one harddrive (60gig), one NTFS partition, and no floppy.

No luck so far.

It hasn't come up in a while, but someone should say thank you to Bean, Ago, all all the others who I can't recall right now - for all the help and amazing work here.

Despite the niggles, I'm really excited about being able to install and learn about Ubuntu Linux without the specter of altering partitions. 

I've been wanting to use Linux for a while now, but it will take some time and some learning to get all my work divorced from the windows system. I'm now Access-free, with MySQL and OOo, but I've got a ways to go before I can do most of my work without MS.



r

---

### Post by sp0rk on 2007-06-02
Just to add, I tried the grldr.mbr that bean linked in the other thread.  It returned the exact same error, except the 3 after NTFS5: was a 2.

---

### Post by bean123 on 2007-06-02
ok, i found the bug, please try out the new version.

---

### Post by sba99jpd on 2007-06-02
Hi,

Thanks for that.  I was having the same problem as the original poster, but the grldr attached in the last post does help - to an extent, but I now have "error 17; file not found" and apparently the file it is looking for is menu.1st

Thanks

---

### Post by miketowninc on 2007-06-02
HI bean
hI i tryed it too and i go error8:kernel must be loaded before..

i think my boot.ini is the problem can you tellme how it looks like?
thanks

---

### Post by bean123 on 2007-06-02
Can you get into the grub console ?

---

### Post by miketowninc on 2007-06-02
yes i can
but it says that error

---

### Post by tuxcantfly on 2007-06-02
merged in the other thread discussing this same issue

---

### Post by bean123 on 2007-06-02
The ntfs boot code have been intergarted into grldr, please try.

grldr.mbr is not needed anymore, you can delete it and remove the corresponding setting in boot.ini.

---

### Post by miketowninc on 2007-06-02
how did the boot.ini look like before? i dont remember?

---

### Post by miketowninc on 2007-06-02
like this:  c:\grldr.mbr="Ubuntu"

---

### Post by bean123 on 2007-06-02
> **miketowninc said:**
> like this:  c:\grldr.mbr="Ubuntu"

It should be like this:

C:\grldr="Ubuntu"

remove the C:\grldr.mbr=... line.

---

### Post by miketowninc on 2007-06-02
i did again with the new one same problem

it just has grub> and i type boot
and it says
no kernel


i extract grld to C:
is that the right directory? or does wubi have a directory where is should extract to?

---

### Post by miketowninc on 2007-06-02
what should i do??????????

---

### Post by miketowninc on 2007-06-02
> **bean123 said:**
> It should be like this:

C:\grldr="Ubuntu"

remove the C:\grldr.mbr=... line.


ok
didnt see that before sorry im so dumb

---

### Post by bean123 on 2007-06-02
i think the menu file is missing, is there menu.lst in C:\ ?

---

### Post by miketowninc on 2007-06-02
Nope no menu.lst


wierd

---

### Post by bean123 on 2007-06-02
By default, grldr will scan / , /boot/grub and /grub for menu.lst. i think wubi have changed the search path. you can modify the preset menu with grubmenu, but the most easy way is to find menu.lst, and copy it to C:\.

---

### Post by miketowninc on 2007-06-02
ok i found it in the grub folder of the wubi folder

i will copy and then restart

thanks for the help

---

### Post by miketowninc on 2007-06-02
ok it is installing now on my other pc


thanks bean good job

---

### Post by dropkickfitz on 2007-06-03
Wow

I've been away for a week and look forword to reading this post.

I'm glad I am not the only one with this issue.

"Dude, it's a Dud!"

I will try to do what the pro's recommend and get back to you all soon.

Thanks

DKF

---

### Post by dndrich on 2007-06-03
I am new to this forum, and tried Wubi.  I got the same error message as above.  I have NTFS.  I am hopeful that this will be corrected in the Wubi code so that I don't have to go through the complex series of instructions above.  Is it likely that Wubi will be set up to handle NTFS soon?  That would be great.

Daniel

---

### Post by ago on 2007-06-04
Test3 should be ok with this. 

Also not c:\menu.lst is embedded with grldr

If you have multiple partitions copy c:\grldr to each drive

---

### Post by bean123 on 2007-06-04
I found a new bug. if you are still having trouble with grub, check out the new version.

---

### Post by ago on 2007-06-04
bean123 any particular reason why you keep shipping grldr.mbr?

---

### Post by ago on 2007-06-04
Note that if you use the grldr from the file above you may have to copy c:\wubi\boot\winboot\menu.lst into c:\ , we stopped copying menu.lst into c:\ since that is now embedded withing grldr itself, if you change grldr you also have to make sure that there is a menu.lst file under c:\

---

### Post by bean123 on 2007-06-04
Vista user need to use grldr.mbr as boot file.

---

### Post by ago on 2007-06-04
> **bean123 said:**
> Vista user need to use grldr.mbr as boot file.

Can't they be unified? I noticed that XP can also use grldr.mbr

---

### Post by bean123 on 2007-06-04
In fact, grldr.mbr is more flexible, it works in Windows 2000/XP/2003/Vista, and you can use grubinst to change boot parameter. for example:

grubinst -o -b=grldr1 grldr.mbr

The generated grldr.mbr would load grldr1 instead of grldr.

grldr is actually grldr.mbr+pre_stage2. The first 16 sector of grldr is almost identical to grldr.mbr, it's used to load the rest of the file.

Vista doesn't support boot file larger than 8k, so you must use grldr.mbr.

---

### Post by Computer Guru on 2007-06-04
Bean, can i also do 
 
```
grubinst -o -b=boot/grldr grldr.mbr
``` and have grldr.mbr load boot/grldr instead?

---

### Post by bean123 on 2007-06-04
> **Computer Guru said:**
> Bean, can i also do 
 
```
grubinst -o -b=boot/grldr grldr.mbr
``` and have grldr.mbr load boot/grldr instead?

Nope, grldr.mbr only scans file in the root directory.

---

### Post by ago on 2007-06-04
bean123, I was only trying to eliminate files from C:\, we can have as many files as we want into C:\wubi\boot\winboot. My understanding so far is that I can have only grldr for XP, but need grldr and grldr.mbr for Vista.

---

### Post by Computer Guru on 2007-06-04
Ago: In my testing, it isn't possible to load GRLDR from the BCD without GRLDR.mbr
 
This is quite ridiculous, MS playing games again. I've been speaking to the developers of the BCD, and they're telling me that I should be able to run grub.exe *directly *from the vista bootloader, but I can't seem to get that to work although grub.exe *does* meet all the requirements they put forth for an executable from the BCD.
 
However, there *is* a workaround, but it's not pretty.
The way I was doing it earlier, I was grubinst to setup stage1 and stage2. Both files could be placed in any directory you want, then you can tell stage1 where stage2 is, and reference stage1 from the BCD.
 
However, this is a very buggy and fragile method compared to GRLDR, so I decided to bite the bullet and just stick GRLDR in the root and hope no one notices :P
 
For me the real kicker though was that the stage1+stage2 method only supported ext2/3fs, fat32, and NTFS to some extent. No ReiserFS support and the NTFS would break if you even defrag your drive.

---

### Post by ago on 2007-06-04
grldr + grldr.mbr is more than fine, I was just being picky. One thing though is that in the future we might rename the items under c:\ so that we have no issues when uninstalling.

grldr.wubi
grldr.mbr.wubi

---

### Post by bean123 on 2007-06-04
> **ago said:**
> grldr + grldr.mbr is more than fine, I was just being picky. One thing though is that in the future we might rename the items under c:\ so that we have no issues when uninstalling.

grldr.wubi
grldr.mbr.wubi

Currently,  grldr.mbr only supports filename that is at most 7 characters long, including the embeded period, so you need to shorten above names.

---

### Post by ago on 2007-06-04
wubildr
wubildr.mbr (I assume that does not have a 7 char restriction)

---

### Post by dndrich on 2007-06-05
OK, I've been trying to follow this thread, but it is hard to understand.

I have an older Dell m600 with no floppy drive.  I got the cannot find GRLDR error as above.  I have NTFS, but I also have a small partition left over from dell that is FAT 32.  It is only about 32 megs, and I have no idea what is in it.  So how do I get Wubi to install correctly?  Can somebody give me a step by step?  I would love to try this setup.

Daniel

---

### Post by bean123 on 2007-06-05
you should be able to resolve this problem with the latest build at #63.

to use it, just overwrite C:\grldr (i assume you install to C:) with the file from the attachment, and copy c:\wubi\boot\winboot\menu.lst to C:\.

if it doesn't work, please run fstest.bat to capture debug information.

---

### Post by ago on 2007-06-05
beanm find-file does not work on my fat32 partition

fstest info gives: 

ntfs_mount: 0

---

### Post by bean123 on 2007-06-05
> **ago said:**
> beanm find-file does not work on my fat32 partition

fstest info gives: 

ntfs_mount: 0

fstest only works in ntfs partition.

can you see the file list with [TAB] ?

---

### Post by tinybit on 2007-06-05
ago:

Type

geometry (hdX)

to show the drive info.

Type

root (hdX,Y)

to display the filesystem info of your FAT32 partition.

---

### Post by dndrich on 2007-06-06
OK, please help.  I am a novice at this.  Here is what I did.  I have a Dell m600 laptop.  It has a small fat 16 partition, and the standard large NTFS partition.  I downloaded and ran wubi.  It gave the grldr error.  I downloaded the new version of glrdr from post #63.  I ran it.  I have copied the list file to c:.  I now get past the first error to grub>, whatever that is.  I typed "boot", because I saw somebody else did that.  I got error 8, kernel must be loaded before booting.  I hit escape, and it looks like I am in some program called Grub4dos.  What do I do now?  I can't get past this point.  I am really a novice, so I am amazed I have gotten this far.  What am I supposed to do now?  Do I have to copy something to the small fat 16 partition, and if so, how do I do it without a floppy drive?

Daniel

---

### Post by bean123 on 2007-06-06
> **dndrich said:**
> OK, please help.  I am a novice at this.  Here is what I did.  I have a Dell m600 laptop.  It has a small fat 16 partition, and the standard large NTFS partition.  I downloaded and ran wubi.  It gave the grldr error.  I downloaded the new version of glrdr from post #63.  I ran it.  I have copied the list file to c:.  I now get past the first error to grub>, whatever that is.  I typed "boot", because I saw somebody else did that.  I got error 8, kernel must be loaded before booting.  I hit escape, and it looks like I am in some program called Grub4dos.  What do I do now?  I can't get past this point.  I am really a novice, so I am amazed I have gotten this far.  What am I supposed to do now?  Do I have to copy something to the small fat 16 partition, and if so, how do I do it without a floppy drive?

Daniel

you can't just type "boot", you need to load the kernel and initrd first. but you don't need to know the details, menu.lst would do it for you.

if you copy menu.lst to C:\, it should be loaded automatically. if not, try this command:

grub> find --set-root /menu.lst

it would find menu.lst, then

grub> configfile /menu.lst

it would load the menu.lst file.

---

### Post by dndrich on 2007-06-06
I will try this tonight when I get home.  I do have menu.lst in c:\, but for some reason that does not work.  So I will try what you say.  After that, will it remember automatically?

Daniel

---

### Post by miketowninc on 2007-06-06
YOu have to do something else i had that to you have to download the grldr.zip its in this thread from bean123. Andyou have to extract that to the C:/ then it will work for sure i had the same problem the first time. :0

---

### Post by miketowninc on 2007-06-06
here is the link to grld.zip

[http://ubuntuforums.org/attachment.php?attachmentid=34146&d=1180806484](http://ubuntuforums.org/attachment.php?attachmentid=34146&d=1180806484)

---

### Post by ago on 2007-06-06
Latest minefield includes the latest grldr
[http://cutlersoftware.com/ubuntusetup/devel/minefield](http://cutlersoftware.com/ubuntusetup/devel/minefield)

---

### Post by dndrich on 2007-06-06
Whoo, boy.  I just can't seem to get this to work.  I downloaded the latest build from the link above.  Still no go.  I don't get past control-alt-delete with that build.  glrdr is renamed something like wubiglr.  I really want to make this work, so I need to start from scratch.  So, if I were to start from scratch, what should I do?  Remember, I have a Dell m600 laptop with NTFS as the main partition, and a small fat 16 partition that came with the computer from Dell.  I have no floppy.  Thoughts?  I have tried everything on this thread except copying glrdr into the fat 16 partition.  I don't know how to do that without a floppy.

---

### Post by bean123 on 2007-06-06
> **dndrich said:**
> Whoo, boy.  I just can't seem to get this to work.  I downloaded the latest build from the link above.  Still no go.  I don't get past control-alt-delete with that build.  glrdr is renamed something like wubiglr.  I really want to make this work, so I need to start from scratch.  So, if I were to start from scratch, what should I do?  Remember, I have a Dell m600 laptop with NTFS as the main partition, and a small fat 16 partition that came with the computer from Dell.  I have no floppy.  Thoughts?  I have tried everything on this thread except copying glrdr into the fat 16 partition.  I don't know how to do that without a floppy.

Try the latest build here:

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

About the menu.lst problem, you can embeded menu.lst in grldr, first download grubutil:

[http://download.gna.org/grubutil/](http://download.gna.org/grubutil/)

there is a tool called grubmenu, then:

grubmenu import grldr menu.lst

this will embed menu.lst in grldr.

---

### Post by dndrich on 2007-06-06
Thanks for trying to help.  Do I run it from within Windows?  How do I run it?  And which version of Wubi should I try?

Daniel

---

### Post by bean123 on 2007-06-06
> **dndrich said:**
> Thanks for trying to help.  Do I run it from within Windows?  How do I run it?  And which version of Wubi should I try?

Daniel

open a cmd.exe windows, and type the command. you may want to change grldr and menu.lst to the actual location of the files. wubi version does not matter.

---

### Post by dndrich on 2007-06-06
OK, I went to that link for grub install, and there are like 35 versions.  Which one do I download?

---

### Post by bean123 on 2007-06-06
> **dndrich said:**
> OK, I went to that link for grub install, and there are like 35 versions.  Which one do I download?

[http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-06.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-06.zip)
[http://download.gna.org/grubutil/grubutil-1.1-bin-w32-15.zip](http://download.gna.org/grubutil/grubutil-1.1-bin-w32-15.zip)

---

### Post by dndrich on 2007-06-06
Wow!  You're quick!

OK, I have downloaded those.  Now, I stupidly managed to delete my nearly 700 meg iso of Ubuntu (argh!) as I was playing around with this.  So, I am currently downloading another iso, should be done in an hour.  I will continue to run the latest build of wubi, and install.  Then I'll install the latest grub4dos, and move glrdr to c:\, and then run grubutil, and check the box for embeded?  Is that the order I should try?

Daniel

---

### Post by dndrich on 2007-06-06
This is just endlessly frustrating.  I have tried these things, but they don't really seem to do the trick.  I tried opening the command window, and using grubmenu as described.  It crashes and does not do whatever it is supposed to do.  I have tried getting past control alt delete, and it just sticks on ntfs and won't even get to grub now.  I just need to start over.  What would you suggest?  How do I load grub4dos as downloaded?

Daniel

---

### Post by bean123 on 2007-06-07
> **dndrich said:**
> This is just endlessly frustrating.  I have tried these things, but they don't really seem to do the trick.  I tried opening the command window, and using grubmenu as described.  It crashes and does not do whatever it is supposed to do.  I have tried getting past control alt delete, and it just sticks on ntfs and won't even get to grub now.  I just need to start over.  What would you suggest?  How do I load grub4dos as downloaded?

Daniel

Run fstest.bat to capture debug info, it may be another ntfs bug.

Also paste your menu.lst here, i embed it for you.

---

### Post by dndrich on 2007-06-07
oh, my god!  I copied a version of glrdr into c:, ran grubmenu as described, and it looks like ubuntu is installing!  Wow!  I think you must have been correct, and it appears that I may have it installing!  Right now it is formatting the virtual disk!  So I think I am there.  Thanks for your help.  I will keep you posted if this works!

Daniel

---

### Post by ago on 2007-06-07
I have added the latest grldr code to the minefield build: [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by dndrich on 2007-06-07
OK, thanks for your help.  I don't know quite what I did, but Ubuntu is now loaded and running fine!  I can't print over my network or get my wireless to work, but that is another story...at least Ubuntu is working!

Daniel

---

### Post by rnelson on 2007-06-08
Using the last minefield with the Compaq Presario 2100 laptop.

Still seeing this error.

Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart

I'll try again later.


r

---

### Post by bean123 on 2007-06-08
> **rnelson said:**
> Using the last minefield with the Compaq Presario 2100 laptop.

Still seeing this error.

Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart

I'll try again later.


r

You are not using the latest version of fstest.exe, because error message "Multiple $DATA not supported" is no longer displayed.

---

### Post by minoas on 2007-06-08
Same here tried Wubi-7.04-minefield-178.52.exe up to Wubi-7.04-minefield-180.52.exe and kept gettting this message.I also noticed GRLDR is NOT created on any drives but wubildr is.Also Test3 works ok but im getting the cannot shudown issue with the NTFS configuration tool of Ubuntu.S

---

### Post by ago on 2007-06-08
Bean123,

I have the issue when using c:\wubildr="Ubuntu" in boot.ini -> "cannot find GRLDR in all drive".

Note that if I rename wubildr to grldr (and edit boot.ini accordingly) then it works fine.

It looks like the first chunk of grldr (~grldr.mbr) looks for "grldr" in order to load a second chunk  and since the "grldr" name is "hardcoded" in the first chunk, it fails whenever grldr is renamed.

I know how to target a different file by using grubinst grldr.-o=wubildr wubildr.mbr, but I do not know how to use grubinst to generate grldr as opposed of grldr.mbr.

---

### Post by bean123 on 2007-06-09
You need to change the boot file name embeded in grldr with a hex editor.  Just find all occurrences of GRLDR and grldr within the first 16 sectors and change it to wubildr.

For grldr.mbr, you don't need to do it manually, grubinst can be used to generate customized boot file:

grubinst -b=wubildr -o c:\wubildr.mbr

---

### Post by tinybit on 2007-06-09
> **bean123 said:**
> You need to change the boot file name embeded in grldr with a hex editor.  Just find all occurrences of GRLDR and grldr within the first 16 sectors and change it to wubildr.


This has a problem with ext2/ext3 partition boot record. The boot sector code will check the length of the filename "grldr", which is 5 characters. If wubildr is to be loaded, the length should also be changed to 7.

See this piece of code in grldrstart.S:

        lodsw                   /* AL=name_len, should be 5 for grldr */
                                /* AH=file_type(1 for regular file) */
        cmpw    $0x0105, %ax

The 0105 (for grldr)should be changed to 0107(for wubildr).

---

### Post by ago on 2007-06-09
For the moment I will use wubildr.mbr to "chainload" to wubildr then

---

### Post by ago on 2007-06-09
Can you all please try the latest minefield (194.52) it should sort out the issues above.

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by zyclop on 2007-08-07
what all  these esteemed linux professionals forget to tell you is:

1] create a bootable dos floppy from XP formatting a dos bootable floppy
2] copy grub.exe and all other files that you might find after extracting
onto the floppy. like grldr and menu.lst and such.
3] boot the floppy into dos.
4] run grub.exe
5] enter command mode, hit tab and go from there.

hope this helps.
zyclop

---

### Post by tuxcantfly on 2007-08-08
> what all these esteemed linux professionals forget to tell you is:

1] create a bootable dos floppy from XP formatting a dos bootable floppy
2] copy grub.exe and all other files that you might find after extracting
onto the floppy. like grldr and menu.lst and such.
3] boot the floppy into dos.
4] run grub.exe
5] enter command mode, hit tab and go from there.

hope this helps.
zyclop

Or, alternatively, just install GRUB to the MBR and go for a standard install.

---

### Post by ines sarria on 2008-11-21
hi i'm ines and i dont understand... i have the same problem

try (hd0,0) ntfs5:no wubildr
try (hd0,1) invalid or null
try (hd0,2) invalid or null
try (hd0,3) invalid or null
try (fd0) invalid or null
Error: cannot find GRLDR in all devices. press ctrl+alt+del to restart

Que hago?? copio el archivo grldr_mbr en c: y ya??? i need your held please

---

### Post by me.translucent on 2009-02-03
same problem is with me .. i too have a dell (dell inspiron 1520)

---

### Post by svrider1000 on 2009-02-13
Can anyone paste what the entire boot.ini should look like. I see people saying add this line here but if I saw what should be there I could just copy it.

Thanks

j

---

### Post by thbj on 2009-02-15
Hi,

I must admit that I haven't read through this whole thread, but maybe I can help someone since the problem is similar to the problem I had. You can maybe use part of my solution regarding booting GRUB on NTFS:

 [http://www.boot-land.net/forums/index.php?showtopic=7109](http://www.boot-land.net/forums/index.php?showtopic=7109)

Here I describe using the newest GRUB4DOS, that can be found found here: 

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

If this helps, great. Otherwise sorry to bother you :-)

Best Regards,

Thomas Bille J.

---

### Post by radek- on 2009-02-23
Hi, I tried to boot by using a bootable USB created with Ubuntu's own "Create bootable USB device" program. I then tried to boot via this USB memory but got the missing GRLDR error. I copied glrd and menu.lst files from Grub4Dos but it still gave me some error messages and then led to a menu with all kinds of booting options. I tried to choose the usb memory but it just gave the GRLDR error and led back to menu. I tried also some option with Linux but it just led to dos.

Then I read thbj's guide (previous message) but there isn't a menu.lst in the USB created with Ubuntu's program. So should I still do the edits on C:\ as thbj guided or should I use some other option in the menu I described earlier (assumingly Grub4dos menu)

EDIT: Got Ubuntu to boot by using Unetbootin, weird thing thought that creating bootable USB in Ubuntu doesn't seem to work but..

---

### Post by Servopal on 2009-04-27
I'm totally new to Linux/Ubuntu, and have been trying to install the new Ubuntu (Jaunty Jackalope) in windows, and I've been getting this exact same message.

I'm really shocked this this is now two years later, and the same problem is still there.

I don't understand most of what's in this thread, to be honest... And it seems like lots of other people didn't either...  but I'd REALLY like to install Ubuntu in windows.  i can't keep working with just the live disk, and I don't want to do that partition thingie until I know I want to keep Ubuntu.

I'd be REALLY grateful if anybody can offer any (easy to understand) advice.

I did error check and defrag my drive before installing Ubuntu, but it didn't help.

---

### Post by kd0afk on 2009-04-30
I too am having problems with this. I get the same error.
I am trying to install Ubuntu with Unetbootin and it goes ok till I get to the OS choices screen and when I choose Unetbootin I get the error. Please could someone condense this information into a tidy little package and post the directions. I, as well as many other noobs would really appreciate it.

---

### Post by kd0afk on 2009-04-30
> **thbj said:**
> Hi,

I must admit that I haven't read through this whole thread, but maybe I can help someone since the problem is similar to the problem I had. You can maybe use part of my solution regarding booting GRUB on NTFS:

 [http://www.boot-land.net/forums/index.php?showtopic=7109](http://www.boot-land.net/forums/index.php?showtopic=7109)

Here I describe using the newest GRUB4DOS, that can be found found here: 

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

If this helps, great. Otherwise sorry to bother you :-)

Best Regards,

Thomas Bille J.
I followed your directions to the letter but I am still getting the error.

---

### Post by sae.area on 2009-05-11
Hi,

I have a Toshiba Satellite A210-287 laptop running Windows Vista Home Premium Edition 32 bit. The 320 GB hard drive includes a 1,6 GB EISA configuration hidden partition at the beginning, a C partition and an E partition (all NTFS). The letter D is already taken by the DVD drive. 

I had installed ubuntu via wubi onto C and ran into the same problem as described above.

Then I uninstalled it from C and installed it to E, but the same problem occurred. 

Then I looked with the help of BCEDIT to check the references and they looked ok to me. (It pointed to the ubuntu folder on E)

But the loader files where installed on C and after I moved the files from C to E it started to work.

---

### Post by foofiebeast on 2010-05-13
So this problem still hasn't been resolved really?

I tried installing 10.04 on my dell "optiplex gx280" today and ran into this cannot frind grldr error when trying to boot from the cd.

any help?

---

### Post by VampiricPadraig on 2010-05-13
I also cannot get this working. This is a serious problem. Even doing anything wont allow me to use Ubuntu. PLEASE HELP!!!

---

### Post by wackenedgar on 2010-07-27
Hello i get the same error message. When i try copy the grldr file to the c drive i get a windows message Error 0x80070522: A required privilege is not held by the client

I am loggeed in as administrator and it is windows 7 ultimate.

´Thanks for the help.

---

### Post by xnsine on 2010-11-24
I'm getting that same 3 year old GRLDR not found error.  Back in 2007 they suggested going to fat freaking 16!! And they still havent checked this error?  Is wubi tested at all? Or was it dropped a long time ago? The ubuntu team should just quit adding this borked, broken piece of crap worthless program. Why keep it around when it's been out of service for years now?   Why not just say, if you want ubuntu, dual boot? I wanted to try it, but now, I'll stay with windows.  I'm not partitioning and dual booting.

---

### Post by xnsine on 2010-11-24
bump for first result.

---

