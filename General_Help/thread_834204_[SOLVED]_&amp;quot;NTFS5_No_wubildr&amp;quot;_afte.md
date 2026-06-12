---
title: "[SOLVED] &amp;quot;NTFS5: No wubildr&amp;quot; after re-install"
date: 2008-06-19
forum: General Help
---

### Post by michaelomichael on 2008-06-19
Hi there, I really need some help with this because I had wubi running perfectly for a few weeks and loved it, and I really don't want to go back to XP!

After running the Wubi 8.04 installer in Windows, I reboot and choose "Ubuntu" from the boot menu, then I get this:

----------
Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: Cannot find GRLDR in all devices.  Press Ctrl+Alt+Del to restart.
----------

I have a compaq/hp laptop with a single hard drive, and I had previously installed Wubi 8.04.  Then I did something stupid with the /usr directory and had to uninstall!  When I reinstalled all my problems began :(

I've defragged my hard drive a bunch of times, tried using jkdefrag to defrag the C:\wubildr* files and the C:\ubuntu directory, and everything inbetween.  

I also got a copy of "grldr" from somewhere and added an entry to boot.ini to run that instead (this worked a little, but I guess it's an older version of the loader since I had to remove some of the "--ignore-floppies" switches from commands; even when I got through to the final ubuntu install screens it restarted and refused to load the kernel)

I've uninstalled and re-installed a bunch of times, and tried newer versions of the wubi installer (wubi-8.04.1-rev502 and 503) but they're the same.

I've also run chkdsk (/r, /f, both) a few times, with varying results.  Sometimes it tells me that I have "8kb in bad sectors", and sometimes it just hangs on "...verifying file data (stage 4 of 5)... 0 percent completed."

I suspect that there's a small part of my HD that's damaged and it's affecting wubildr, but I don't know how to fix it.

I trawled through dozens of other threads that look similar, but the issues seem to be different from mine, and the fixes don't work.

Can anyone please please help?  (please)

---

### Post by michaelomichael on 2008-06-19
Not wishing to obscure the post, but most similar posts ask the author to submit some fstest.exe results at some point, so here goes:


[SIZE="1"]C:\>Downloads\fstest.exe info C:\
version: 1.0 build 3
part_base: 0x3F (0M)
part_leng: 0x6FC3D80 (57223M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x50

C:\>Downloads\fstest.exe list C:\
0000022E             0  [Documents and Settings]
000184B4        713913  printttest1.ps
0000F71C           244  SQ2FA4~1.SQM
000291EF           244  sqmnoopt00.sqm
0000E10C             0  [src]
0002E551             0  [571077a3fc49a4183d7c25edc92ecf60]
0002E551             0  [571077~1]
0002A0A2           956  aa.xml
000079E8             0  [audio]
000295CF         11978  avi_log.txt
000006E7       9201946  back_up.reg
000001DB           406  boot.ini
000269C4          5276  build.xml
00007AE8           236  Copy of boot.ini
00007AE8           236  COPYOF~1.INI
0002E55A             2  Department_localprompt_5.xml
0002E55A             2  DEPART~1.XML
00006E6A          8575  dlcf.log
0000022E             0  [DOCUME~1]
00009BC1             0  [dotnet]
0000A048             0  [Downloads]
0000A048             0  [DOWNLO~1]
000160FD          7508  google.wsdl.xml
000160FD          7508  GOOGLE~1.XML
000001D1        149000  grldr
000001E0        149000  grldr.original
000001E0        149000  GRLDR~1.ORI
0000023E             0  [grub4dos-test]
0000023E             0  [GRUB4D~1]
0000071C        135781  gsldr
000001DF     501731328  hiberfil.sys
00003B8E             0  [I386]
000389B2           822  icon.bmp
000389F9             0  [InstantRails]
000389F9             0  [INSTAN~1]
00005A45             0  [Intel]
0000C268             0  IO.SYS
000100DE             0  [java]
00034838           822  mask.bmp
000001CD           763  menu.lst
000091D6           782  menu.lst.old
000091D6           782  MENULS~1.OLD
0000C267             0  MSDOS.SYS
00001F9D         47564  ntdetect.com
00001F9E        250032  ntldr
0000CC38     752492544  pagefile.sys
0002932A         46668  Person_localprompt_1.xml
0002932A         46668  PERSON~1.XML
000184B4        713913  PRINTT~1.PS
00000018             0  [Program Files]
00000018             0  [PROGRA~1]
00016C62             0  [Psfonts]
00008F2E          6878  PWlang.log
00019454             0  [rails]
00001F9F             0  [RECYCLER]
0000FDA6           203  Shortcut (2) to CD Drive.lnk
00037D73           203  Shortcut (3) to CD Drive.lnk
00009F2C           145  Shortcut to CD Drive.lnk
00028D3E           302  shortcuts.dat
00028D3E           302  SHORTC~1.DAT
00009F2C           145  SHORTC~1.LNK
0000FDA6           203  SHORTC~2.LNK
00037D73           203  SHORTC~3.LNK
0000F911           244  SQ13B0~1.SQM
0000B61A           244  SQ13B4~1.SQM
0000B5AE           244  SQ13B8~1.SQM
00014CC1           244  SQ13BC~1.SQM
000089C9           244  SQ23B8~1.SQM
000069D5           244  SQ2FA0~1.SQM
0003A69E           244  sqmnoopt01.sqm
0000B6B5           244  sqmnoopt02.sqm
0000B6D3           244  sqmnoopt03.sqm
0000B727           244  sqmnoopt04.sqm
0000CD5C           244  sqmnoopt05.sqm
000069D5           244  sqmnoopt06.sqm
0000F71C           244  sqmnoopt07.sqm
00008F09           244  sqmnoopt08.sqm
00003A97           244  sqmnoopt09.sqm
0000B5AE           244  sqmnoopt10.sqm
00014CC1           244  sqmnoopt11.sqm
0000F911           244  sqmnoopt12.sqm
0000B61A           244  sqmnoopt13.sqm
000089C9           244  sqmnoopt14.sqm
000291EF           244  SQMNOO~1.SQM
0003A69E           244  SQMNOO~2.SQM
0000B6B5           244  SQMNOO~3.SQM
0000B6D3           244  SQMNOO~4.SQM
0000B727           244  SQ2FA8~1.SQM
0000CD5C           244  SQ2FAC~1.SQM
00008F09           244  SQ3FA8~1.SQM
00003A97           244  SQ3FAC~1.SQM
0000B9C4           232  SQA368~1.SQM
00008C54           232  SQA378~1.SQM
0000B72F           232  SQA37A~1.SQM
00014C91           232  SQA38A~1.SQM
00014CE7           232  SQA768~1.SQM
0000D2C7           232  SQA77A~1.SQM
0000BAA0           232  SQA78A~1.SQM
000155BE           232  SQAB68~1.SQM
0000FFF5           232  SQAB7A~1.SQM
00015192           232  SQAF68~1.SQM
00010051           232  SQAF7A~1.SQM
0002A35D           232  sqmdata00.sqm
00043DDF           232  sqmdata01.sqm
0000B6B6           232  sqmdata02.sqm
0000B6D4           232  sqmdata03.sqm
0000B72F           232  sqmdata04.sqm
0000D2C7           232  sqmdata05.sqm
0000FFF5           232  sqmdata06.sqm
00010051           232  sqmdata07.sqm
00014C91           232  sqmdata08.sqm
0000BAA0           232  sqmdata09.sqm
0000B9C4           232  sqmdata10.sqm
00014CE7           232  sqmdata11.sqm
000155BE           232  sqmdata12.sqm
00015192           232  sqmdata13.sqm
00008C54           232  sqmdata14.sqm
0002A35D           232  SQMDAT~1.SQM
00043DDF           232  SQMDAT~2.SQM
0000B6B6           232  SQMDAT~3.SQM
0000B6D4           232  SQMDAT~4.SQM
000479A1           822  ss.bmp
000059BC             0  [System Volume Information]
00001D30             0  [system.sav]
000059BC             0  [SYSTEM~1]
00007191        917672  TB.log
00026128             0  [Temp]
00008D2A             0  test
000294CF             2  test.txt
0002A0AA           901  test.xml
000007FD             0  [ubuntu]
00008D2C     840028160  ubuntuhome.tar
00008D30      70328320  ubuntushare.tar
00002109             0  [WINDOWS]
0000760F       1091085  Wubi-8.04.exe
0000760F       1091085  WUBI-8~1.EXE
0000929E             0  [wubi-installer]
0000929E             0  [WUBI-I~1]
000008E6        188547  wubildr
000008E7          8192  wubildr.mbr
000001D7        186043  wubildr.original
000001D7        186043  WUBILD~1.ORI
0000FEAC             0  [XEDIT]

C:\>Downloads\fstest.exe inode C:\wubildr
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=80)
    wubildr
  $DATA (0x80) (nr,sz=188547)
    31444432+376

C:\>Downloads\fstest.exe comp C:\wubildr
File size : 188547
Comparing
Succeed

C:\>Downloads\fstest.exe inode C:\$MFT
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (r,sz=224)
  $DATA (0x80) (nr,sz=312999936)
    80+322168,98530232+204496
Attr List:
  $STANDARD_INFORMATION (0x10) (r,mft=0x0,sz=72)
  $FILENAME (0x30) (r,mft=0x10,sz=74)
    $MFT
  $DATA (0x80) (nr,mft=0x0,vcn=0x0,sz=312999936)
  $DATA (0x80) (nr,mft=0xF,vcn=0x10129,sz=312999936)
  $DATA (0x80) (nr,mft=0x11,vcn=0x10B55,sz=312999936)
  $DATA (0x80) (nr,mft=0x12,vcn=0x116C4,sz=312999936)
  $BITMAP (0xB0) (nr,mft=0x10,vcn=0x0,sz=38208)

C:\>Downloads\fstest.exe inode C:\
ntfs_dir: 17
[/SIZE]

---

### Post by tinybit on 2008-06-19
Before Bean123 comes in and reply, I would like to reply in a way.
> 
I also got a copy of "grldr" from somewhere and added an entry to boot.ini to run that instead (this worked a little, but I guess it's an older version of the loader since I had to remove some of the "--ignore-floppies" switches from commands; even when I got through to the final ubuntu install screens it restarted and refused to load the kernel)


If grldr works(I mean, it can boot to the "grub" prompt), you may copy your menu.lst to the same directory as grldr and try booting again.

Also try the latest "test" build:

[http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-06-18-gate-a20-test-only.zip](http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-06-18-gate-a20-test-only.zip)

You only need to extract grldr from the ZIP ball.

---

### Post by bean123 on 2008-06-20
The fstest result is normal, but I notice that $MFT uses non resident attribute list, which could cause problem. Perhaps you can defrag the drive and try again.

BTW, you can also use vista boot loader + grub2.

---

### Post by michaelomichael on 2008-06-22
Thanks for the response folks.  

Tinybit, I originally had a bit of success copying the menu.lst into C:\ (it eventually completed the non-windows part of the install, but wouldn't get past grub again once I rebooted; subsequent attempts to re-create this with re-installs didn't work at all.  I'll give the new version of grub a shot though, and let you know how it goes.

Bean123, I'll try another defrag (I think I can do "JKDefragCmd C:\$MFT" to concentrate it on that particular file/dir?).  I'll look into the vista bootloader too.

Do you think this is caused by an issue in the bootloader or is it just a disk error?

Thanks again

---

### Post by bean123 on 2008-06-23
> **michaelomichael said:**
> Thanks for the response folks.  

Tinybit, I originally had a bit of success copying the menu.lst into C:\ (it eventually completed the non-windows part of the install, but wouldn't get past grub again once I rebooted; subsequent attempts to re-create this with re-installs didn't work at all.  I'll give the new version of grub a shot though, and let you know how it goes.

Bean123, I'll try another defrag (I think I can do "JKDefragCmd C:\$MFT" to concentrate it on that particular file/dir?).  I'll look into the vista bootloader too.

Do you think this is caused by an issue in the bootloader or is it just a disk error?

Thanks again

It's caused by the boot loader. The intermediate loader grldr.mbr is quite limited in size (2048 bytes for ntfs access), there is some corner case that it can't handle properly.

The trick about vista loader is that it support a larger boot file, up to 64K. This means we can load the real loader, instead of relying on grldr.mbr. But grub4dos is too large to fit within 64K, grub2 is ok.

---

### Post by michaelomichael on 2008-06-25
Hi, I think you were onto something when you said that C:\$MFT was too fragmented.  

My regular defrags (both the windows one, and JKDefrag) couldn't fix this, so I downloaded the 
[trial version of Diskeeper 2008 Home]("http://consumer.diskeeper.com/downloads/Downloads.aspx") and set it to run a manual defrag of the MFT section on the next reboot.

After that I just rebooted, uninstalled and re-installed Wubi, and it now seems to be working fine!  :)

Thanks to both of you for your suggestions and insight, there's no way I'd have figured that out on my own.

Can I make a suggestion that the "fstest" check is built into the wubi installer so it could check for this sort of scenario straight away?  The installer could then offer the user the choice of continuing or scheduling a defrag on the next reboot.  What do you think?

Thanks again!!

---

### Post by ago on 2008-06-25
> **michaelomichael said:**
> 
Can I make a suggestion that the "fstest" check is built into the wubi installer so it could check for this sort of scenario straight away?  The installer could then offer the user the choice of continuing or scheduling a defrag on the next reboot.  What do you think?



Sounds like a good idea, please open a bug in Launchpad to remind me

[https://launchpad.net/wubi](https://launchpad.net/wubi)

---

