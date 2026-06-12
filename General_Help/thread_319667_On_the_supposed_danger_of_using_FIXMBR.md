---
title: "On the supposed danger of using FIXMBR"
date: 2006-12-16
forum: General Help
---

### Post by DigitalAxis on 2006-12-16
I'm running a dual-booting Xubuntu/WinXP Pro SP2 system and somehow the bootsector (or FAT, or something) on /dev/hda2 (FAT32, Windows) has been altered.  Not the whole thing, but one of the copies, such that every time I boot Xubuntu it takes forever to do the disk scanning, because every single time fdisk prints out a comparison between the main version and the backup, tells me there's a mismatch, and says "not doing anything about this".  This has begun to really irritate me, because I have a Pentium 4M laptop, and it takes 2 minutes to boot Xubuntu... which is far, far too long.

The solution would seem to be to rewrite the MBR (I use NTLDR to load GRUB, so no problems there) using FIXMBR, but when I get to that step with my Windows XP install CD it warns me that I have a non-standard MBR (unsurprising, since Xubuntu tells me the same thing) but also that changing it might ruin my computer.

So, the question is this:
How safe is using FIXMBR?  Will it correctly identify my partitions, or will it overwrite my partition table with some crazy default?
If so, what steps should I take to save/restore a working partition table?

Alternately, would I be better off just setting up Xubuntu to not scan my windows partition?  And how would I do that?

---

### Post by Herman on 2006-12-16
When the bootsector is not the same as its backup........................................................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")

Hello DigitalAxis,
The filesystem check looks at the bootsector, not the MBR. 

The MBR (Master Boot Record) is located in sector number 0 of the first track of our hard disk, which is always empty. I it is not formatted with any filesystem and it is not part of Windows at all.

Each Partition has a bootsector, I call the first sector of each partition a boot sector. Windows bootsector is commonly the first sector of the next track of the hard disk, there are 63 sectors per track. If your Windows has the FAT32 filesystem, you can restore the Windows bootsector from its backup. Use the link above to see how to do that with Linux.
The Windows command for that would be 'FIXBOOT'.

However, you can run 'FIXMBR' too, it won't hurt anything. Then you can restore Grub to MBR, write Lilo to MBR, then overwrite it with GAG Boot Manager, the FIXMBR again, then re-install Grub...  
as many times as you like. I do those things to my computers day in and day out and I have never worn out a MBR yet. The MBR is just another sector of a hard disk and it's made of the same material as the rest of the hard disk. It will never wear out unless the hard disk has a bearing failure or something like that. :D
I know because I do this kind of thing a lot to keep my website up to date and to experiment with bootloaders so I can learn things to help people with them. 
So don't worry, be happy!  :D

Regards, Herman ;)

---

### Post by DigitalAxis on 2006-12-16
How very odd, I could have sworn I ran dosfdisk on the drive at some point already... Oh well, now I know.

I assume I now need to copy the (mostly empty, apparently) backup to the original...

---

### Post by Herman on 2006-12-16
>  I assume I now need to copy the (mostly empty, apparently) backup to the original... Hmmm, it's 'mostly empty?' :-k

Are you sure? 

If so then maybe you 'd better be careful and think this over a bit first.
Xubuntu/WinXP Pro SP2 system with FAT32 files sytem eh? On on /dev/hda2

You can run one of those commands again that are shown in that link for another look at the bootsector and it's backup and see maybe , and if the backup is really empty, I'd select 3)'take no action' for the time being.
```
 sudo dosfsck  -ar /dev/hda2
```

---

### Post by Herman on 2006-12-16
If it's the backup that's really empty, you might need to copy the original to the backup. You didn't say you are having any problems booting Windows, so I presume now it's the backup that's faulty rather than the original bootsector.

You might be better off using your Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and use the FIXBOOT command instead of doing it from Linux.

And also, if you do get into any problems, How to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/"). That works without a MBR or a bootsector or a boot.ini, NTLDR or NTdetect.com! :D

---

### Post by DigitalAxis on 2006-12-16
I don't quite know why it was only just as I posted this thread that I realized a bootsector on a partition would have no effect on a partition table or Master Boot Record (stored in the first sector of the HARD DRIVE, not a partition, d'oh)...  I guess I had a couple weeks of not thinking about it/brainfart...

Looking at it more carefully now, I notice that there aren't 512 bytes listed, and at most there are a few long runs.  Since I don't know what it's supposed to look like I assume that the backup very well could be right- it's a bootsector for a partition, not an MBR; it could conceivably be 'emptier'.

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  90:33/0e, 91:c9/1f, 92:8e/be, 93:d1/74, 94:bc/7e, 95:f4/ac, 96:7b/22
  , 97:8e/c0, 98:c1/74, 99:8e/06, 100:d9/b4, 101:bd/0e, 102:00/cd, 103:7c/10
  , 104:88/eb, 105:4e/f5, 106:02/b4, 107:8a/00, 108:56/cd, 109:40/16
  , 111:08/00, 113:13/19, 114:73/eb, 115:05/fe, 116:b9/54, 117:ff/68
  , 118:ff/69, 119:8a/73, 120:f1/20, 121:66/70, 122:0f/61, 123:b6/72
  , 124:c6/74, 125:40/69, 126:66/74, 127:0f/69, 128:b6/6f, 129:d1/6e
  , 130:80/20, 131:e2/64, 132:3f/6f, 133:f7/65, 134:e2/73, 135:86/20
  , 136:cd/6e, 137:c0/6f, 138:ed/74, 139:06/20, 140:41/68, 141:66/61
  , 142:0f/76, 143:b7/65, 144:c9/20, 145:66/61, 146:f7/6e, 147:e1/20
  , 148:66/6f, 149:89/70, 150:46/65, 151:f8/72, 152:83/61, 153:7e/74
  , 154:16/69, 155:00/6e, 156:75/67, 157:38/20, 158:83/73, 159:7e/79
  , 160:2a/73, 161:00/74, 162:77/65, 163:32/6d, 164:66/20, 165:8b/6c
  , 166:46/6f, 167:1c/61, 168:66/64, 169:83/65, 170:c0/72, 171:0c/20
  , 172:bb/69, 173:00/6e, 174:80/73, 175:b9/74, 176:01/61, 177:00/6c
  , 178:e8/6c, 179:2b/65, 180:00/64, 181:e9/20, 182:48/6f, 183:03/6e
  , 184:a0/20, 185:fa/69, 186:7d/74, 187:b4/2e, 188:7d/0a, 189:8b/0d
  , 190:f0/50, 191:ac/72, 192:84/65, 193:c0/73, 194:74/73, 195:17/20
  , 196:3c/61, 197:ff/20, 198:74/6b, 199:09/65, 200:b4/79, 201:0e/20
  , 202:bb/74, 203:07/6f, 204:00/20, 205:cd/72, 206:10/65, 207:eb/62
  , 208:ee/6f, 209:a0/6f, 210:fb/74, 211:7d/2e, 212:eb/2e, 213:e5/2e
  , 214:a0/00, 215:f9/00, 216:7d/00, 217:eb/00, 218:e0/00, 219:98/00
  , 220:cd/00, 221:16/00, 222:cd/00, 223:19/00, 224:66/00, 225:60/00
  , 226:66/00, 227:3b/00, 228:46/00, 229:f8/00, 230:0f/00, 231:82/00
  , 232:4a/00, 234:66/00, 235:6a/00, 237:66/00, 238:50/00, 239:06/00
  , 240:53/00, 241:66/00, 242:68/00, 243:10/00, 245:01/00, 247:80/00
  , 248:7e/00, 249:02/00, 251:0f/00, 252:85/00, 253:20/00, 255:b4/00
  , 256:41/00, 257:bb/00, 258:aa/00, 259:55/00, 260:8a/00, 261:56/00
  , 262:40/00, 263:cd/00, 264:13/00, 265:0f/00, 266:82/00, 267:1c/00
  , 269:81/00, 270:fb/00, 271:55/00, 272:aa/00, 273:0f/00, 274:85/00
  , 275:14/00, 277:f6/00, 278:c1/00, 279:01/00, 280:0f/00, 281:84/00
  , 282:0d/00, 284:fe/00, 285:46/00, 286:02/00, 287:b4/00, 288:42/00
  , 289:8a/00, 290:56/00, 291:40/00, 292:8b/00, 293:f4/00, 294:cd/00
  , 295:13/00, 296:b0/00, 297:f9/00, 298:66/00, 299:58/00, 300:66/00
  , 301:58/00, 302:66/00, 303:58/00, 304:66/00, 305:58/00, 306:eb/00
  , 307:2a/00, 308:66/00, 309:33/00, 310:d2/00, 311:66/00, 312:0f/00
  , 313:b7/00, 314:4e/00, 315:18/00, 316:66/00, 317:f7/00, 318:f1/00
  , 319:fe/00, 320:c2/00, 321:8a/00, 322:ca/00, 323:66/00, 324:8b/00
  , 325:d0/00, 326:66/00, 327:c1/00, 328:ea/00, 329:10/00, 330:f7/00
  , 331:76/00, 332:1a/00, 333:86/00, 334:d6/00, 335:8a/00, 336:56/00
  , 337:40/00, 338:8a/00, 339:e8/00, 340:c0/00, 341:e4/00, 342:06/00
  , 343:0a/00, 344:cc/00, 345:b8/00, 346:01/00, 347:02/00, 348:cd/00
  , 349:13/00, 350:66/00, 351:61/00, 352:0f/00, 353:82/00, 354:54/00
  , 355:ff/00, 356:81/00, 357:c3/00, 359:02/00, 360:66/00, 361:40/00
  , 362:49/00, 363:0f/00, 364:85/00, 365:71/00, 366:ff/00, 367:c3/00
  , 368:4e/00, 369:54/00, 370:4c/00, 371:44/00, 372:52/00, 373:20/00
  , 374:20/00, 375:20/00, 376:20/00, 377:20/00, 378:20/00, 428:0d/00
  , 429:0a/00, 430:4e/00, 431:54/00, 432:4c/00, 433:44/00, 434:52/00
  , 435:20/00, 436:69/00, 437:73/00, 438:20/00, 439:6d/00, 440:69/00
  , 441:73/00, 442:73/00, 443:69/00, 444:6e/00, 445:67/00, 446:ff/00
  , 447:0d/00, 448:0a/00, 449:44/00, 450:69/00, 451:73/00, 452:6b/00
  , 453:20/00, 454:65/00, 455:72/00, 456:72/00, 457:6f/00, 458:72/00
  , 459:ff/00, 460:0d/00, 461:0a/00, 462:50/00, 463:72/00, 464:65/00
  , 465:73/00, 466:73/00, 467:20/00, 468:61/00, 469:6e/00, 470:79/00
  , 471:20/00, 472:6b/00, 473:65/00, 474:79/00, 475:20/00, 476:74/00
  , 477:6f/00, 478:20/00, 479:72/00, 480:65/00, 481:73/00, 482:74/00
  , 483:61/00, 484:72/00, 485:74/00, 486:0d/00, 487:0a/00, 505:ac/00
  , 506:bf/00, 507:cc/00

```

There's a preponderance of bytes in there that should be zero, that's what I meant.  But it probably means nothing.

EDIT: I've already used FIXBOOT; it didn't do anything really.  It probably replaced the hard drive bootsector (on /dev/hda), which wouldn't do anything to the bootsector on /dev/hda2...  And no, I have no problems running Windows, at least that I know of.

---

### Post by Herman on 2006-12-16
I'll just nuke one of my Windows XP bootsectors in a test computer with a 'dd' command for you so I can get a look at another output to compare yours to, I won't be long, sorry to be keeping you waiting...

---

### Post by DigitalAxis on 2006-12-16
Wow, thanks!

I hope they save this thread for posterity so that nobody needs to go do that again.

---

### Post by Herman on 2006-12-16
No problem, actually I couldn't exactly think of the right 'dd' command so I found it easier to remember how to hose it by installing Grub to it instead.
Here it is,
```
herman@testedgyeftbeta:~$ sudo dosfsck /dev/hda1
Password:
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda1: 30770 files, 370286/460749 clusters
herman@testedgyeftbeta:~$ sudo grub-install /dev/hda1
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
(hd1)   /dev/hdb
herman@testedgyeftbeta:~$ sudo dosfsck /dev/hda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  1:48/58, 62:03/00, 63:02/00, 64:ff/80, 66:00/29, 67:80/f0, 68:46/16
  , 69:40/29, 70:c9/26, 71:05/4e, 72:00/4f, 73:08/20, 74:fa/4e, 75:90/41
  , 76:90/4d, 77:f6/45, 78:c2/20, 79:80/20, 80:75/20, 81:02/20, 82:b2/46
  , 83:80/41, 84:ea/54, 85:59/33, 86:7c/32, 87:00/20, 88:00/20, 89:31/20
  , 90:c0/33, 91:8e/c9, 92:d8/8e, 93:8e/d1, 94:d0/bc, 95:bc/f4, 96:00/7b
  , 97:20/8e, 98:fb/c1, 99:a0/8e, 100:40/d9, 101:7c/bd, 102:3c/00, 103:ff/7c
  , 104:74/88, 105:02/4e, 106:88/02, 107:c2/8a, 108:52/56, 109:be/40
  , 110:7f/b4, 111:7d/08, 112:e8/cd, 113:34/13, 114:01/73, 115:f6/05
  , 116:c2/b9, 117:80/ff, 118:74/ff, 119:54/8a, 120:b4/f1, 121:41/66
  , 122:bb/0f, 123:aa/b6, 124:55/c6, 125:cd/40, 126:13/66, 127:5a/0f
  , 128:52/b6, 129:72/d1, 130:49/80, 131:81/e2, 132:fb/3f, 133:55/f7
  , 134:aa/e2, 135:75/86, 136:43/cd, 137:a0/c0, 138:41/ed, 139:7c/06
  , 140:84/41, 141:c0/66, 142:75/0f, 143:05/b7, 144:83/c9, 145:e1/66
  , 146:01/f7, 147:74/e1, 148:37/66, 149:66/89, 150:8b/46, 151:4c/f8
  , 152:10/83, 153:be/7e, 154:05/16, 155:7c/00, 156:c6/75, 157:44/38
  , 158:ff/83, 159:01/7e, 160:66/2a, 161:8b/00, 162:1e/77, 163:44/32
  , 164:7c/66, 165:c7/8b, 166:04/46, 167:10/1c, 168:00/66, 169:c7/83
  , 170:44/c0, 171:02/0c, 172:01/bb, 174:66/80, 175:89/b9, 176:5c/01
  , 177:08/00, 178:c7/e8, 179:44/2b, 180:06/00, 181:00/e9, 182:70/48
  , 183:66/03, 184:31/a0, 185:c0/fa, 186:89/7d, 187:44/b4, 188:04/7d
  , 189:66/8b, 190:89/f0, 191:44/ac, 192:0c/84, 193:b4/c0, 194:42/74
  , 195:cd/17, 196:13/3c, 197:72/ff, 198:05/74, 199:bb/09, 200:00/b4
  , 201:70/0e, 202:eb/bb, 203:7d/07, 204:b4/00, 205:08/cd, 206:cd/10
  , 207:13/eb, 208:73/ee, 209:0a/a0, 210:f6/fb, 211:c2/7d, 212:80/eb
  , 213:0f/e5, 214:84/a0, 215:ea/f9, 216:00/7d, 217:e9/eb, 218:8d/e0
  , 219:00/98, 220:be/cd, 221:05/16, 222:7c/cd, 223:c6/19, 224:44/66
  , 225:ff/60, 226:00/66, 227:66/3b, 228:31/46, 229:c0/f8, 230:88/0f
  , 231:f0/82, 232:40/4a, 233:66/00, 234:89/66, 235:44/6a, 236:04/00
  , 237:31/66, 238:d2/50, 239:88/06, 240:ca/53, 241:c1/66, 242:e2/68
  , 243:02/10, 244:88/00, 245:e8/01, 246:88/00, 247:f4/80, 248:40/7e
  , 249:89/02, 250:44/00, 251:08/0f, 252:31/85, 253:c0/20, 254:88/00
  , 255:d0/b4, 256:c0/41, 257:e8/bb, 258:02/aa, 259:66/55, 260:89/8a
  , 261:04/56, 262:66/40, 263:a1/cd, 264:44/13, 265:7c/0f, 266:66/82
  , 267:31/1c, 268:d2/00, 269:66/81, 270:f7/fb, 271:34/55, 272:88/aa
  , 273:54/0f, 274:0a/85, 275:66/14, 276:31/00, 277:d2/f6, 278:66/c1
  , 279:f7/01, 280:74/0f, 281:04/84, 282:88/0d, 283:54/00, 284:0b/fe
  , 285:89/46, 286:44/02, 287:0c/b4, 288:3b/42, 289:44/8a, 290:08/56
  , 291:7d/40, 292:3c/8b, 293:8a/f4, 294:54/cd, 295:0d/13, 296:c0/b0
  , 297:e2/f9, 298:06/66, 299:8a/58, 300:4c/66, 301:0a/58, 302:fe/66
  , 303:c1/58, 304:08/66, 305:d1/58, 306:8a/eb, 307:6c/2a, 308:0c/66
  , 309:5a/33, 310:8a/d2, 311:74/66, 312:0b/0f, 313:bb/b7, 314:00/4e
  , 315:70/18, 316:8e/66, 317:c3/f7, 318:31/f1, 319:db/fe, 320:b8/c2
  , 321:01/8a, 322:02/ca, 323:cd/66, 324:13/8b, 325:72/d0, 326:2a/66
  , 327:8c/c1, 328:c3/ea, 329:8e/10, 330:06/f7, 331:48/76, 332:7c/1a
  , 333:60/86, 334:1e/d6, 335:b9/8a, 336:00/56, 337:01/40, 338:8e/8a
  , 339:db/e8, 340:31/c0, 341:f6/e4, 342:31/06, 343:ff/0a, 344:fc/cc
  , 345:f3/b8, 346:a5/01, 347:1f/02, 348:61/cd, 349:ff/13, 350:26/66
  , 351:42/61, 352:7c/0f, 353:be/82, 354:85/54, 355:7d/ff, 356:e8/81
  , 357:40/c3, 359:eb/02, 360:0e/66, 361:be/40, 362:8a/49, 363:7d/0f
  , 364:e8/85, 365:38/71, 366:00/ff, 367:eb/c3, 368:06/4e, 369:be/54
  , 370:94/4c, 371:7d/44, 372:e8/52, 373:30/20, 374:00/20, 375:be/20
  , 376:99/20, 377:7d/20, 378:e8/20, 379:2a/00, 381:eb/00, 382:fe/00
  , 383:47/00, 384:52/00, 385:55/00, 386:42/00, 387:20/00, 389:47/00
  , 390:65/00, 391:6f/00, 392:6d/00, 394:48/00, 395:61/00, 396:72/00
  , 397:64/00, 398:20/00, 399:44/00, 400:69/00, 401:73/00, 402:6b/00
  , 404:52/00, 405:65/00, 406:61/00, 407:64/00, 409:20/00, 410:45/00
  , 411:72/00, 412:72/00, 413:6f/00, 414:72/00, 416:bb/00, 417:01/00
  , 419:b4/00, 420:0e/00, 421:cd/00, 422:10/00, 423:ac/00, 424:3c/00
  , 426:75/00, 427:f4/00, 428:c3/0d, 429:00/0a, 430:00/4e, 431:00/54
  , 432:00/4c, 433:00/44, 434:00/52, 435:00/20, 436:00/69, 437:00/73
  , 438:00/20, 439:00/6d
1) Copy original to backup
2) Copy backup to original
3) No action
? 


```It looks to me as if my backup, which in my case is the correct copy, has more in common with your original, but you should take a good look and decide for yourself too.

I'd guess you should choose 1) copy the original to your backup.

I'll be choosing 2) copy the backup to the original, because there's no doubt in my case which is the correct copy.

Do you have a Windows 'Install' CD for a 'Recovery Console?' I only have 'Restore' CDs, they don't have that feature, so I use Linux for this. (Not that I ever really need to do this in real life, I just like doing experiments, that's the only reason I do things like this.)

---

### Post by DigitalAxis on 2006-12-16
Problem solved! (mostly)

Windows boots fine
Xubuntu boots, but still takes two minutes.  Hopefully it just took a long time to run fdisk this time because something was different...

Thank you, Herman.  I figured I'd have to wait a few days after I'd gone away for Christmas...  but it's already fixed.

---

### Post by Herman on 2006-12-16
Here's another view, since your differences don't begin until byte 90, I copied from byte 90 down a ways on mine and pasted it under the top several lines of yours to make it easier to compare.

DigitalAxis
   ```
 90:33/0e, 91:c9/1f, 92:8e/be, 93:d1/74, 94:bc/7e, 95:f4/ac, 96:7b/22
  , 97:8e/c0, 98:c1/74, 99:8e/06, 100:d9/b4, 101:bd/0e, 102:00/cd, 103:7c/10
  , 104:88/eb, 105:4e/f5, 106:02/b4, 107:8a/00, 108:56/cd, 109:40/16
  , 111:08/00, 113:13/19, 114:73/eb, 115:05/fe, 116:b9/54, 117:ff/68
  , 118:ff/69, 119:8a/73, 120:f1/20, 121:66/70, 122:0f/61, 123:b6/72
  , 124:c6/74, 125:40/69, 126:66/74, 127:0f/69, 128:b6/6f, 129:d1/6e
  , 130:80/20, 131:e2/64, 132:3f/6f, 133:f7/65, 134:e2/73, 135:86/20
  , 136:cd/6e, 137:c0/6f, 138:ed/74, 139:06/20, 140:41/68, 141:66/61
  , 142:0f/76, 143:b7/65, 144:c9/20, 145:66/61, 146:f7/6e, 147:e1/20
  , 148:66/6f, 149:89/70, 150:46/65, 151:f8/72, 152:83/61, 153:7e/74
  , 154:16/69, 155:00/6e, 156:75/67, 157:38/20, 158:83/73, 159:7e/79
  , 160:2a/73, 161:00/74, 162:77/65, 163:32/6d, 164:66/20, 165:8b/6c
  , 166:46/6f, 167:1c/61, 168:66/64, 169:83/65, 170:c0/72, 171:0c/20

```   herman
 ```
 , 90:c0/33, 91:8e/c9, 92:d8/8e, 93:8e/d1, 94:d0/bc, 95:bc/f4, 96:00/7b
  , 97:20/8e, 98:fb/c1, 99:a0/8e, 100:40/d9, 101:7c/bd, 102:3c/00, 103:ff/7c
  , 104:74/88, 105:02/4e, 106:88/02, 107:c2/8a, 108:52/56, 109:be/40
  , 110:7f/b4, 111:7d/08, 112:e8/cd, 113:34/13, 114:01/73, 115:f6/05
  , 116:c2/b9, 117:80/ff, 118:74/ff, 119:54/8a, 120:b4/f1, 121:41/66
  , 122:bb/0f, 123:aa/b6, 124:55/c6, 125:cd/40, 126:13/66, 127:5a/0f
  , 128:52/b6, 129:72/d1, 130:49/80, 131:81/e2, 132:fb/3f, 133:55/f7
  , 134:aa/e2, 135:75/86, 136:43/cd, 137:a0/c0, 138:41/ed, 139:7c/06
  , 140:84/41, 141:c0/66, 142:75/0f, 143:05/b7, 144:83/c9, 145:e1/66
  , 146:01/f7, 147:74/e1, 148:37/66, 149:66/89, 150:8b/46, 151:4c/f8
  , 152:10/83, 153:be/7e, 154:05/16, 155:7c/00, 156:c6/75, 157:44/38
  , 158:ff/83, 159:01/7e, 160:66/2a, 161:8b/00, 162:1e/77, 163:44/32
  , 164:7c/66, 165:c7/8b, 166:04/46, 167:10/1c, 168:00/66, 169:c7/83

 
```Now, remembering that I know for sure my backup is okay and you think it might be your original that might be okay, 
yours shows '90:33/0e' where mine shows '90:c0/33'.
Yours shows '91:c9/1f' where mine shows '91:8e/c9'.
Yours shows '92:8e/be' where mine shows '92:d8/8e', and so on.

That's why I think you can probably do 1) copy original to backup.
> Problem solved! (mostly)

Windows boots fine
Xubuntu boots, but still takes two minutes. Hopefully it just took a long time to run fdisk this time because something was different...

Thank you, Herman.  I figured I'd have to wait a few days after I'd gone away for Christmas...  but it's already fixed.                                                                                                                               Oh, you did it already! Good. :D

---

### Post by bodhi.zazen on 2006-12-16
Off topic:

I can see there is a serious conversation going on here, but IMO the "supposed danger of using FIXMBR" is that it restores windows :p

---

### Post by Herman on 2006-12-16
He-he, well I guess you're right there. :D

It shows how good Ubuntu is when we can even use it to fix Windows with eh? ;)

Regards, Herman :D

---

