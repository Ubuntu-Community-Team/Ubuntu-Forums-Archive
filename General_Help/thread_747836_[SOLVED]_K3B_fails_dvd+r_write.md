---
title: "[SOLVED] K3B fails dvd+r write"
date: 2008-04-06
forum: General Help
---

### Post by logos34 on 2008-04-06
Now k3b refuses to write dvd+r.  WTF? I just burned a +r disc not too long ago, but i can't read it--every app says it's blank, except K3b which initially showed it partially filled and now says it's blank.  Today I wrote two full dvd**+rw** in k3b just fine, so at least that works.  It gives me something about " LUN appears to be stuck writing LBA".  Never encountered this before.  Everything set for auto, filesystemtype: linux only (no joliet). I',m just trying to backup some ogg music files to blank dvd+r.

Ideas anyone?

> 
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 12.3x1352KBps.
    1605632/4588259328 ( 0.0%) @0.0x, remaining 333:16 RBU 100.0% UBU   2.0%    1605632/4588259328 ( 0.0%) @0.0x, remaining 476:06 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4588259328 ( 0.0%) @0.0x, remaining 618:55 RBU 100.0% UBU 100.0%
    1605632/4588259328 ( 0.0%) @0.0x, remaining 809:22 RBU 100.0% UBU 100.0%
    1605632/4588259328 ( 0.0%) @0.0x, remaining 952:12 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4588259328 ( 0.0%) @0.0x, remaining 1095:01 RBU 100.0% UBU 100.0%
    1605632/4588259328 ( 0.0%) @0.0x, remaining 1285:28 RBU 100.0% UBU 100.0%
    1605632/4588259328 ( 0.0%) @0.0x, remaining 1428:18 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4588259328 ( 0.0%) @0.0x, remaining 1571:07 RBU 100.0% UBU 100.0%
    1605632/4588259328 ( 0.0%) @0.0x, remaining 1761:34 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=310h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2240361 -dvd-compat -speed=12 -overburn -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2240361
I: -input-charset not specified, using utf-8 (detected in locale settings)



---

### Post by logos34 on 2008-04-07
bump

---

### Post by logos34 on 2008-04-08
I really need some help with this.  I need to backup/archive ~25 gb worth of music to dvd.  
If anyone has ANY idea how to fix this, please don't hesitate to post.  

I just tried downgrading to the previous dvd+rw-tools package (7.06, from Feisty), but the version reported is still the latest, 7.1.  AS I say, I cannot seem to burn a dvd+r in any app, neither nautilus-cd-burner, k3b, gomebaker, brasero, etc.  I was able to archive all my previous music to these very same discs in windows (using boith nero and iTunes burners).  I am able to read those discs in linux.  I'm using Memorex 16X dvd+r (actually they're Ricoh).  The drive (Asus DRW-1608P2) has the latest firmware update.  I'm trying to burn to the remaining discs from the very same package as the others, and none work.  (I just hope I haven't made coasters out of all of them trying to get a burn going). 

I can burn burn other formats fine--cd-r, cd-rw, dvd+rw.  I just burned half a dvd+r (multisession) not too long ago.  But now I can't read that particular disc, let alone write a blank one.  What could be the problem?  Faulty media would seem to be out of the question.  I'd really like to avoid having to buy another pack.

---

### Post by logos34 on 2008-04-10
After much fuss it seems the problem was a combination of the media being unable to handle burning at the full speed  and a lens that needed a little cleaning.  The 16x media is 2 years old and is apparently unable to burn and verify at anything other than the slowest speed, 4x.  A dab of isopropyl alchohol with a q-tip enabled me to get a complete burn, but it still resulted in write errors until I lowered the speed.  At least it's not the drive, but I made coasters out of four discs in the process. :(

So the lesson is: clean and slow down!

---

