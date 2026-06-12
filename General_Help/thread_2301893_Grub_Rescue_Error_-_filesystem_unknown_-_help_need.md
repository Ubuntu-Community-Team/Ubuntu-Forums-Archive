---
title: "Grub Rescue Error - filesystem unknown - help needed (my grad school app data stuck)"
date: 2015-11-06
forum: General Help
---

### Post by Arun_Mishra on 2015-11-06
[COLOR=#000000]I have Ubuntu installed in /dev/sda3 18.9 GB partition. [/COLOR]

[COLOR=#000000]I did a fresh install of Ubuntu 15.10 a couple of days back in /dev/sda3 and was using it yesterday. All of a sudden the system froze and did not respond for half an hour. [/COLOR][COLOR=#000000]So I used the power button to shut down my system and restart it. (I know so stupid of me [/COLOR]:([COLOR=#000000]
 But after restarting, I am not able to use two partitions sda2 (176 GB) and sda3 (18.9 GB). Both these partitions where open when my system froze. So, I guess, it must have done something to the partitions when my system froze. It might have done some short of damage to my partitions. I have valuable data in both the partitions, especially the 176 GB partition. [/COLOR]:mad:[COLOR=#000000]

On booting, I got the following error:

Unknown filesystem
Entering grub rescue
grub rescue>

Then I tried to repair grub2 using grub-repair. [/COLOR][COLOR=#000000]I got the following message from Boot Repair. Still unable to boot. Please help. I have my grad school application data stuck in the 176 GB drive. Can't format. I am a new Ubuntu user.   [/COLOR]:confused: 

[COLOR=#000000]Pastebin URL: [/COLOR][http://paste.ubuntu.com/13113691/](http://paste.ubuntu.com/13113691/)

[COLOR=#000000]Ubuntu Pastebin[/COLOR]

[COLOR=#000000]Paste from boot-repair at Thu, 5 Nov 2015 17:04:26 +0000[/COLOR]
Code:

[Download as text]("http://paste.ubuntu.com/13113691/plain/")
[COLOR=#000000][FONT=Verdana][TABLE="class: pastetable"]
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
576[/TD]
[TD="class: code"][COLOR=#000000]Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 9Feb2015[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos6[COLOR=#666666])[/COLOR]/boot/grub.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 2000/XP: NTFS
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]
mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 2472664 of /dev/sdb1 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disklabel [COLOR=#AA22FF]type[/COLOR]: dos

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *             63    78,782,759    78,782,697   7 NTFS / exFAT / HPFS
/dev/sda2          78,782,823   448,847,276   370,064,454   7 NTFS / exFAT / HPFS
/dev/sda3         448,847,870   488,396,799    39,548,930   5 Extended
/dev/sda5         484,222,976   488,396,799     4,173,824  82 Linux swap / Solaris
/dev/sda6         448,847,872   484,222,975    35,375,104  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.6 GiB, 3879731200 bytes, 7577600 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disklabel [COLOR=#AA22FF]type[/COLOR]: dos

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *             63     7,576,127     7,576,065   b W95 FAT32


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        12E66F5DE66F3FD9                       ntfs       
/dev/sda5        55fa8f81-8934-49e1-9c91-1f48a01cc7ba   swap       
/dev/sdb1        349A-5CF3                              vfat       [COLOR=#B8860B]TOSHIBA[/COLOR]

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -l /dev/disk/by-id"[/COLOR] output: [COLOR=#666666]======================[/COLOR]

total 0
lrwxrwxrwx 1 root root  9 Nov  5 17:00 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY -> ../../sda
lrwxrwxrwx 1 root root 10 Nov  5 17:02 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  5 17:01 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov  5 17:00 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov  5 17:00 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov  5 17:01 ata-FUJITSU_MHZ2250BH_G2_K617T862D9RY-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Nov  5  2015 ata-Slimtype_DVD_A_DS8A1P_804290001073 -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov  5 17:00 usb-TOSHIBA_TransMemory_EDEF154F0B49CE31CEBCA621-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  5 17:00 usb-TOSHIBA_TransMemory_EDEF154F0B49CE31CEBCA621-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Nov  5 17:00 wwn-0x500000e04224af2e -> ../../sda
lrwxrwxrwx 1 root root 10 Nov  5 17:02 wwn-0x500000e04224af2e-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  5 17:01 wwn-0x500000e04224af2e-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov  5 17:00 wwn-0x500000e04224af2e-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov  5 17:00 wwn-0x500000e04224af2e-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov  5 17:01 wwn-0x500000e04224af2e-part6 -> ../../sda6

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sdb1        /cdrom                   vfat       [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]==============================[/COLOR] sdb1/syslinux.cfg: [COLOR=#666666]==============================[/COLOR]

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash ---

label ubnentry0
menu label ^Help
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash ---

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity  quiet splash ---

label ubnentry3
menu label ^Check disc [COLOR=#AA22FF]**for **[/COLOR]defects
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper integrity-check  quiet splash ---

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

--------------------------------------------------------------------------------

[COLOR=#666666]==============[/COLOR] sdb1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 menu.c32                           :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda3

00000000  87 03 37 [COLOR=#AA22FF]fc [/COLOR]b9 ad 10 f8  2b d0 38 8f 8f ac c0 73  |..7.....+.8....s|
00000010  19 72 ba 7f 6b ca 3e 00  40 80 48 d7 d6 fe fa 81  |.r..k.>.@.H.....|
00000020  97 82 5a dd a0 68 0a 9f  24 5e e4 a7 41 09 04 41  |..Z..h..[COLOR=#B8860B]$^[/COLOR]..A..A|
00000030  35 f3 f8 d0 d0 57 2a 32  e4 56 02 dc f7 58 0e cf  |5....W*2.V...X..|
00000040  f6 ce 0a e9 1a 3f f7 1d  73 8b 7d 22 85 5b 7a 28  |.....?..s.[COLOR=#666666]}[/COLOR][COLOR=#BB4444]".[z(|[/COLOR]
[COLOR=#BB4444]00000050  bb 63 1d 77 cf 66 bc 62  f4 b6 f8 55 7b 37 6f 3e  |.c.w.f.b...U{7o>|[/COLOR]
[COLOR=#BB4444]00000060  65 6d 4e 8c a9 04 07 44  56 04 17 e1 31 bb 4d 19  |emN....DV...1.M.|[/COLOR]
[COLOR=#BB4444]00000070  57 45 48 c8 16 a6 b6 27  8f e5 34 ba 6f 91 b4 de  |WEH....'..4.o...|[/COLOR]
[COLOR=#BB4444]00000080  ab 9c 03 b0 a0 88 f0 63  43 73 96 76 9c e1 dd 4e  |.......cCs.v...N|[/COLOR]
[COLOR=#BB4444]00000090  df 7d fc e5 a9 25 66 0d  91 e7 eb 35 de 11 7c 4d  |.}...%f....5..|M|[/COLOR]
[COLOR=#BB4444]000000a0  31 76 9f 7a ce 9b fe c5  36 95 94 c4 cf e1 ca cf  |1v.z....6.......|[/COLOR]
[COLOR=#BB4444]000000b0  3b 40 1e cd d3 27 30 80  4e c8 c8 de 47 31 70 b7  |;@...'0.N...G1p.|[/COLOR]
[COLOR=#BB4444]000000c0  c6 10 87 a6 51 5e 60 f4  86 70 23 e7 01 6e 2b ec  |....Q^`..p#..n+.|[/COLOR]
[COLOR=#BB4444]000000d0  e3 61 3a fb fe 7b 51 46  bb 47 80 f3 60 7a 77 ca  |.a:..{QF.G..`zw.|[/COLOR]
[COLOR=#BB4444]000000e0  6d ce 3d 09 00 61 f2 bb  e6 ed 99 13 1c 9e c3 bd  |m.=..a..........|[/COLOR]
[COLOR=#BB4444]000000f0  b2 6a a0 c4 2c fe 6e 3b  79 ec 93 5a f8 ab d3 a8  |.j..,.n;y..Z....|[/COLOR]
[COLOR=#BB4444]00000100  5e 33 8c 68 1e d4 36 ab  83 85 2e 2a 2a 5f 49 fa  |^3.h..6....**_I.|[/COLOR]
[COLOR=#BB4444]00000110  27 1a af 72 5a 96 8a e1  f6 3b d2 35 9a be 77 11  |'..rZ....;.5..w.|[/COLOR]
[COLOR=#BB4444]00000120  9c 56 c2 14 e7 01 9b 08  69 2c 26 3c 43 b7 08 9a  |.V......i,&<C...|[/COLOR]
[COLOR=#BB4444]00000130  7e 02 44 21 54 bc f9 e6  d3 1c 16 a0 72 97 64 ab  |~.D!T.......r.d.|[/COLOR]
[COLOR=#BB4444]00000140  54 5d 18 eb da ec e3 ba  fb 7c 66 ff 55 73 e7 8d  |T].......|f.Us..|[/COLOR]
[COLOR=#BB4444]00000150  b8 15 3b 08 27 49 92 56  a0 0b ff 46 9b 7e 22 64  |..;.'I.V...F.~"[/COLOR]d|
00000160  45 a5 29 fd 91 46 64 69  21 77 91 8c f6 31 4d d7  |E.[COLOR=#666666])[/COLOR]..Fdi!w...1M.|
00000170  75 8a dd 48 ae 18 f3 44  5c f4 80 a1 ef 11 58 2c  |u..H...D[COLOR=#BB6622]**\.**[/COLOR]....X,|
00000180  93 0a 4f 35 98 25 72 88  62 ff 72 1f 9b 35 0d 42  |..O5.%r.b.r..5.B|
00000190  9b ff e3 fa 1e 84 9a 95  27 aa 9f 9b 64 68 34 06  |........[COLOR=#BB4444]'...dh4.|[/COLOR]
[COLOR=#BB4444]000001a0  aa 9c 72 d3 34 90 38 2f  c3 e8 68 a8 18 93 d0 a6  |..r.4.8/..h.....|[/COLOR]
[COLOR=#BB4444]000001b0  71 59 de 1f d8 fa 13 6d  ba 65 29 07 49 c6 00 fe  |qY.....m.e).I...|[/COLOR]
[COLOR=#BB4444]000001c0  ff ff 82 fe ff ff 02 c8  1b 02 00 b0 3f 00 00 fe  |............?...|[/COLOR]
[COLOR=#BB4444]000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c8 1b 02 00 00  |................|[/COLOR]
[COLOR=#BB4444]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]Unknown BootLoader on sda6[/COLOR]



[COLOR=#BB4444]=============================== StdErr Messages: ===============================[/COLOR]

[COLOR=#BB4444]cat: write error: Broken pipe[/COLOR]
[COLOR=#BB4444]hexdump: /dev/sda6: Input/output error[/COLOR]
[COLOR=#BB4444]hexdump: /dev/sda6: Input/output error[/COLOR]
[COLOR=#BB4444]File descriptor 9 (/proc/13955/mounts) leaked on lvs invocation. Parent PID 26053: bash[/COLOR]
[COLOR=#BB4444]File descriptor 63 (pipe:[121187]) leaked on lvs invocation. Parent PID 26053: bash[/COLOR]

[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2015-11-05__16h41 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 4ppa33[/COLOR]
[COLOR=#BB4444]boot-sav version : 4ppa33[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa47~saucy[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 4ppa33[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda[COLOR=#BB4444]': Input/output error.[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda[COLOR=#BB4444]': Input/output error.[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda[COLOR=#BB4444]': Input/output error.[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda[COLOR=#BB4444]': Input/output error.[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda[COLOR=#BB4444]': Input/output error.[/COLOR]
[COLOR=#BB4444]error: cannot read `/dev/sda'[/COLOR]: Input/output error.
error: cannot [COLOR=#AA22FF]read[/COLOR] [COLOR=#BB4444]`[/COLOR]/dev/sda': Input/output error.
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Ubuntu 15.10, wily, Ubuntu, i686[COLOR=#666666])[/COLOR]
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity  quiet splash --- [COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/casper/vmlinuz
ls: cannot access /home/usr/.config: No such file or [COLOR=#B8860B]directory[/COLOR]

[COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda1:Windows 8 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain

[COLOR=#666666]===================[/COLOR] blkid:
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"12E66F5DE66F3FD9"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR] [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"57ad6c4e-01"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"TOSHIBA"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"349A-5CF3"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR] [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"3bf37c58-01"[/COLOR]
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sda5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"55fa8f81-8934-49e1-9c91-1f48a01cc7ba"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR] [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"57ad6c4e-05"[/COLOR]


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.


[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA FUJITSU MHZ2250B [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 250GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  40.3GB  40.3GB  primary   ntfs            boot
2      40.3GB  230GB   189GB   primary   ntfs
3      230GB   250GB   20.2GB  extended
6      230GB   248GB   18.1GB  logical
5      248GB   250GB   2137MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]


Model: TOSHIBA TransMemory [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 3880MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  3879MB  3879MB  primary  fat32        [COLOR=#B8860B]boot[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA FUJITSU MHZ2250B:;
1:32.3kB:40.3GB:40.3GB:ntfs::boot;
2:40.3GB:230GB:189GB:ntfs::;
3:230GB:250GB:20.2GB:::;
6:230GB:248GB:18.1GB:::;
5:248GB:250GB:2137MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

BYT;
/dev/sdb:3880MB:scsi:512:512:msdos:TOSHIBA TransMemory:;
1:32.3kB:3879MB:3879MB:fat32::boot;

[COLOR=#666666]===================[/COLOR] lsblk:
KNAME TYPE FSTYPE     SIZE LABEL   MODEL            UUID
sda   disk          232.9G         FUJITSU MHZ2250B
sda1  part ntfs      37.6G                          12E66F5DE66F3FD9
sda2  part          176.5G
sda3  part              1K
sda5  part swap         2G                          55fa8f81-8934-49e1-9c91-1f48a01cc7ba
sda6  part           16.9G
sdb   disk            3.6G         TransMemory
sdb1  part vfat       3.6G TOSHIBA                  349A-5CF3
sr0   rom            1024M         DVD A  DS8A1P
loop0 loop squashfs   1.1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0
sda3     1  0  0
sda5     1  0  0         [COLOR=#666666][[/COLOR]SWAP[COLOR=#666666]][/COLOR]
sda6     1  0  0
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


[COLOR=#666666]===================[/COLOR] mount:
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,nosuid,relatime,size[COLOR=#666666]=[/COLOR]1014216k,nr_inodes[COLOR=#666666]=[/COLOR]213539,mode[COLOR=#666666]=[/COLOR]755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,nosuid,noexec,relatime,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]620,ptmxmode[COLOR=#666666]=[/COLOR]000[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,noexec,relatime,size[COLOR=#666666]=[/COLOR]205344k,mode[COLOR=#666666]=[/COLOR]755[COLOR=#666666])[/COLOR]
/dev/sdb1 on /cdrom [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/cow on / [COLOR=#AA22FF]type [/COLOR]overlay [COLOR=#666666]([/COLOR]rw,relatime,lowerdir[COLOR=#666666]=[/COLOR]//filesystem.squashfs,upperdir[COLOR=#666666]=[/COLOR]/cow/upper,workdir[COLOR=#666666]=[/COLOR]/cow/work[COLOR=#666666])[/COLOR]
securityfs on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime[COLOR=#666666])[/COLOR]
tmpfs on /dev/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
tmpfs on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,size[COLOR=#666666]=[/COLOR]5120k[COLOR=#666666])[/COLOR]
tmpfs on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]755[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,xattr,release_agent[COLOR=#666666]=[/COLOR]/lib/systemd/systemd-cgroups-agent,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
pstore on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/net_cls,net_prio [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,net_cls,net_prio[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/cpuset [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,cpuset,clone_children[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/cpu,cpuacct [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,cpu,cpuacct[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/devices [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,devices[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/freezer [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,freezer[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/blkio [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,blkio[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/perf_event [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,perf_event,release_agent[COLOR=#666666]=[/COLOR]/run/cgmanager/agents/cgm-release-agent.perf_event[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/hugetlb [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent[COLOR=#666666]=[/COLOR]/run/cgmanager/agents/cgm-release-agent.hugetlb[COLOR=#666666])[/COLOR]
cgroup on /sys/fs/cgroup/memory [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,nosuid,nodev,noexec,relatime,memory[COLOR=#666666])[/COLOR]
systemd-1 on /proc/sys/fs/binfmt_misc [COLOR=#AA22FF]type [/COLOR]autofs [COLOR=#666666]([/COLOR]rw,relatime,fd[COLOR=#666666]=[/COLOR]29,pgrp[COLOR=#666666]=[/COLOR]1,timeout[COLOR=#666666]=[/COLOR]0,minproto[COLOR=#666666]=[/COLOR]5,maxproto[COLOR=#666666]=[/COLOR]5,direct[COLOR=#666666])[/COLOR]
hugetlbfs on /dev/hugepages [COLOR=#AA22FF]type [/COLOR]hugetlbfs [COLOR=#666666]([/COLOR]rw,relatime[COLOR=#666666])[/COLOR]
debugfs on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw,relatime[COLOR=#666666])[/COLOR]
mqueue on /dev/mqueue [COLOR=#AA22FF]type [/COLOR]mqueue [COLOR=#666666]([/COLOR]rw,relatime[COLOR=#666666])[/COLOR]
tracefs on /sys/kernel/debug/tracing [COLOR=#AA22FF]type [/COLOR]tracefs [COLOR=#666666]([/COLOR]rw,relatime[COLOR=#666666])[/COLOR]
fusectl on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw,relatime[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev,relatime[COLOR=#666666])[/COLOR]
cgmfs on /run/cgmanager/fs [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,relatime,size[COLOR=#666666]=[/COLOR]100k,mode[COLOR=#666666]=[/COLOR]755[COLOR=#666666])[/COLOR]
tmpfs on /run/user/999 [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev,relatime,size[COLOR=#666666]=[/COLOR]205344k,mode[COLOR=#666666]=[/COLOR]700,uid[COLOR=#666666]=[/COLOR]999,gid[COLOR=#666666]=[/COLOR]999[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,relatime,user_id[COLOR=#666666]=[/COLOR]999,group_id[COLOR=#666666]=[/COLOR]999[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,relatime,user_id[COLOR=#666666]=[/COLOR]0,group_id[COLOR=#666666]=[/COLOR]0,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg log mapper mcelog mem memory_bandwidth mqueue ndctl0 net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vfio vga_arbiter vhci vhost-net xconsole zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  e8 20 b2 04 00 00 00 00  |......... ......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d9 3f 6f e6 5d 6f e6 12  |.........?o.[COLOR=#666666]][/COLOR]o..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 fe 01 90 90 66 60 1e  |.............f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk [COLOR=#AA22FF]read [/COLOR]error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  991M     0  991M   0% /dev
tmpfs          tmpfs     201M   22M  180M  11% /run
/dev/sdb1      vfat      3.7G  1.2G  2.5G  33% /cdrom
/dev/loop0     squashfs  1.2G  1.2G     0 100% /rofs
/cow           overlay  1003M  175M  828M  18% /
tmpfs          tmpfs    1003M  504K 1003M   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs    1003M     0 1003M   0% /sys/fs/cgroup
tmpfs          tmpfs    1003M   24K 1003M   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     201M   80K  201M   1% /run/user/999
/dev/sda1      fuseblk    38G   28G   11G  72% /mnt/boot-sav/sda1

[COLOR=#666666]===================[/COLOR] fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.1 GiB, 1186353152 bytes, 2317096 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes




Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disklabel [COLOR=#AA22FF]type[/COLOR]: dos
Disk identifier: 0x57ad6c4e

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63  78782759  78782697  37.6G  7 HPFS/NTFS/exFAT
/dev/sda2        78782823 448847276 370064454 176.5G  7 HPFS/NTFS/exFAT
/dev/sda3       448847870 488396799  39548930  18.9G  5 Extended
/dev/sda5       484222976 488396799   4173824     2G 82 Linux swap / Solaris
/dev/sda6       448847872 484222975  35375104  16.9G 83 Linux

Partition table entries are not in disk order.


Disk /dev/sdb: 3.6 GiB, 3879731200 bytes, 7577600 sectors
Units: sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disklabel [COLOR=#AA22FF]type[/COLOR]: dos
Disk identifier: 0x3bf37c58

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *       63 7576127 7576065  3.6G  b W95 FAT32


No OS or WinEFI [COLOR=#B8860B]system[/COLOR]

[COLOR=#666666]===================[/COLOR] Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for **[/COLOR]fsck[COLOR=#666666])[/COLOR] except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

ntfsfix /dev/sda1
Refusing to operate on [COLOR=#AA22FF]read[/COLOR]-write mounted device /dev/sda1.

Boot successfully repaired.

You can now reboot your computer.
[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[Download as text]("http://paste.ubuntu.com/13113691/plain/")

---

### Post by yancek on 2015-11-06
Your comments in your post do not coincide with the output of the bootinfoscript.  sda3 is actually an Extended partition which cannot hold data but is only a container for logical partitions.  The logical partition sda6 is a Linux partition and likely where you had Ubuntu installed.  If you scroll down a little to sda6 you will not see the standard Linux boot files referred to as you see the windows files referred to in sda1.  Also, no grub.cfg files shows in the output.  It might be that you just need to do a filesystem check on sda6.  If that doesn't help you may need to reinstall Grub and then chroot and update it.  The first link has some info on fsck which you would need to run on sda6.  If reinstalling Grub2 is needed, go to the second link below which has several methods explained.

   [https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Arun_Mishra on 2015-11-06
You are absolutely right. Ubuntu is installed in sda6. In fact sda3 is the extended partition with the swap and sda6 which has the Ubuntu installation. My problem actually something wrong with the superblock in sda6. I fixed it using the help available in the blog below, which I found in other Ubuntu threads:

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

