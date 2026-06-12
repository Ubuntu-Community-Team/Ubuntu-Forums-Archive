---
title: "[SOLVED] How to determine which Linux partition w/ Grub controls the MBR?"
date: 2008-06-22
forum: General Help
---

### Post by caljohnsmith on 2008-06-22
If in addition to Ubuntu I have other linux distros installed in separate partitions on my HD, what is a good way to determine exactly which distro (partition) is controlling the MBR? I know I can figure it out by examining the menu.lst files for all the partitions, but is there some Grub command in the grub CLI that will just tell me what partition controls the MBR?

Thanks for any help.

---

### Post by AndyCee on 2008-06-22
ubuntuforums.org/showthread.php?t=224351

Best grub tutorial ever. I think the command you're looking for is 

```
sudo grub
find /boot/grub/stage1
```

Good luck.

---

### Post by louieb on 2008-06-22
Not anyway I know of to tell which Linux installs GRUB controls
 the MBR. (other that the one you mentioned about checking the menu.lst).

If you have always used the default install then I'd bet the GRUB you get belongs to the last distro you installed.  

Most Linux installers let you put the GRUB stage1 code in the boot sector of its install partition. thats what I do. then I just add a **configfile** or **chainloader** option to my 1st GRUBS menu.lst to boot the other Linux distro. 

Cood stuff here on GRUB [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

Good to know stuff here too [GrubHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GrubHowto#head-1296ce2b184032373f19ad50a91d506eb886ac5f")

---

### Post by meierfra. on 2008-06-22
I don't really recommend this **([SIZE="3"]since "dd" is one of those dangerous commands and you have to be really careful  whenever you use "dd")[/SIZE]**, but this will tell you which linux is in control of the MBR 

```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```

(Here you need to replace /dev/sda by  whatever drive  you are booting from. Also this is a command in a linux terminal, not in the grub command line))

The output will look like this


00000000   ff05
00000002

or

00000000   8205
00000002

In the first case the controlling linux is (hd0,5)  
ff means the controlling linux  is on the boot drive, "ff 0n"  means (hd0,n).

In the second case the controlling linux is (hd2,5)    "8m 0n" means (hdm,n)

---

### Post by louieb on 2008-06-23
> **meierfra. said:**
> I don't really recommend this...

:)Nice. Do you remember where you found this little nugget.?

---

### Post by caljohnsmith on 2008-06-23
> **meierfra. said:**
> 
```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
```

I agree with louieb, where did you find this extremely useful gem of pure Linux voodoo? :) Do you know the translation behind the number for the HD? If "ff" is the first HD, "52" the second, what would be the third or fourth for instance? 

Although I wish grub had some command to simply tell which partition the MBR points to, this command gets the job done. Thanks much for sharing it!

---

### Post by VMC on 2008-06-23
> **louieb said:**
> :)Nice. Do you remember where you found this little nugget.?

Here is a good explanation of how Grub works on the machine level. It describes in detail how Grub works. It displays the hex of the MBR.

So this might be what your looking for:

[http://mirror.href.com/thestarman/asm/mbr/GRUB.htm](http://mirror.href.com/thestarman/asm/mbr/GRUB.htm)

---

### Post by meierfra. on 2008-06-23
> If "ff" is the first HD, "52" the second, what would be the third or fourth for instance? 

It's a little different:  ff means the first drive. In all other cases ,  "xy" means (hdy,x).


> Do you remember where you found this little nugget.? 

Well, just by looking at the first few sectors of the hard drive, I have found out where Grub stores the (hdx,y) variables. Later I noticed  that the[ grub manual (Appendix D.2.) ]("http//www.gnu.org/software/grub/manual/grub.pdf") contains this information.
I don't remember where I learned about "dd" and "hexdump".
The exact code I made up myself to answers the OP's question.

---

### Post by caljohnsmith on 2008-06-23
Thanks for clarifying how the HD numbers are interpreted from the dd command's output, meierfra. 

But here's another important thing I noticed:
On boot-up, if I enter the Grub CLI, if I do the "find /boot/grub/stage1" command, it finds (hd0,1) which I know is the partition that the MBR points to. BUT, if I enter the Grub CLI after I've booted into one of my linux distros (using "sudo grub"), the "find /boot/grub/stage1" command returns both (hd0,1) and (hd0.3). To clarify, I have 4 partitions like such:
```

(hd0,0) = Windows
(hd0,1) = Ubuntu (has Grub installed)
(hd0,2) = Swap space
(hd0,3) = Mandriva (also has Grub installed, but Grub was installed to the boot sector of its partition, not to the MBR)
```
Thus it seems like when I do the "find /boot/grub/stage1" command from the boot-up Grub CLI, I get the partition the MBR points to. But if I go to the Grub CLI from within one of my Linux distros and do the same command, Grub returns ALL my partitions that contain a Grub stage1 file, and not just the partition that the MBR points to. 

Can someone please either confirm or clarify this?

---

### Post by meierfra. on 2008-06-23
> Thus it seems like when I do the "find /boot/grub/stage1" command from the boot-up Grub CLI, I get the partition the MBR points to. But if I go to the Grub CLI from within one of my Linux distros and do the same command, Grub returns ALL my partitions that contain a Grub stage1 file, and not just the partition that the MBR points to.


The Grub CLI should also return all partitions containing the  stage1 file.

I'm not sure why it doesn't. Couple of possible reasons:


1) Your bios are only able to see the first 130GB of your hard drive and the Mandriva stage1 file is beyond the 130 GB limit.

2)  The Mandriva  ext3 filesystem uses  256 bytes inodes and older versions of grub are not able to read such a file system.


But both of these explanations  don't make sense to me, since in either case  you should not be able to boot Mandriva

Although in case 1) you might be able to boot. Maybe only the stage 1 files are out of reach (which wouldn't cause a problem) But stage2, menu.lst and the kernel are in reach. What is the output of


find /boot/grub/menu.lst

and
 
 find /boot/grub/stage2

---

### Post by meierfra. on 2008-06-23
Correction:

In case 2) one is able to boot into Mandriva. ( "chainloader"  works but "configfile" does not.)

Are you using Ubuntu 7.10 or lower ?  (The Ubuntu 8.04 grub can read Mandriva but the others can not)

---

### Post by mempman on 2008-06-23
> **caljohnsmith said:**
> 
Thus it seems like when I do the "find /boot/grub/stage1" command from the boot-up Grub CLI, I get the partition the MBR points to. But if I go to the Grub CLI from within one of my Linux distros and do the same command, Grub returns ALL my partitions that contain a Grub stage1 file, and not just the partition that the MBR points to. 

Can someone please either confirm or clarify this?


find /boot/grub/stage1 command will start at / and search every directory for the file called "stage1."  Another way, although not very clever, to figure out what distro is controlling your boot process would be to modify each of your menu.lst files and put a string beside the kernel line--such as vga=xxx, or somethign, doesn't really matter--then when you boot and are confronted with grub, you can hit 'e' to modify the arguments, and then you will be able to see the little string that you placed and will be able to identify your partition as such.

hope it works out.

---

### Post by caljohnsmith on 2008-06-23
> **meierfra. said:**
> Correction:

In case 2) one is able to boot into Mandriva. ( "chainloader"  works but "configfile" does not.)

Are you using Ubuntu 7.10 or lower ?  (The Ubuntu 8.04 grub can read Mandriva but the others can not)
I started originally with 7.10 and upgraded to 8.04 successfully. My installed grub package is 0.97-29ubuntu21. You are right on the mark in that I cannot load Mandriva with "configfile" notation, but I can with "chainloader" since I have Mandriva's grub installed into its partition boot sector and not the MBR. 

When I search for menu.lst and stage2 in grub's CLI while I'm in either of my two linux distros (accessing the grub CLI with "sudo grub"), it still returns both distros. Yet doing the same thing in Grub's CLI on boot-up still returns just my Ubuntu partition only (hd0,1).

So do I need to upgrade/reconfigure Grub or something?

---

### Post by meierfra. on 2008-06-23
Try reinstalling grub:

at any grub prompt:

```

root (hd0,1)
setup (hd0)
quit
```

---

### Post by caljohnsmith on 2008-06-23
> **meierfra. said:**
> Try reinstalling grub:

at any grub prompt:

```

root (hd0,1)
setup (hd0)
quit
```
I thought this only rewrote the MBR to point to (hd0,1) and does not actually reinstall grub. I tried it anyway and it didn't change anything, so I did a full reinstall of Grub (and of course I first backed up my menu.lst); even though in Synaptic I set the "mark with complete removal" for Grub and then uninstalled Grub, still all the files were left in the /boot/grub/ folder. So I manually deleted them all, and then reinstalled Grub. But even after reinstalling, no files were created in /boot/grub! So I did a "sudo grub-install /dev/sda" and that created all my /boot/grub files except menu.lst, which was fine since I copied back the old one anyway.

Bottom line is that after the complete reinstall everything works as expected; doing "find /boot/grub/stage1" at boot-up now returns both (hd0,1) and (hd0,3) or both linux partitions. And even better, I can now load Mandriva using the "configfile" notation. 

Just for future reference, is there a better way to reinstall Grub instead of manually deleting the /boot/grub files after uninstalling Grub and then run the grub-install command after reinstalling Grub?

Thanks for all the help, meierfra. :)

---

### Post by meierfra. on 2008-06-23
> "sudo grub-install /dev/sda" 

This is probably all you had to do  and that's what I should have suggested right away.    The whole problem comes from the "stage2"  file. "grub-install"  reinstalls  all stage files. 

To my defense: "setup (hd0)"  does more than just changing a few numbers. It does reinstall the stage1 and stage1.5 files to the first few sectors of the MBR.  Also I  thought that upgrading to Hardy would have automatically upgraded all the stage files in /boot/grub.  It doesn't! 

Thanks for posting your solution. Now it all makes sense to me.

---

### Post by unutbu on 2008-06-24
What is meant by "which linux controls the MBR?" I'm confused by this terminology. I thought there were many MBRs -- one for each partition and one at the beginning of each hard disk. Are we really asking, "Which partition does the MBR at the beginning of the hard disk point to?"

Moreover, is the dd command supposed to tell you the partition in which /boot/grub/menu.lst resides? 
If so, my system seems to be a counterexample.
When I run

```
% sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump

```
I get
```

0000000 0000                                   
0000002

```

But my linux partition is (hd0,2):
```

% sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```

I thought the dd command should return 

```
00000000 ff02
00000002     
```
Am I misunderstanding what the dd command is telling me?

Thanks very much for your help.

---

### Post by meierfra. on 2008-06-24
> I thought there were many MBRs -- one for each partition and one at the beginning of each hard disk. 

The whole hard drive has an MBR.   A primary partition does not have an MBR.   The 63 sectors before a logical partition are called the MBR of that partition. But usually if one talks about an MBR, ones means the MBR of the hard drive.

> If so, my system seems to be a counterexample.
Could be. But are you sure that Grub is installed  to  the MBR of the hard drive? Maybe Grub is installed to the boot sector of /dev/sda3. 

What is the output of

```
sudo dd if=/dev/sda  bs=512  count=1| hexdump
```

and

```
sudo dd if=/dev/sda3 bs=512 count=1 | hexdump
```

---

### Post by unutbu on 2008-06-24
```
% sudo dd if=/dev/sda  bs=512  count=1| hexdump
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.9634e-05 seconds, 17.3 MB/s
0000000 c033 d08e 00bc 8e7c 8ec0 bed8 7c00 00bf
0000010 b906 0200 f3fc 50a4 1c68 cb06 b9fb 0004
0000020 bebd 8007 007e 7c00 0f0b 1085 8301 10c5
0000030 f1e2 18cd 5688 5500 46c6 0511 46c6 0010
0000040 41b4 aabb cd55 5d13 0f72 fb81 aa55 0975
0000050 c1f7 0001 0374 46fe 6610 8060 107e 7400
0000060 6626 0068 0000 6600 76ff 6808 0000 0068
0000070 687c 0001 1068 b400 8a42 0056 f48b 13cd
0000080 839f 10c4 eb9e b814 0201 00bb 8a7c 0056
0000090 768a 8a01 024e 6e8a cd03 6613 7361 fe1e
00000a0 114e 850f 000c 7e80 8000 840f 008a 80b2
00000b0 82eb 3255 8ae4 0056 13cd eb5d 819c fe3e
00000c0 557d 75aa ff6e 0076 8ae8 0f00 1585 b000
00000d0 e6d1 e864 007f dfb0 60e6 78e8 b000 e6ff
00000e0 e864 0071 00b8 cdbb 661a c023 3b75 8166
00000f0 54fb 5043 7541 8132 02f9 7201 662c 0768
0000100 00bb 6600 0068 0002 6600 0868 0000 6600
0000110 6653 6653 6655 0068 0000 6600 0068 007c
0000120 6600 6861 0000 cd07 5a1a f632 00ea 007c
0000130 cd00 a018 07b7 08eb b6a0 eb07 a003 07b5
0000140 e432 0005 8b07 acf0 003c fc74 07bb b400
0000150 cd0e eb10 2bf2 e4c9 eb64 2400 e002 24f8
0000160 c302 6e49 6176 696c 2064 6170 7472 7469
0000170 6f69 206e 6174 6c62 0065 7245 6f72 2072
0000180 6f6c 6461 6e69 2067 706f 7265 7461 6e69
0000190 2067 7973 7473 6d65 4d00 7369 6973 676e
00001a0 6f20 6570 6172 6974 676e 7320 7379 6574
00001b0 006d 0000 6200 997a 0000 4800 0000 0100
00001c0 0001 fede 063f 003f 0000 b708 0001 0000
00001d0 0701 fe0b 93bf b747 0001 124d 00a0 0080
00001e0 9481 fe83 ffff c994 00a1 a2f4 2444 fe00
00001f0 ffff fe05 ffff 6c88 24e6 6a39 005c aa55
0000200
% sudo dd if=/dev/sda3 bs=512 count=1 | hexdump
1+0 records in
1+0 records out
0000000 48eb 0090 0000 0000 0000 0000 0000 0000
0000010 0000 0000 0000 0000 0000 0000 0000 0000
*
0000030 0000 0000 0000 0000 0000 0000 0000 0203
0000040 00ff 8000 4314 08e6 0800 90fa f690 80c2
0000050 0275 80b2 59ea 007c 3100 8ec0 8ed8 bcd0
0000060 2000 a0fb 7c40 ff3c 0274 c288 be52 7d7f
0000070 34e8 f601 80c2 5474 41b4 aabb cd55 5a13
0000080 7252 8149 55fb 75aa a043 7c41 c084 0575
0000090 e183 7401 6637 4c8b be10 7c05 44c6 01ff
00000a0 8b66 441e c77c 1004 c700 0244 0001 8966
00000b0 085c 44c7 0006 6670 c031 4489 6604 4489
00000c0 b40c cd42 7213 bb05 7000 7deb 08b4 13cd
00000d0 0a73 c2f6 0f80 ea84 e900 008d 05be c67c
00000e0 ff44 6600 c031 f088 6640 4489 3104 88d2
00000f0 c1ca 02e2 e888 f488 8940 0844 c031 d088
0000100 e8c0 6602 0489 a166 7c44 3166 66d2 34f7
0000110 5488 660a d231 f766 0474 5488 890b 0c44
0000120 443b 7d08 8a3c 0d54 e2c0 8a06 0a4c c1fe
0000130 d108 6c8a 5a0c 748a bb0b 7000 c38e db31
0000140 01b8 cd02 7213 8c2a 8ec3 4806 607c b91e
0000150 0100 db8e f631 ff31 f3fc 1fa5 ff61 4226
0000160 be7c 7d85 40e8 eb00 be0e 7d8a 38e8 eb00
0000170 be06 7d94 30e8 be00 7d99 2ae8 eb00 47fe
0000180 5552 2042 4700 6f65 006d 6148 6472 4420
0000190 7369 006b 6552 6461 2000 7245 6f72 0072
00001a0 01bb b400 cd0e ac10 003c f475 00c3 0000
00001b0 0000 0000 0000 0000 0000 0000 0000 0000
*
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55
0000200
512 bytes (512 B) copied, 2.4445e-05 seconds, 20.9 MB/s

```

---

### Post by meierfra. on 2008-06-24
unutbu:  You have Grub installed on /dev/sda3 and not on /dev/sda. I didn't spend enough time to figure out what boot loader is installed in the MBR. Do you know? Is it the original Windows MBR?

If you run

```
sudo dd if=/dev/sda   bs=512  count=1| hexdump -c
sudo dd if=/dev/sda3  bs=512  count=1| hexdump -c
```

you will see some  human readable lines. 
For example the  /dev/sda3 output  on  lines 17-19 will say "Grub Geometry Hard Disk Read Error".

My code to identify   the controlling linux does not work if grub is installed on a partition. But if grub is not installed on the MBR, then usually the  partition with the boot flag is in charge of the booting. So you don't need any tricky code.

---

### Post by unutbu on 2008-06-24
Thanks once again meierfra..
I don't actually know what bootloader is installed on the MBR -- the system had Ubuntu pre-installed. I'm guessing that it is the original Windows MBR. 

```

% sudo dd if=/dev/sda   bs=512  count=1| hexdump -c
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.8015e-05 seconds, 18.3 MB/s
0000000   3 300 216 320 274  \0   | 216 300 216 330 276  \0   | 277  \0
0000010 006 271  \0 002 374 363 244   P   h 034 006 313 373 271 004  \0
0000020 275 276  \a 200   ~  \0  \0   |  \v 017 205 020 001 203 305 020
0000030 342 361 315 030 210   V  \0   U 306   F 021 005 306   F 020  \0
0000040 264   A 273 252   U 315 023   ]   r 017 201 373   U 252   u  \t
0000050 367 301 001  \0   t 003 376   F 020   f   ` 200   ~ 020  \0   t
0000060   &   f   h  \0  \0  \0  \0   f 377   v  \b   h  \0  \0   h  \0
0000070   |   h 001  \0   h 020  \0 264   B 212   V  \0 213 364 315 023
0000080 237 203 304 020 236 353 024 270 001 002 273  \0   | 212   V  \0
0000090 212   v 001 212   N 002 212   n 003 315 023   f   a   s 036 376
00000a0   N 021 017 205  \f  \0 200   ~  \0 200 017 204 212  \0 262 200
00000b0 353 202   U   2 344 212   V  \0 315 023   ] 353 234 201   > 376
00000c0   }   U 252   u   n 377   v  \0 350 212  \0 017 205 025  \0 260
00000d0 321 346   d 350 177  \0 260 337 346   ` 350   x  \0 260 377 346
00000e0   d 350   q  \0 270  \0 273 315 032   f   # 300   u   ;   f 201
00000f0 373   T   C   P   A   u   2 201 371 002 001   r   ,   f   h  \a
0000100 273  \0  \0   f   h  \0 002  \0  \0   f   h  \b  \0  \0  \0   f
0000110   S   f   S   f   U   f   h  \0  \0  \0  \0   f   h  \0   |  \0
0000120  \0   f   a   h  \0  \0  \a 315 032   Z   2 366 352  \0   |  \0
0000130  \0 315 030 240 267  \a 353  \b 240 266  \a 353 003 240 265  \a
0000140   2 344 005  \0  \a 213 360 254   <  \0   t 374 273  \a  \0 264
0000150 016 315 020 353 362   + 311 344   d 353  \0   $ 002 340 370   $
0000160 002 303   I   n   v   a   l   i   d       p   a   r   t   i   t
0000170   i   o   n       t   a   b   l   e  \0   E   r   r   o   r    
0000180   l   o   a   d   i   n   g       o   p   e   r   a   t   i   n
0000190   g       s   y   s   t   e   m  \0   M   i   s   s   i   n   g
00001a0       o   p   e   r   a   t   i   n   g       s   y   s   t   e
00001b0   m  \0  \0  \0  \0   b   z 231  \0  \0  \0   H  \0  \0  \0 001
00001c0 001  \0 336 376   ? 006   ?  \0  \0  \0  \b 267 001  \0  \0  \0
00001d0 001  \a  \v 376 277 223   G 267 001  \0   M 022 240  \0 200  \0
00001e0 201 224 203 376 377 377 224 311 241  \0 364 242   D   $  \0 376
00001f0 377 377 005 376 377 377 210   l 346   $   9   j   \  \0   U 252
0000200

```

Your prediction was once again right on the money.
Lines 17-19 say "GRUB Geometry Hard Disk Read Error":

```

% sudo dd if=/dev/sda3  bs=512  count=1| hexdump -c
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.7703e-05 seconds, 18.5 MB/s
0000000 353   H 220  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
0000010  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
*
0000030  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0 003 002
0000040 377  \0  \0 200 024   C 346  \b  \0  \b 372 220 220 366 302 200
0000050   u 002 262 200 352   Y   |  \0  \0   1 300 216 330 216 320 274
0000060  \0     373 240   @   |   < 377   t 002 210 302   R 276 177   }
0000070 350   4 001 366 302 200   t   T 264   A 273 252   U 315 023   Z
0000080   R   r   I 201 373   U 252   u   C 240   A   | 204 300   u 005
0000090 203 341 001   t   7   f 213   L 020 276 005   | 306   D 377 001
00000a0   f 213 036   D   | 307 004 020  \0 307   D 002 001  \0   f 211
00000b0   \  \b 307   D 006  \0   p   f   1 300 211   D 004   f 211   D
00000c0  \f 264   B 315 023   r 005 273  \0   p 353   } 264  \b 315 023
00000d0   s  \n 366 302 200 017 204 352  \0 351 215  \0 276 005   | 306
00000e0   D 377  \0   f   1 300 210 360   @   f 211   D 004   1 322 210
00000f0 312 301 342 002 210 350 210 364   @ 211   D  \b   1 300 210 320
0000100 300 350 002   f 211 004   f 241   D   |   f   1 322   f 367   4
0000110 210   T  \n   f   1 322   f 367   t 004 210   T  \v 211   D  \f
0000120   ;   D  \b   }   < 212   T  \r 300 342 006 212   L  \n 376 301
0000130  \b 321 212   l  \f   Z 212   t  \v 273  \0   p 216 303   1 333
0000140 270 001 002 315 023   r   * 214 303 216 006   H   |   ` 036 271
0000150  \0 001 216 333   1 366   1 377 374 363 245 037   a 377   &   B
0000160   | 276 205   } 350   @  \0 353 016 276 212   } 350   8  \0 353
0000170 006 276 224   } 350   0  \0 276 231   } 350   *  \0 353 376   G
0000180   R   U   B      \0   G   e   o   m  \0   H   a   r   d       D
0000190   i   s   k  \0   R   e   a   d  \0       E   r   r   o   r  \0
00001a0 273 001  \0 264 016 315 020 254   <  \0   u 364 303  \0  \0  \0
00001b0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
*
00001f0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0   U 252
0000200

```

---

### Post by meierfra. on 2008-06-24
Did some googeling. Your MBR is the typical Vista MBR:
[http://www.multibooters.co.uk/mbr.html]("http://www.multibooters.co.uk/mbr.html")

For some reason the output of hexdump swaps the order in each of the four letter blocks: Your output starts with 

c033 d08e


the web page has it as

33c0  8ed0

---

### Post by unutbu on 2008-06-24
I don't understand why, but if I type 

```
sudo dd if=/dev/sda  bs=512  count=1 | hexdump -C
```

rather than 

```
sudo dd if=/dev/sda  bs=512  count=1 | hexdump
```

I get the Vista MBR signature exactly, without the pairs of hex digits swapped.

---

### Post by VMC on 2008-06-24
> **unutbu said:**
> I don't understand why, but if I type 

```
sudo dd if=/dev/sda  bs=512  count=1 | hexdump -C
```

rather than 

```
sudo dd if=/dev/sda  bs=512  count=1 | hexdump
```

I get the Vista MBR signature exactly, without the pairs of hex digits swapped.

Here's a footnote from this [Wiki]("http://en.wikipedia.org/wiki/Master_boot_record")
^  1. On all IBM PC, PC compatible or any other little-endian computers, hexadecimal numbers of two or more bytes are always stored on media or in memory in reverse order (for more efficient CPU processing). Thus, the hex number 0xAA55 (or AA55h) will appear in a disk editor as the sequence: 55 AA.

Mine are not swapped either.

---

