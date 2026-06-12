---
title: "Minimal BASH-like line editing...."
date: 2014-01-16
forum: General Help
---

### Post by roy4 on 2014-01-16
Hello, 

My game crashed today on ubuntu 12.04 and i had to turn the power off. But wen restarted ubuntu again i get the following error:

```
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>
```

Im new to ubuntu, so i dont know how to solve the error.
 
I tried to use the repair boot but it still doesnt work. Info from the repair boot:

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
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
524[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 31Jan2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]3.61-4.03[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /wubildr

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E[COLOR=#666666]}[/COLOR].u......
    Boot sector info:  Syslinux looks at sector 1126251 of /dev/sdb1 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   763,570,175   763,363,328   7 NTFS / exFAT / HPFS
/dev/sda3         763,570,176 1,903,476,735 1,139,906,560   f W95 Extended [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda5         763,572,224 1,903,476,735 1,139,904,512   7 NTFS / exFAT / HPFS
/dev/sda4       1,903,476,736 1,953,523,711    50,046,976  27 Hidden NTFS [COLOR=#666666]([/COLOR]Recovery Environment[COLOR=#666666])[/COLOR]


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *            245     1,999,871     1,999,627   6 FAT16


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1AB2D55EB2D53F47                       ntfs       SYSTEM
/dev/sda2        0AE65214E651FFFD                       ntfs       
/dev/sda4        4042AF6042AF5A04                       ntfs       SAMSUNG_REC
/dev/sda5        9E9C5B9F9C5B70AF                       ntfs       
/dev/sdb1        3B69-1AFD                              [COLOR=#B8860B]vfat[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sdb1        /cdrom                   vfat       [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sdb1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------

[COLOR=#AA22FF]**if **[/COLOR]loadfont /boot/grub/font.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray

menuentry [COLOR=#BB4444]"Boot-Repair-Disk session"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]==============================[/COLOR] sdb1/syslinux.cfg: [COLOR=#666666]==============================[/COLOR]

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash --

label ubnentry2
menu label ^64bit session [COLOR=#666666]([/COLOR]failsafe[COLOR=#666666])[/COLOR]
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  noapic noapm nodma nomce nolapic nomodeset nosmp [COLOR=#B8860B]vga[/COLOR][COLOR=#666666]=[/COLOR]normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --

--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sdb1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]=================[/COLOR] sdb1: Location of files loaded by Syslinux: [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

            ?? [COLOR=#666666]=[/COLOR] ??             syslinux.cfg                                   1
            ?? [COLOR=#666666]=[/COLOR] ??             ldlinux.sys                                    1
            ?? [COLOR=#666666]=[/COLOR] ??             menu.c32                                       [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]==============[/COLOR] sdb1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 menu.c32                           :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda2/Wubi



[COLOR=#666666]=========[/COLOR] Devices which don[COLOR=#BB4444]'t seem to have a corresponding hard drive: =========[/COLOR]

[COLOR=#BB4444]sdc [/COLOR]

[COLOR=#BB4444]=============================== StdErr Messages: ===============================[/COLOR]

[COLOR=#BB4444]File descriptor 8 (/proc/8037/mounts) leaked on lvscan invocation. Parent PID 15533: bash[/COLOR]
[COLOR=#BB4444]  No volume groups found[/COLOR]

[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2014-01-16__21h59 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 3.198~ppa16~raring[/COLOR]
[COLOR=#BB4444]boot-sav version : 3.198~ppa16~raring[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa45~raring[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 3.198~ppa16~raring[/COLOR]
[COLOR=#BB4444]File descriptor 8 (/proc/8037/mounts) leaked on lvs invocation. Parent PID 9428: /bin/sh[/COLOR]
[COLOR=#BB4444]No volume groups found[/COLOR]
[COLOR=#BB4444]boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)[/COLOR]
[COLOR=#BB4444]ls: cannot access /home/usr/.config: No such file or directory[/COLOR]
[COLOR=#BB4444]CPU op-mode(s):        32-bit, 64-bit[/COLOR]
[COLOR=#BB4444]initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash -- BOOT_IMAGE=/casper/vmlinuz[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda1:Windows 7 (loader):Windows:chain[/COLOR]
[COLOR=#BB4444]/dev/sda4:Windows Recovery Environment (loader):Windows1:chain[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/loop0: TYPE="squashfs"[/COLOR]
[COLOR=#BB4444]/dev/sda1: LABEL="SYSTEM" UUID="1AB2D55EB2D53F47" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda2: UUID="0AE65214E651FFFD" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda4: LABEL="SAMSUNG_REC" UUID="4042AF6042AF5A04" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="9E9C5B9F9C5B70AF" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sdb1: SEC_TYPE="msdos" UUID="3B69-1AFD" TYPE="vfat"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Windows not detected by os-prober on sda2.[/COLOR]
[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]
[COLOR=#BB4444]There is Wubi inside sda2[/COLOR]
[COLOR=#BB4444]=================== UEFI/Legacy mode:[/COLOR]
[COLOR=#BB4444]This live-session is not in EFI-mode.[/COLOR]
[COLOR=#BB4444]EFI in dmesg.[/COLOR]
[COLOR=#BB4444][    0.000000] ACPI: UEFI 00000000aafea000 0003E (v01 SECCSD LH43STAR 00000002 PTL  00000002)[/COLOR]
[COLOR=#BB4444][    0.000000] ACPI: UEFI 00000000aafe9000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)[/COLOR]
[COLOR=#BB4444][    0.000000] ACPI: UEFI 00000000aafe6000 00256 (v01 SECCSD LH43STAR 00000002 PTL  00000002)[/COLOR]
[COLOR=#BB4444]SecureBoot maybe enabled.[/COLOR]


[COLOR=#BB4444]=================== PARTITIONS & DISKS:[/COLOR]
[COLOR=#BB4444]sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.[/COLOR]
[COLOR=#BB4444]sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.[/COLOR]
[COLOR=#BB4444]sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.[/COLOR]
[COLOR=#BB4444]sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.[/COLOR]

[COLOR=#BB4444]sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes[/COLOR]


[COLOR=#BB4444]=================== parted -l:[/COLOR]

[COLOR=#BB4444]Model: ATA SAMSUNG HN-M101M (scsi)[/COLOR]
[COLOR=#BB4444]Disk /dev/sda: 1000GB[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512B/4096B[/COLOR]
[COLOR=#BB4444]Partition Table: msdos[/COLOR]

[COLOR=#BB4444]Number  Start   End     Size    Type      File system  Flags[/COLOR]
[COLOR=#BB4444]1      1049kB  106MB   105MB   primary   ntfs         boot[/COLOR]
[COLOR=#BB4444]2      106MB   391GB   391GB   primary   ntfs[/COLOR]
[COLOR=#BB4444]3      391GB   975GB   584GB   extended               lba[/COLOR]
[COLOR=#BB4444]5      391GB   975GB   584GB   logical   ntfs[/COLOR]
[COLOR=#BB4444]4      975GB   1000GB  25.6GB  primary   ntfs         diag[/COLOR]


[COLOR=#BB4444]Model: SanDisk Cruzer Micro (scsi)[/COLOR]
[COLOR=#BB4444]Disk /dev/sdb: 1025MB[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512B/512B[/COLOR]
[COLOR=#BB4444]Partition Table: msdos[/COLOR]

[COLOR=#BB4444]Number  Start  End     Size    Type     File system  Flags[/COLOR]
[COLOR=#BB4444]1      125kB  1024MB  1024MB  primary  fat16        boot[/COLOR]

[COLOR=#BB4444]=================== parted -lm:[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sda:1000GB:scsi:512:4096:msdos:ATA SAMSUNG HN-M101M;[/COLOR]
[COLOR=#BB4444]1:1049kB:106MB:105MB:ntfs::boot;[/COLOR]
[COLOR=#BB4444]2:106MB:391GB:391GB:ntfs::;[/COLOR]
[COLOR=#BB4444]3:391GB:975GB:584GB:::lba;[/COLOR]
[COLOR=#BB4444]5:391GB:975GB:584GB:ntfs::;[/COLOR]
[COLOR=#BB4444]4:975GB:1000GB:25.6GB:ntfs::diag;[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sdb:1025MB:scsi:512:512:msdos:SanDisk Cruzer Micro;[/COLOR]
[COLOR=#BB4444]1:125kB:1024MB:1024MB:fat16::boot;[/COLOR]


[COLOR=#BB4444]=================== mount:[/COLOR]
[COLOR=#BB4444]/cow on / type overlayfs (rw)[/COLOR]
[COLOR=#BB4444]proc on /proc type proc (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]udev on /dev type devtmpfs (rw,mode=0755)[/COLOR]
[COLOR=#BB4444]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/COLOR]
[COLOR=#BB4444]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)[/COLOR]
[COLOR=#BB4444]/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)[/COLOR]
[COLOR=#BB4444]/dev/loop0 on /rofs type squashfs (ro,noatime)[/COLOR]
[COLOR=#BB4444]none on /sys/fs/cgroup type tmpfs (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/fs/fuse/connections type fusectl (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/kernel/debug type debugfs (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/kernel/security type securityfs (rw)[/COLOR]
[COLOR=#BB4444]tmpfs on /tmp type tmpfs (rw,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)[/COLOR]
[COLOR=#BB4444]none on /run/shm type tmpfs (rw,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)[/COLOR]
[COLOR=#BB4444]gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)[/COLOR]
[COLOR=#BB4444]/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/COLOR]
[COLOR=#BB4444]/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/COLOR]
[COLOR=#BB4444]/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/COLOR]
[COLOR=#BB4444]/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/COLOR]


[COLOR=#BB4444]=================== ls:[/COLOR]
[COLOR=#BB4444]/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero[/COLOR]
[COLOR=#BB4444]ls /dev/mapper:  control[/COLOR]

[COLOR=#BB4444]=================== hexdump -n512 -C /dev/sda1[/COLOR]
[COLOR=#BB4444]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/COLOR]
[COLOR=#BB4444]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|[/COLOR]
[COLOR=#BB4444]00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|[/COLOR]
[COLOR=#BB4444]00000040  f6 00 00 00 01 00 00 00  47 3f d5 b2 5e d5 b2 1a  |........G?..^...|[/COLOR]
[COLOR=#BB4444]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/COLOR]
[COLOR=#BB4444]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/COLOR]
[COLOR=#BB4444]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/COLOR]
[COLOR=#BB4444]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/COLOR]
[COLOR=#BB4444]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/COLOR]
[COLOR=#BB4444]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/COLOR]
[COLOR=#BB4444]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/COLOR]
[COLOR=#BB4444]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/COLOR]
[COLOR=#BB4444]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/COLOR]
[COLOR=#BB4444]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/COLOR]
[COLOR=#BB4444]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/COLOR]
[COLOR=#BB4444]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/COLOR]
[COLOR=#BB4444]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/COLOR]
[COLOR=#BB4444]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/COLOR]
[COLOR=#BB4444]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/COLOR]
[COLOR=#BB4444]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/COLOR]
[COLOR=#BB4444]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/COLOR]
[COLOR=#BB4444]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/COLOR]
[COLOR=#BB4444]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/COLOR]
[COLOR=#BB4444]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |[/COLOR]
[COLOR=#BB4444]00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |[/COLOR]
[COLOR=#BB4444]000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|[/COLOR]
[COLOR=#BB4444]000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|[/COLOR]
[COLOR=#BB4444]000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|[/COLOR]
[COLOR=#BB4444]000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|[/COLOR]
[COLOR=#BB4444]000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|[/COLOR]
[COLOR=#BB4444]000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]=================== hexdump -n512 -C /dev/sda2[/COLOR]
[COLOR=#BB4444]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/COLOR]
[COLOR=#BB4444]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|[/COLOR]
[COLOR=#BB4444]00000020  00 00 00 00 80 00 80 00  ff ff 7f 2d 00 00 00 00  |...........-....|[/COLOR]
[COLOR=#BB4444]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]00000040  f6 00 00 00 01 00 00 00  fd ff 51 e6 14 52 e6 0a  |..........Q..R..|[/COLOR]
[COLOR=#BB4444]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/COLOR]
[COLOR=#BB4444]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/COLOR]
[COLOR=#BB4444]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/COLOR]
[COLOR=#BB4444]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/COLOR]
[COLOR=#BB4444]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/COLOR]
[COLOR=#BB4444]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/COLOR]
[COLOR=#BB4444]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/COLOR]
[COLOR=#BB4444]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/COLOR]
[COLOR=#BB4444]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/COLOR]
[COLOR=#BB4444]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/COLOR]
[COLOR=#BB4444]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/COLOR]
[COLOR=#BB4444]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/COLOR]
[COLOR=#BB4444]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/COLOR]
[COLOR=#BB4444]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/COLOR]
[COLOR=#BB4444]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/COLOR]
[COLOR=#BB4444]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/COLOR]
[COLOR=#BB4444]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/COLOR]
[COLOR=#BB4444]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/COLOR]
[COLOR=#BB4444]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/COLOR]
[COLOR=#BB4444]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |[/COLOR]
[COLOR=#BB4444]00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |[/COLOR]
[COLOR=#BB4444]000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|[/COLOR]
[COLOR=#BB4444]000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|[/COLOR]
[COLOR=#BB4444]000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|[/COLOR]
[COLOR=#BB4444]000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|[/COLOR]
[COLOR=#BB4444]000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|[/COLOR]
[COLOR=#BB4444]000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]=================== hexdump -n512 -C /dev/sda4[/COLOR]
[COLOR=#BB4444]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/COLOR]
[COLOR=#BB4444]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c0 74 71  |........?.....tq|[/COLOR]
[COLOR=#BB4444]00000020  00 00 00 00 80 00 80 00  ff a7 fb 02 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]00000040  f6 00 00 00 01 00 00 00  04 5a af 42 60 af 42 40  |.........Z.B`.B@|[/COLOR]
[COLOR=#BB4444]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/COLOR]
[COLOR=#BB4444]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/COLOR]
[COLOR=#BB4444]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/COLOR]
[COLOR=#BB4444]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/COLOR]
[COLOR=#BB4444]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/COLOR]
[COLOR=#BB4444]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/COLOR]
[COLOR=#BB4444]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/COLOR]
[COLOR=#BB4444]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/COLOR]
[COLOR=#BB4444]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/COLOR]
[COLOR=#BB4444]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/COLOR]
[COLOR=#BB4444]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/COLOR]
[COLOR=#BB4444]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/COLOR]
[COLOR=#BB4444]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/COLOR]
[COLOR=#BB4444]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/COLOR]
[COLOR=#BB4444]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/COLOR]
[COLOR=#BB4444]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/COLOR]
[COLOR=#BB4444]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/COLOR]
[COLOR=#BB4444]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/COLOR]
[COLOR=#BB4444]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/COLOR]
[COLOR=#BB4444]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |[/COLOR]
[COLOR=#BB4444]00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |[/COLOR]
[COLOR=#BB4444]000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|[/COLOR]
[COLOR=#BB4444]000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|[/COLOR]
[COLOR=#BB4444]000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|[/COLOR]
[COLOR=#BB4444]000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|[/COLOR]
[COLOR=#BB4444]000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|[/COLOR]
[COLOR=#BB4444]000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]=================== hexdump -n512 -C /dev/sda5[/COLOR]
[COLOR=#BB4444]00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|[/COLOR]
[COLOR=#BB4444]00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|[/COLOR]
[COLOR=#BB4444]00000020  00 00 00 00 80 00 80 00  ff 8f f1 43 00 00 00 00  |...........C....|[/COLOR]
[COLOR=#BB4444]00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]00000040  f6 00 00 00 01 00 00 00  af 70 5b 9c 9f 5b 9c 9e  |.........p[..[..|[/COLOR]
[COLOR=#BB4444]00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|[/COLOR]
[COLOR=#BB4444]00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|[/COLOR]
[COLOR=#BB4444]00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|[/COLOR]
[COLOR=#BB4444]00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|[/COLOR]
[COLOR=#BB4444]00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|[/COLOR]
[COLOR=#BB4444]000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|[/COLOR]
[COLOR=#BB4444]000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|[/COLOR]
[COLOR=#BB4444]000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|[/COLOR]
[COLOR=#BB4444]000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|[/COLOR]
[COLOR=#BB4444]000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|[/COLOR]
[COLOR=#BB4444]000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|[/COLOR]
[COLOR=#BB4444]00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|[/COLOR]
[COLOR=#BB4444]00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|[/COLOR]
[COLOR=#BB4444]00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|[/COLOR]
[COLOR=#BB4444]00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|[/COLOR]
[COLOR=#BB4444]00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|[/COLOR]
[COLOR=#BB4444]00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|[/COLOR]
[COLOR=#BB4444]00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|[/COLOR]
[COLOR=#BB4444]00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|[/COLOR]
[COLOR=#BB4444]00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 53 63  |t.............Sc|[/COLOR]
[COLOR=#BB4444]00000190  68 69 6a 66 66 6f 75 74  00 0d 0a 62 6f 6f 74 6d  |hijffout...bootm|[/COLOR]
[COLOR=#BB4444]000001a0  67 72 20 6f 6e 74 62 72  65 65 6b 74 00 0d 0a 62  |gr ontbreekt...b|[/COLOR]
[COLOR=#BB4444]000001b0  6f 6f 74 6d 67 72 20 67  65 63 6f 6d 70 72 69 6d  |ootmgr gecomprim|[/COLOR]
[COLOR=#BB4444]000001c0  65 65 72 64 00 0d 0a 44  72 75 6b 20 43 74 72 6c  |eerd...Druk Ctrl|[/COLOR]
[COLOR=#BB4444]000001d0  2b 41 6c 74 2b 44 65 6c  65 74 65 20 6f 6d 20 6f  |+Alt+Delete om o|[/COLOR]
[COLOR=#BB4444]000001e0  70 6e 69 65 75 77 20 74  65 20 73 74 61 72 74 65  |pnieuw te starte|[/COLOR]
[COLOR=#BB4444]000001f0  6e 0d 0a 00 74 0d 0a 00  8c 99 ad c5 00 00 55 aa  |n...t.........U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]=================== df -Th:[/COLOR]

[COLOR=#BB4444]Filesystem     Type       Size  Used Avail Use% Mounted on[/COLOR]
[COLOR=#BB4444]/cow           overlayfs  2.9G   21M  2.9G   1% /[/COLOR]
[COLOR=#BB4444]udev           devtmpfs   2.9G   12K  2.9G   1% /dev[/COLOR]
[COLOR=#BB4444]tmpfs          tmpfs      589M  820K  588M   1% /run[/COLOR]
[COLOR=#BB4444]/dev/sdb1      vfat       977M  550M  427M  57% /cdrom[/COLOR]
[COLOR=#BB4444]/dev/loop0     squashfs   435M  435M     0 100% /rofs[/COLOR]
[COLOR=#BB4444]none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup[/COLOR]
[COLOR=#BB4444]tmpfs          tmpfs      2.9G  8.0K  2.9G   1% /tmp[/COLOR]
[COLOR=#BB4444]none           tmpfs      5.0M     0  5.0M   0% /run/lock[/COLOR]
[COLOR=#BB4444]none           tmpfs      2.9G     0  2.9G   0% /run/shm[/COLOR]
[COLOR=#BB4444]none           tmpfs      100M   12K  100M   1% /run/user[/COLOR]
[COLOR=#BB4444]/dev/sda1      fuseblk    100M   26M   75M  26% /mnt/boot-sav/sda1[/COLOR]
[COLOR=#BB4444]/dev/sda2      fuseblk    364G  258G  107G  71% /mnt/boot-sav/sda2[/COLOR]
[COLOR=#BB4444]/dev/sda4      fuseblk     24G   23G  994M  96% /mnt/boot-sav/sda4[/COLOR]
[COLOR=#BB4444]/dev/sda5      fuseblk    544G  300M  544G   1% /mnt/boot-sav/sda5[/COLOR]

[COLOR=#BB4444]=================== fdisk -l:[/COLOR]

[COLOR=#BB4444]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/COLOR]
[COLOR=#BB4444]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors[/COLOR]
[COLOR=#BB4444]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512 bytes / 4096 bytes[/COLOR]
[COLOR=#BB4444]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/COLOR]
[COLOR=#BB4444]Disk identifier: 0x3378c8ec[/COLOR]

[COLOR=#BB4444]Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#BB4444]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sda2          206848   763570175   381681664    7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sda3       763570176  1903476735   569953280    f  W95 Ext'[/COLOR]d [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda4      1903476736  1953523711    25023488   27  Hidden NTFS WinRE
/dev/sda5       763572224  1903476735   569952256    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         245     1999871      999813+   6  [COLOR=#B8860B]FAT16[/COLOR]



[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would restore the [COLOR=#666666][([/COLOR]generic mbr[COLOR=#666666])][/COLOR] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s  repair-wubi fix-windows-boot

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.[/COLOR][/TD]
[/TR]
[/TABLE]

``` So can anyone help me with this?

---

### Post by roy4 on 2014-01-16
o yea i forgot to tell: im using dual boot. Windows still work!

---

### Post by ian-weisser on 2014-01-16
I don't see a Ubuntu dual-boot install in that printout.
I see a WUBI install, and a recommendation to fix it that you didn't do.

---

### Post by roy4 on 2014-01-16
> **ian-weisser said:**
> I don't see a Ubuntu dual-boot install in that printout.
I see a WUBI install, and a recommendation to fix it that you didn't do.
Yes it is a wubi install. But what do i need to fix and how?

---

### Post by jeanjd63 on 2014-01-17
Hello

You can try this :
1) you boot in LiveCD/USB
[B]sudo  mkdir  /win  
sudo  mount  /dev/sda2  /win
sudo  fsck  -f -y  /win/ubuntu/disk/root.disk[/B]
2) you reboot

---

### Post by roy4 on 2014-01-17
> **jeanjd63 said:**
> Hello

You can try this :
1) you boot in LiveCD/USB
[B]sudo  mkdir  /win  
sudo  mount  /dev/sda2  /win
sudo  fsck  -f -y  /win/ubuntu/disk/root.disk[/B]
2) you reboot

it doesnt work. i get the following when using the terminal on the demo from the live cd:

```
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
ubuntu@ubuntu:~$ sudo fsck -f -y /win/ubuntu/disk/root.disk
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: No such file or directory while trying to open /win/ubuntu/disk/root.disk
Possibly non-existent device?
ubuntu@ubuntu:~$ 

```

---

### Post by jeanjd63 on 2014-01-17
Where is the wubi install?  /dev/sda2 or other partition ? 
Can you try this :
**sudo  ls  -l  /win/ubuntu**

---

### Post by roy4 on 2014-01-17
> **jeanjd63 said:**
> Where is the wubi install?  /dev/sda2 or other partition ? 
Can you try this :
**sudo  ls  -l  /win/ubuntu**
im now getting this:

```
ubuntu@ubuntu:~$ sudo ls -l /win/ubuntu
total 2456
drwxrwxrwx 1 root root       0 Nov 15 20:58 disks
drwxrwxrwx 1 root root       0 Nov 15 20:46 install
-rwxrwxrwx 2 root root 2510672 Nov 15 20:46 uninstall-wubi.exe
drwxrwxrwx 1 root root    4096 Nov 15 20:58 winboot
ubuntu@ubuntu:~$ 

```

On windows i have installed wubi on C disk. But i dont know whats it called in ubuntu.

---

### Post by roy4 on 2014-01-17
bump

---

### Post by jeanjd63 on 2014-01-18
And now :
**sudo ls -l  /win/ubuntu/disk**

---

### Post by roy4 on 2014-01-18
> **jeanjd63 said:**
> And now :
**sudo ls -l  /win/ubuntu/disk**

im now getting:

```
ubuntu@ubuntu:~$ sudo ls -l /win/ubuntu/disks
total 262144
drwxrwxrwx 1 root root         0 Nov 15 20:46 boot
-rwxrwxrwx 2 root root         0 Jan 16 18:35 root.disk
-rwxrwxrwx 2 root root 268435456 Nov 15 22:00 swap.disk
ubuntu@ubuntu:~$
```

ps: my ubutu install folder is in sda2:

```
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.9G   94M  2.8G   4% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  876K  1.2G   1% /run
/dev/sdb1       973M  861M  112M  89% /cdrom
/dev/loop0      667M  667M     0 100% /rofs
tmpfs           2.9G   12K  2.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            2.9G   80K  2.9G   1% /run/shm
/dev/sda5       544G  300M  544G   1% /media/9E9C5B9F9C5B70AF
**[COLOR=#ff0000]/dev/sda2       364G  262G  103G  72% /win[/COLOR]**
ubuntu@ubuntu:~$
```

---

### Post by jeanjd63 on 2014-01-18
Your root.disk has a zero size. It is anormal. 
I think you have to force a chkdsk of your partition /dev/sda2 under windows

---

### Post by roy4 on 2014-01-18
> **jeanjd63 said:**
> Your root.disk has a zero size. It is anormal. 
I think you have to force a chkdsk of your partition /dev/sda2 under windows
How do i do that?

---

### Post by jeanjd63 on 2014-01-18
At the command prompt type 'CHKDSK /f' and hit OK button. If it says the  volume is in use with an option Y/N to check disk on startup, press Y  and again hit OK or Enter button.
This will always check the disk at startup until disabled by cancelling the scan within the allotted time.

---

### Post by roy4 on 2014-01-18
> **jeanjd63 said:**
> At the command prompt type 'CHKDSK /f' and hit OK button. If it says the  volume is in use with an option Y/N to check disk on startup, press Y  and again hit OK or Enter button.
This will always check the disk at startup until disabled by cancelling the scan within the allotted time.

it still didnt work

afther scanning with CHKDSK /f in windows,  im still getting:

```
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
ubuntu@ubuntu:~$ sudo ls -l /win/ubuntu
total 2456
drwxrwxrwx 1 root root       0 Nov 15 20:58 disks
drwxrwxrwx 1 root root       0 Nov 15 20:46 install
-rwxrwxrwx 2 root root 2510672 Nov 15 20:46 uninstall-wubi.exe
drwxrwxrwx 1 root root    4096 Nov 15 20:58 winboot
ubuntu@ubuntu:~$ sudo ls -l /win/ubuntu/disks
total 262144
drwxrwxrwx 1 root root         0 Nov 15 20:46 boot
**[COLOR=#ff0000]-rwxrwxrwx 2 root root         0 Jan 16 18:35 root.disk[/COLOR]**
-rwxrwxrwx 2 root root 268435456 Nov 15 22:00 swap.disk
ubuntu@ubuntu:~$ 

```

---

### Post by jeanjd63 on 2014-01-19
At this time your root.disk is dead and your install too. 
You can try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") for recover your file but nothing is win

---

