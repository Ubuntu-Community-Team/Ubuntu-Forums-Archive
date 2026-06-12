---
title: "HP Thin client t5740 external wd hd 500 grub error"
date: 2014-05-14
forum: General Help
---

### Post by rayalexny on 2014-05-14
I have a HP thin client t5740 (Processor Intel atom with 2gb of memory RAM, no internal hd)  and external USB hard drive (wd 500gb)
when I try to install ubuntu 14.04 with live usb all the installation process is successful
but when I try to boot I get the following error:

Error: no such partition
entering rescue mode
grub rescue>


I try to repair using this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I try with different version 10.04 ...... and the only distro that work perfectly is Puppy Linux but I dont wanna used I prefer Ubuntu because I get more help at the forum.

Please somebody advise me on that.....:mad::mad::mad::mad:




**Paste from boot-repair at Thu, 15 May 2014 01:54:46 +0100**

  [Download as text]("http://paste.ubuntu.com/7465563/plain/")  [TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603
604
605
606
607
608
609
610
611
612
613
614
615
616
617
618
619
620
621
622
623
624
625
626
627
628
629
630
631
632
633
634
635
636
637
638
639
640
641
642
643
644
645
646
647
648
649
650
651
652
653
654
655
656
657
658
659
660
661
662
663
664
665
666
667
668
669
670
671
672
673
674
675
676
677
678
679
680
681
682
683
684
685
686
687
688
689
690[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 45440 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3930 MB, 3930062848 bytes
112 heads, 47 sectors/track, 1458 cylinders, total 7675904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          1,376     7,675,903     7,674,528   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   781,250,559   781,248,512  83 Linux
/dev/sdb2         781,252,606   976,705,535   195,452,930   5 Extended
/dev/sdb5         970,557,440   976,705,535     6,148,096  82 Linux swap / Solaris
/dev/sdb6         781,252,608   970,557,439   189,304,832  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1DCC-9F3F                              vfat       Lexar
/dev/sdb1        803ffa9f-8d81-445c-87bb-642dc54d96a4   ext4       
/dev/sdb5        dea0d946-4f8e-44df-8809-56aef4644b42   swap       
/dev/sdb6        0e2dec50-c6bc-4289-85a4-b05bccd46a98   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1        /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4 ext4       (rw,nosuid,nodev,uhelper=udisks2)


============================== sda1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sda1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=803ffa9f-8d81-445c-87bb-642dc54d96a4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
#UUID=0e2dec50-c6bc-4289-85a4-b05bccd46a98 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=dea0d946-4f8e-44df-8809-56aef4644b42 none            swap    sw              0       0
UUID=0e2dec50-c6bc-4289-85a4-b05bccd46a98    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

============================= sdb6/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  803ffa9f-8d81-445c-87bb-642dc54d96a4
else
  search --no-floppy --fs-uuid --set=root 803ffa9f-8d81-445c-87bb-642dc54d96a4
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-803ffa9f-8d81-445c-87bb-642dc54d96a4' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  0e2dec50-c6bc-4289-85a4-b05bccd46a98
    else
      search --no-floppy --fs-uuid --set=root 0e2dec50-c6bc-4289-85a4-b05bccd46a98
    fi
    linux    /vmlinuz-3.13.0-24-generic root=UUID=803ffa9f-8d81-445c-87bb-642dc54d96a4 ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-803ffa9f-8d81-445c-87bb-642dc54d96a4' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-803ffa9f-8d81-445c-87bb-642dc54d96a4' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  0e2dec50-c6bc-4289-85a4-b05bccd46a98
        else
          search --no-floppy --fs-uuid --set=root 0e2dec50-c6bc-4289-85a4-b05bccd46a98
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=UUID=803ffa9f-8d81-445c-87bb-642dc54d96a4 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-803ffa9f-8d81-445c-87bb-642dc54d96a4' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  0e2dec50-c6bc-4289-85a4-b05bccd46a98
        else
          search --no-floppy --fs-uuid --set=root 0e2dec50-c6bc-4289-85a4-b05bccd46a98
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /vmlinuz-3.13.0-24-generic root=UUID=803ffa9f-8d81-445c-87bb-642dc54d96a4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  0e2dec50-c6bc-4289-85a4-b05bccd46a98
    else
      search --no-floppy --fs-uuid --set=root 0e2dec50-c6bc-4289-85a4-b05bccd46a98
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  0e2dec50-c6bc-4289-85a4-b05bccd46a98
    else
      search --no-floppy --fs-uuid --set=root 0e2dec50-c6bc-4289-85a4-b05bccd46a98
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  be 9f 5f a2 d6 9a a7 85  a8 5c 03 5f f1 9d e0 26  |.._......\._...&|
00000010  d4 02 c8 10 88 6d 0e c7  66 16 ad 48 df 0d 17 d8  |.....m..f..H....|
*
000001b0  d4 02 c8 10 88 6d 0e c7  66 16 ad 48 df 0d 00 fe  |.....m..f..H....|
000001c0  ff ff 82 fe ff ff 02 90  48 0b 00 d0 5d 00 00 fe  |........H...]...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 90 48 0b 00 00  |............H...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-hPxP5h3r/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-hPxP5h3r/Tmp_Log: No such file or directory
File descriptor 9 (/proc/4315/mounts) leaked on lvscan invocation. Parent PID 13113: bash
File descriptor 63 (pipe:[44276]) leaked on lvscan invocation. Parent PID 13113: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-05-15__00h47 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit
initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern

=================== os-prober:
/dev/sdb1:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Lexar" UUID="1DCC-9F3F" TYPE="vfat"
/dev/sdb1: UUID="803ffa9f-8d81-445c-87bb-642dc54d96a4" TYPE="ext4"
/dev/sdb5: UUID="dea0d946-4f8e-44df-8809-56aef4644b42" TYPE="swap"
/dev/sdb6: UUID="0e2dec50-c6bc-4289-85a4-b05bccd46a98" TYPE="ext4"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 17 01:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 10:48 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:48 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:48 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 10:48 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:48 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:48 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:48 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:48 README




=================== /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot detected in the fstab of sdb1: UUID=0e2dec50-c6bc-4289-85a4-b05bccd46a98     (sdb6)
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    32,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4.
sdb6    : sdb,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/ubuntu/0e2dec50-c6bc-4289-85a4-b05bccd46a98.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: Lexar USB Flash Drive (scsi)
Disk /dev/sda: 3930MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      705kB  3930MB  3929MB  primary  fat32        boot


Model: WD My Passport 07A8 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  400GB  400GB   primary   ext4            boot
2      400GB   500GB  100GB   extended
6      400GB   497GB  96.9GB  logical   ext4
5      497GB   500GB  3148MB  logical   linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:3930MB:scsi:512:512:msdos:Lexar USB Flash Drive;
1:705kB:3930MB:3929MB:fat32::boot;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:WD My Passport 07A8;
1:1049kB:400GB:400GB:ext4::boot;
2:400GB:500GB:100GB:::;
6:400GB:497GB:96.9GB:ext4::;
5:497GB:500GB:3148MB:linux-swap(v1)::;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb6 on /media/ubuntu/0e2dec50-c6bc-4289-85a4-b05bccd46a98 type ext4 (rw,nosuid,nodev,uhelper=udisks2)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb5 sdb6 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom usb vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  100M  1.4G   7% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      297M  1.1M  296M   1% /run
/dev/sda1      vfat       3.7G  1.9G  1.8G  52% /cdrom
/dev/loop0     squashfs   936M  936M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.5G  1.2M  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G   80K  1.5G   1% /run/shm
none           tmpfs      100M   68K  100M   1% /run/user
/dev/sdb1      ext4       367G  3.1G  345G   1% /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4
/dev/sdb6      ext4        89G   94M   85G   1% /media/ubuntu/0e2dec50-c6bc-4289-85a4-b05bccd46a98

=================== fdisk -l:

Disk /dev/sda: 3930 MB, 3930062848 bytes
112 heads, 47 sectors/track, 1458 cylinders, total 7675904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1376     7675903     3837264    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b82b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   781250559   390624256   83  Linux
/dev/sdb2       781252606   976705535    97726465    5  Extended
/dev/sdb5       970557440   976705535     3074048   82  Linux swap / Solaris
/dev/sdb6       781252608   970557439    94652416   83  Linux

Partition table entries are not in disk order


/boot detected. Please check the options.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdb1 into the MBR of sdb, using the following options:        sdb6/boot,
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Custom-Repair
This setting will reinstall the grub2 of sdb1 into the MBR of sdb, using the following options:        sdb6/boot,
Additional repair will be performed: unhide-bootmenu-10s


Mount sdb6 on /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4/boot

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
Subsystem: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42]
Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
*******

grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
,.

Reinstall the GRUB of sdb1 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

chroot /media/ubuntu/803ffa9f-8d81-445c-87bb-642dc54d96a4 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin

Boot successfully repaired.

You can now reboot your computer.[/TD]
[/TR]
[/TABLE]

---

