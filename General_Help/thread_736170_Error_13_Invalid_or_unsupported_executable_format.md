---
title: "Error 13: Invalid or unsupported executable format"
date: 2008-03-26
forum: General Help
---

### Post by uLtiMaTeNuB on 2008-03-26
This is my first time installing ubuntu (or any linux on that matter) and I decided to use Wubi since I wanted to test out Ubuntu without overriding my windows installation. 

Anyhow, I'm completely new at this stuff :confused: and here's the problem:

[IMG]http://i25.tinypic.com/w229zp.jpg[/IMG]

After I booted up ubuntu for the first time I got that error. All of the ubuntu boot options would lead me to the same error and the only thing I can access is the command line (the only thing I know how to do there is type reboot..). 

For anyone that can't see the error in the pic:

> kernel /ubuntu/install/boot/vmlinuz boot=casper debian-installer/custom-install
ation=/ubuntu/install/custom-installation iso-scan/filename=/unbuntu/install/har
dy-desktop-i386.iso quiet splash ro automatic-ubiquity locale=en_US.UTF-8 nopro
mpt --

Error 13: Invalid or unsupported executable format

Press any key to continue...

Thank you in advanced for anyone that helps.

---

### Post by ago on 2008-03-26
This is after the first install, just after running the windows section correct?

Can you pls make sure that kernel and initrd in c:\ubuntu\install\boot are not fragmented?

You can use [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/) for that

Also can you use tab completion in the grub console to navigate to the kernel files?

kernel (hd0,0)/ubuntu/install/boot/vmlinuz

replace 0,0 as appropriate, first number is the disk -1, second number the partition -1

---

### Post by uLtiMaTeNuB on 2008-03-26
Alright, I'll give that a try.

---

### Post by uLtiMaTeNuB on 2008-03-26
Okay, I defragmented the files and I'm still getting the same problem. As I said before, I'm a complete noob at this lol. I don't understand the tab completion part. 

If you can give me a series of commands to run, I could do it.

Thank you again and sorry for the trouble :(.

---

### Post by ago on 2008-03-26
Is your drive compressed by any chance?

As for tab competion, press esc at the countdown after boot, then at the menu press "c"

Type the path above and press the TAB  key once in while to see the available options.

root (hd[TAB]

will now list the available disks

root (hd0,
root (hd1,

root (hd1,[TAB]

will list available partitions and so on
See if you can reach the vmlinuz file

---

### Post by uLtiMaTeNuB on 2008-03-26
My hard drive only has one partition.

root only brings up (hd0,0) with tab completion and I can't go further than that.
(hd1,[TAB] doesn't exist. 

I booted up windows and checked if the drive was compressed and it wasn't. The file system is NTFS if that has any effect..

---

### Post by ago on 2008-03-26
What version of Wubi did you use? You should try rev 457 off the wubi-installer.org website

---

### Post by uLtiMaTeNuB on 2008-03-26
I used... Wubi 8.04 beta rev457. Oh well, I guess my problem isn't going to solve itself today. I'm going to redownload it again since it might have gone corrupt.

Thanks for the help, I'm going to go take a break while it downloads.

---

### Post by ago on 2008-03-26
Can you try to replace C:\wubildr with the grldr file within the following archive? Also copy c:\ubuntu\winboot\menu.lst to c:\

[http://ubuntuforums.org/attachment.php?attachmentid=62477&d=1205423881](http://ubuntuforums.org/attachment.php?attachmentid=62477&d=1205423881)

---

### Post by uLtiMaTeNuB on 2008-03-26
I'm sorry, I went afk before but I completely redownloaded ubuntu and it appears to be booting up.

---

### Post by htoke on 2008-03-27
I am seeing the same error. Used the JkDefrag, but that did not help. Also grub is able to correctly locate the file as well as read the NTFS file system. I can see the listing for the parent directory correctly from grub (using tab). 
Here is my config is:
IBM lenovo x61s laptop, 1 GB RAM, 80 GB hard disk. currently running windows XP SP2
wubi-804-rev431.

Not sure where the problem is.

---

### Post by ago on 2008-03-27
Can you try to uninstall and redownload everything?

It would help if you could compare the md5 of c:\ubuntu\install\boot\vmlinuz with \casper\vmlinuz within the CD/ISO

---

### Post by htoke on 2008-03-27
Sorry will not be able to check the MD5 as I removed the earlier installation and now restarted the entire download with wub-8.04-rev455.
Lets hope this works.

---

### Post by daberger on 2008-03-27
im getting the same problem so i guess ill try redownloading but im sad bcuz i have slow internet and it takes 14 hours to download

---

### Post by htoke on 2008-03-29
Things finally worked for me, so posting this from Firefox running on kubuntu-kde4 :) .  Used wubi8.04_rev455, but downloaded the ISO image for 8.04 separately (I was not sure if wubi would support the kde4 remix, but turns out it does). Once the CD was downloaded, then install went through fine and I was able to get the whole up and running in under an hour.

---

### Post by ago on 2008-03-29
This seem to be a randomly occurring error.

Repeating the installation (even without redownloading the ISO) might fix things

I cannot reproduce it myself. It would help a lot if people that experience that could post the md5 of C:\ubuntu\install\boot\vmlinuz and the one within the ISO f:/casper/vmlinuz or run from the grub console

cat --hex --skip=0x1F0 --length=80 (hd0,0)\ubuntu\install\boot\vmlinuz

replacing 0,0 as appropriate (first number is the disk number -1, second number is the partition number -1)

---

### Post by bean123 on 2008-03-30
This bug is quite tricky, if someone has similar problem, please don't reinstall yet, otherwise we can't figure out the real cause.

---

### Post by MolsonH on 2008-03-30
Hi, I'm also getting the same error. I'm a real newb
I uploaded the md5 files
[http://cid-dfffe7bdd196d5b7.skydrive.live.com/browse.aspx/Ubuntu](http://cid-dfffe7bdd196d5b7.skydrive.live.com/browse.aspx/Ubuntu)
I'm going to try to reinstall again, it didn't work the first time. 
I had to use Wubi because when I booted with the CD it wouldn't recognise my SATA drive. I did a bit of googling and it seems the chipset I have (Intel P35) you can't install having an IDE DVD/CD rom with a SATA HD. I just wonder if this would have anything to do with it. As I have a SATA and IDE HD, with 5 partitions in all. I tried to browse them on the console booting ubunto but I just don't know anything about Linux I can't seem to get to it, when pressing tab it seems all partitions I go on I have the same files?

---

### Post by MolsonH on 2008-03-30
Well I tried to redownload, and it worked in a sence that i'm not getting Error 13 anymore but i'm getting a busybox console windows now, and when I look at the log I get this error
stdin: error 0
/init: /init: 1: cannot open /dev/scd0: no medium found
not sure if the 2 are related in any way

---

### Post by ago on 2008-03-30
> **MolsonH said:**
> Hi, I'm also getting the same error. I'm a real newb
I uploaded the md5 files
[http://cid-dfffe7bdd196d5b7.skydrive.live.com/browse.aspx/Ubuntu](http://cid-dfffe7bdd196d5b7.skydrive.live.com/browse.aspx/Ubuntu)


The 2 kernels are identical. Bean123 any hint?

---

### Post by ago on 2008-03-30
> **MolsonH said:**
> Well I tried to redownload, and it worked in a sence that i'm not getting Error 13 anymore but i'm getting a busybox console windows now, and when I look at the log I get this error
stdin: error 0
/init: /init: 1: cannot open /dev/scd0: no medium found
not sure if the 2 are related in any way

Is that after the first (after windows) or the second (after linux installation) reboot?
If it is after the first reboot see if there is any relevant mounting error in /casper.log within the busybox (other than no medium found).

---

### Post by MolsonH on 2008-03-30
This is after the first reboot, the windows reboot. I can't get into ubuntu unless i put the live CD in. and with the live CD I can't get it to recognise my SATA HD.
I think there are some mounting errors, is there a way i can open that log in windows so i can copy/paste it here?

---

### Post by ago on 2008-03-30
Mount the windows partition with something like

mount -t ntfs /dev/sda1 /mnt

#sda1 (a = disk1, 1 = partition 1) change as appropriate 

Then copy over any relevant file

cp /casper.log /mnt

That will appear under c:\ in windows

---

### Post by bean123 on 2008-03-31
> **ago said:**
> The 2 kernels are identical. Bean123 any hint?

I think it could be caused by some well hidden bug in ntfs driver. However, he already reinstall and the problem disappear, there is no way to verify it until the next bug report.

---

### Post by ago on 2008-03-31
So please, if you have this bug, do us a favor, post something here WITHOUT trying to fix it (by reinstalling). So that we can give you instructions to help us pin it down. It is not something we can replicate so we need to rely on your help.

Thanks,

Ago

---

### Post by chrominance on 2008-04-02
(er, never mind, Firefox screwed up my ISO, that's probably responsible for my troubles. sorry I couldn't help!)

---

### Post by RangerSK on 2008-04-05
hi, i got error 13, pls help me:confused:

---

### Post by RangerSK on 2008-04-05
I tried reinstall without download iso, first with same installer, second with latest wubi installer, but everytime I got error 13

---

### Post by webhostbudd on 2008-04-05
yea, im getting the same thing. It's really strange. Ive tried redownloading the iso's multiple times and trying different ones. It just won't work for me with the latest revision 479.

---

### Post by ago on 2008-04-05
Can you upload c:\ubuntu\install\boot\vmlinuz?

---

### Post by RangerSK on 2008-04-06
my vmlinuz:
[http://rapidshare.com/files/105334430/vmlinuz.html](http://rapidshare.com/files/105334430/vmlinuz.html)

---

### Post by bean123 on 2008-04-08
You can use fstest.exe to run some tests, download address:

[http://grub4dos.sourceforge.net/grub4dos/fstest.exe](http://grub4dos.sourceforge.net/grub4dos/fstest.exe)

fstest info C:
fstest inode C:\ubuntu\install\boot\vmlinuz
fstest comp C:\ubuntu\install\boot\vmlinuz
fstest dump C:\ubuntu\install\boot\vmlinuz 0 1024

---

### Post by RangerSK on 2008-04-08
fstest info C:
version: 1.0 build 2
part_base 0x3F (0M)
part_leng 0x30D3C74 (24999M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x60000

fstest info D:
version: 1.0 build 2
part_base 0x30D3CF2 (24999M)
part_leng 0xAEBBC0E (89463M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x60000

fstest inode D:\ubuntu\install\boot\vmlinuz
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=80)
    vmlinuz
  $DATA (0x80) (nr,sz=1887480)
    136546720+256,135232320+520,57019440+1024,55860736+1888

fstest comp D:\ubuntu\install\boot\vmlinuz
File size : 1887480
Comparing .
Succeed

fstest dump D:\ubuntu\install\boot\vmlinuz 0 1024
00000000: CE 43 49 44  64 1A 0B DE  0A E2 E4 92  98 84 B4 44 ; .CIDd..........D
00000010: 97 90 EA F3  EC A6 7A 0A  E1 C6 96 33  DD 36 82 10 ; ......z....3.6..
00000020: A5 2E 28 B9  C1 5E CD 4E  1B EB F3 40  C4 EC 11 B5 ; ..(..^.N...@....
00000030: 48 2E C3 DE  A7 50 86 E8  75 0A 56 EA  50 01 6D 83 ; H....P..u.V.P.m.
00000040: AC 19 64 9A  2D 32 43 93  64 67 F2 60  67 48 9A 76 ; ..d.-2C.dg.`gH.v
00000050: 1F 88 98 79  19 B2 F4 0D  79 84 0B 16  20 60 26 7E ; ...y....y... `&~
00000060: 8B D4 60 2B  2F 58 D0 A3  58 DD DC 1A  24 41 65 53 ; ..`+/X..X...$AeS
00000070: A3 1E A8 C2  20 1A 04 39  59 90 6F 05  25 EE D7 DA ; .... ..9Y.o.%...
00000080: FA 38 DB AA  2C 21 5D 4D  62 7A 1B 6A  6C A3 E8 8C ; .8..,!]Mbz.jl...
00000090: 4C C7 3D CA  26 E7 20 4D  73 F5 4F 3B  D1 1E 95 50 ; L.=.&. Ms.O;...P
000000A0: 69 8A 65 F9  5F BA 2F 33  8D 89 3E 82  87 1C 71 BF ; i.e._./3..>...q.
000000B0: C0 5D F7 A2  30 B2 8E E9  13 3D 7C 03  8F DF 42 A8 ; .]..0....=|...B.
000000C0: 44 14 78 55  97 A8 8C 44  6A 68 B3 9E  DA C5 D4 1B ; D.xU...Djh......
000000D0: 9C 8B EA E1  FD 38 53 96  6B 26 38 DF  1D 38 17 F0 ; .....8S.k&8..8..
000000E0: FB C5 49 81  EA 85 45 25  5B 3E A4 AD  75 0A AC 53 ; ..I...E%[>..u..S
000000F0: EF A3 F9 96  28 23 37 E2  06 B9 A7 45  EA 78 94 9B ; ....(#7....E.x..
00000100: D0 C8 6A 04  1A 4E D2 07  B3 A0 2F 9A  12 EA 64 AC ; ..j..N..../...d.
00000110: D5 AA 74 47  D8 00 75 AA  97 3E 64 E9  25 58 12 AC ; ..tG..u..>d.%X..
00000120: 24 EC B7 31  F2 22 57 B9  FC 7D B2 13  D7 E6 24 75 ; $..1."W..}....$u
00000130: 4E 19 61 78  B4 7F 30 CF  58 2E B1 73  89 EF C5 8F ; N.ax..0.X..s....
00000140: 28 61 4F ED  69 29 ED C0  9F 7A 4A 28  C3 83 CA 8C ; (aO.i)...zJ(....
00000150: E3 E1 7A 83  AF 30 05 7A  3A 4B AA 45  1F 06 6C C1 ; ..z..0.z:K.E..l.
00000160: CC 2B F2 85  38 18 D3 F2  52 D0 5C C3  55 E6 D9 D7 ; .+..8...R.\.U...
00000170: 98 7C 0E 58  BA 36 32 4C  EE FC 92 83  D1 8D 27 C9 ; .|.X.62L......'.
00000180: 7E 75 AE FD  1D DA 35 93  E5 EF AD B1  F9 EC 18 62 ; ~u....5........b
00000190: E2 BB 15 BD  04 D2 0E 1B  3A 0A 16 95  E7 D9 DB 08 ; ........:.......
000001A0: 8A D2 E8 4B  96 0E 5E 5F  7E 03 BA B8  FF 73 CF 08 ; ...K..^_~....s..
000001B0: CD EE 4B 2A  8A AE 42 F7  55 7E F8 F2  06 90 47 7A ; ..K*..B.U~....Gz
000001C0: 99 4F B2 8D  E2 CA 58 50  D2 EC 67 31  1D 61 3B 19 ; .O....XP..g1.a;.
000001D0: E8 27 A2 60  80 1E 29 5E  82 92 8C C4  46 A2 0C 89 ; .'.`..)^....F...
000001E0: 19 2B 34 DB  05 63 90 C4  50 41 9A 23  FF 32 D0 1C ; .+4..c..PA.#.2..
000001F0: E1 CB DD 0B  78 E6 38 F5  B0 10 69 6D  96 F0 12 D2 ; ....x.8...im....
00000200: 01 4C 94 FF  64 D5 E2 15  3D A0 30 78  E5 62 14 08 ; .L..d...=.0x.b..
00000210: BD 32 71 41  26 18 3F 16  DD F5 5F 18  3D BC 72 44 ; .2qA&.?..._.=.rD
00000220: B3 7B FC 6C  19 42 D8 31  1F 87 E6 9E  99 9A AD DB ; .{.l.B.1........
00000230: E0 02 71 C8  13 02 51 A7  98 36 F8 E4  D7 E7 76 46 ; ..q...Q..6....vF
00000240: 23 AB 7A FA  AB 32 09 AB  5B 4B EB E8  D5 F3 71 34 ; #.z..2..[K....q4
00000250: 64 D6 F3 8D  AC E7 91 EC  5C 1D 5C 13  D7 E7 41 CE ; d.......\.\...A.
00000260: 12 73 D1 66  54 22 D8 8D  52 6E BA 51  22 63 A8 91 ; .s.fT"..Rn.Q"c..
00000270: 04 D9 E3 BD  BA 88 01 D6  C4 FA E9 CC  A1 68 54 75 ; .............hTu
00000280: FD C7 6C 78  B7 D1 D0 63  39 A5 F4 81  B5 AB 74 C5 ; ..lx...c9.....t.
00000290: 5C FC FC A7  94 72 D0 C8  07 FF 9F 35  72 AA B8 CC ; \....r.....5r...
000002A0: D3 22 89 06  15 FC D9 56  B0 C0 E6 9B  C9 16 AB 92 ; .".....V........
000002B0: 9B 30 78 33  71 31 D4 1C  4D A8 9F C2  2C F9 B9 20 ; .0x3q1..M...,.. 
000002C0: 17 40 6B 8D  F1 C8 22 F2  2B B0 F6 11  2F D1 D6 41 ; .@k...".+.../..A
000002D0: D6 95 4B E2  0E B4 F0 67  E4 59 DC 80  B7 45 3E 27 ; ..K....g.Y...E>'
000002E0: CE EF C4 FF  94 32 01 4D  3C 43 47 4F  22 94 6C 5B ; .....2.M<CGO".l[
000002F0: A0 CD 97 02  52 69 A3 1E  EF 0E 72 E9  E3 D5 81 36 ; ....Ri....r....6
00000300: F1 A8 BF 7A  23 0E 55 50  9A E0 62 42  FF 86 6A 9A ; ...z#.UP..bB..j.
00000310: FF 90 07 22  45 6D F3 4C  FC 53 3F A6  28 AF 24 FC ; ..."Em.L.S?.(.$.
00000320: C4 D1 EE A8  9E 8F 4F 2F  D8 7C 1F C3  A8 07 39 D9 ; ......O/.|....9.
00000330: 55 2B 97 E1  1E 1B 5D 9E  61 62 F3 44  ED EC 46 E3 ; U+....].ab.D..F.
00000340: FB 03 93 FA  70 D4 62 D5  8D 5A 3E EE  54 66 58 61 ; ....p.b..Z>.TfXa
00000350: B2 7A 52 F7  9F 31 99 01  B3 BC 94 A1  BF FE 6B A6 ; .zR..1........k.
00000360: 61 FC 8C 23  28 C3 61 6A  02 EE 8C 88  7F A0 AC C3 ; a..#(.aj........
00000370: F7 07 2D 17  C2 09 77 63  CE D0 C8 CD  23 0C 8B 7E ; ..-...wc....#..~
00000380: 56 BA 05 DB  89 0C 4B 4B  9F 24 98 F0  D3 7F 41 FA ; V.....KK.$....A.
00000390: C7 F9 70 95  5B 8A E1 37  EA E2 0D 8C  36 A6 82 45 ; ..p.[..7....6..E
000003A0: 2A 2E C7 57  49 F8 AA F1  88 A4 B7 F0  22 50 D0 18 ; *..WI......."P..
000003B0: 78 D4 2C 3D  3B DE F7 C7  A2 8A D8 E4  3F 75 54 CB ; x.,=;.......?uT.
000003C0: 47 63 1F F7  78 61 1F 1F  A7 1A 35 AB  C9 46 C6 84 ; Gc..xa....5..F..
000003D0: 5D 67 6C 0A  0B 24 8C 69  F9 06 DB AC  48 79 18 EB ; ]gl..$.i....Hy..
000003E0: 8F A3 E2 BF  23 4F C1 32  58 C4 02 55  C6 3D 72 30 ; ....#O.2X..U.=r0
000003F0: 1A BE 33 7E  3F 57 79 B3  69 63 89 45  C3 88 77 40 ; ..3~?Wy.ic.E..w@

__________________

---

### Post by bean123 on 2008-04-08
This doesn't seem like a linux kernel, perhaps your download is corrupted.

ago, perhaps you can add some verification to the files, so that user will know when they corrupts.

---

### Post by ago on 2008-04-08
RangerSK can you pls mount the ISO file and check that the file

/casper/vmlinuz

within the ISO has the same md5 as C:\ubuntu\install\boot\vmlinux? 

And could you check that the md5 matches the one mentioned in md5sum.txt within the CD?

Either the ISO is corrupted (which should be caught once we turn on md5 checks on the ISO) or 7z messes up the extraction of the kernel for the ISO (I might add some checks there) or the file gets somehow overwritten later on. Checking the md5 vs the one in md5sum.txt should be enough to nail it...

---

### Post by RangerSK on 2008-04-09
How can I check it?

---

### Post by ago on 2008-04-09
Hi, there are several tools available to calculate the md5, anyone will do. An md5sum is an algorithm that associate a unique number to a file. When such numbers match, it means that the files are bit-identical.

To mount the ISO in order to access the files therein you will need daemon tools or similar.

Basically you have to calculate the md5 for the vmlinuz file on your HD and the one on the HD, and also crosscheck with the appropriate md5 mentioned in md5sums.txt within the CD. That will tell me if the file was corrupted within the ISO or during the extraction process.

---

### Post by Caz666 on 2008-04-10
I stumbled upon this topic today while tring to use Wubi on my media center box. I am running Vista Ultimate and getting REALLY fed up. 
I am still a newb to the Linux world but know my way around computers...

I got the Error 13 Message. Before my luck again with a re-download/re-install, I thought I would contribute a bit.

I hope the following helps a bit:

> can you pls mount the ISO file and check that the file

/casper/vmlinuz

within the ISO has the same md5 as C:\ubuntu\install\boot\vmlinux? 

My MD5 sums match up. While I was at it, I made sure that my orginal ISO file had the same MD5 hash as the only that was copied to the 
\ubuntu\install folder. They are fine. I gets more intersting below...


> And could you check that the md5 matches the one mentioned in md5sum.txt within the CD?

The vmlinuz files do NOT match the MD5 sums of the md5sum.txt.

Thinking that this was weird, I checked the md5 of the ISO itself with the one inside the MD5SUMS file on the mirrors and it does not match...

Bad download?

Caz666

---

### Post by RangerSK on 2008-04-10
checksum vmlinuz on HDD is same as on iso, but different as in md5sum.txt

---

### Post by ago on 2008-04-10
Then the ISO is corrupt.
I will add an md5 check for ISO and initrd

---

### Post by andrewstas on 2009-04-04
Hello there!!!
I am a 100% newbie and I would be very glad to join the ubuntu family!
I am quite experienced in WindowsXP but I have no idea from the linux stuff (terminals, commands, ... etc).

I have exact the same problem as it is described in the 1st post.
Yesterday, I tried to instal ubuntu v8.10 with the help of wubi. Everything seemed to be ok but upon restarting for the first time, this Error13 came up :(

I have installed the ubuntu on the 2nd partition of my hard drive [Z:] since C: didn't have a lot of room. Is this a problem?

My desktop computer is quite old but it does the things I want. Its CPU is the "AMD-K6 3D" at 450MHz and on the motherboard I have 3 SDRAM modules in order to have 320MB RAM (384MB is the maximum that is supported by the motherboard). It runs WindowsXP SP3 on a NTFS 200GB IDE hard disk which is partinioned in 40GB [C:] and 160GB [Z:].

From the options of wubi, I gave 10GB space in Z: for the ubuntu.

Trying to resolve the issue, I did the following things:
**1.** I defragmented the whole folder: Z:\ubuntu\install\ with JkDefrag as it is proposed on post #2. It didn't help.
**2.** Using the winMD5sum software, I did an md5 check of the file ubuntu-8.10-desktop-i386.iso that I found in Z:\ubuntu\install\. The MD5 check sums were the same upon the compare with md5 hash I found here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

I have uploaded the **vmlinuz** file which is located in Z:\ubuntu\install\boot\
[http://www.divshare.com/download/7010529-1d8](http://www.divshare.com/download/7010529-1d8)
if that helps in some way...
I can find this file from the grub console, if I write:
kernel (hd0,1)\ubuntu\install\boot\vmlinuz

I would appreciate any help!
Thank you in advance!

Andreas

---

### Post by drcreep on 2009-04-11
Hello,

just registered to push this thread up to the top.

I also gave Ubuntu a try with the wubi-installer. Needless to say that I get an error 13! :(

I already checked for corrupted files: Neither the iso nor the kernel is broken! But it won't work! :(

So I just run again into Murphy's Law! ](*,)

Any suggestions?

Thanks,
drcreep

---

### Post by andrewstas on 2009-04-12
I uninstalled ubuntu from Z: and reinstalled it with the wubi-installer to drive C:
It worked!!!!
I was able to complete the installation and boot in Ubuntu **for once**.
I say once because the next day I tried to boot into Ubuntu, for the second time, I wasn't able anymore. :(
The booting was freezing at the screen where the loading bar appears with the Ubuntu logo.
I pressed Alt+Ctrl+Del and a part of the loading bar seemed to fill, but neither it unfroze nor it rebooted. I had to do a hard reset in order to reboot my pc.
Before pressing the Alt+Ctrl+Del combination, I had waited for at least one hour!!!
So, I uninstalled the Ubuntu once more and I gave another try to install it in drive Z:
The same Error 13 appeared.
I am desperate...

Andreas

---

### Post by drcreep on 2009-04-12
Hello,

I got Ubuntu finally running on my system. I just tried the suggested harddrive instead of choosing my own one and then it worked! :mrgreen:
But I don't have really any clue what is making the difference. :-k
Except for that:
First I tried to install it on my primary hdd in the first logical partition. On the primary hdd is also the primary partition for windows! -> Error 13!
Then I installed it to the suggested drive which is on my second hdd. This one only have logical partition! -> It ROCKS! \\:D/

Hope it helps a little bit!

Greetings,
drcreep

---

### Post by andrewstas on 2009-04-13
Hmmm... nice but strange! :p
In my case, I think it happens almost the opposite.

Well, I have two hardrives. On the 1st one I have made 2 partitions, C: and Z:
The second one is dedicated for acronis backups for the windows XP.
In my case, the Error 13 appears when I install Ubuntu on Z:.
If I install Ubuntu on C: (the same partition on which windows XP are installed) the Error 13 doesn't appear.
But then I have the second problem I described in my previous post :(

---

