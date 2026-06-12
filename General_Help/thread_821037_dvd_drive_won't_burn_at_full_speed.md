---
title: "dvd drive won't burn at full speed"
date: 2008-06-06
forum: General Help
---

### Post by logos34 on 2008-06-06
this is a real drag.  My 16x dvd drive burns coasters at full speed.  Fails error check or dies before burn is complete.  Worked fine with k3b until recently, except that it only burns 16x media at 12x max for some reason.  Now I can only seem to burn 4x max without errors.  4x dvd+rw still burn fine, but that's neither here nor there.  

So after cleaning the lens and burning yet another coaster,  I figured it must be the media--2 yr old Memorex gone bad.  Got some new Verbatim 16x dvd+r, but K3b can't even get more than half way into the burn!

It can't be the media.  The firmware is up-to-date. 

How can I fix it?

---

### Post by mc4man on 2008-06-06
knowing you use wine why don't you test with imgburn
2.2.0 works great, 2.4.1 works great also (can lose app window if you rotate desktop - burn continues though - may be .dll fix)
personally I think no linux iso creator / burner comes even close
[http://www.imgburn.com/](http://www.imgburn.com/)
[http://www.brothersoft.com/imgburn-75901.html](http://www.brothersoft.com/imgburn-75901.html) - 2.2.0

---

### Post by VMC on 2008-06-06
When I had problems like this, I booted up Windows and used Nero Tools. I found out the drive itself was the problem. I just wanted to make sue it wasn't the OS causing my problem. I don't think Wine works with Nero tools as it needs to run at the hardware level.

Then again, your DVD-RW's burn okay. Another thing I notice on a drive I had. When I upgraded it I had bad burns. Usually the upgrade from burners is just to allow more media to burn. In doing so they messed up my current medea. I re-flashed back to factory firmware and left it alone.

---

### Post by logos34 on 2008-06-06
it spins up and down for a few minutes, then reports some stiff about 'LUN'(?), then appears to be ok for a while, but dies half way

here's the debug:

> System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-16-rt
Devices
-----------------------
ASUS DRW-1608P2 1.41 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 2281398 (4672303104 bytes)
Pipe throughput: 2584096768 bytes read, 2584076288 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 12.3x1352KBps.
    1605632/4672303104 ( 0.0%) @0.0x, remaining 193:55 RBU 100.0% UBU   2.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 387:51 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4672303104 ( 0.0%) @0.0x, remaining 533:18 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 678:45 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 872:41 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1018:07 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1163:34 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1357:30 RBU 100.0% UBU 100.0%
[COLOR="Red"]:-? the LUN appears to be stuck writing LBA=310h, keep retrying in 47ms[/COLOR]
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1502:57 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1648:24 RBU 100.0% UBU 100.0%
    1605632/4672303104 ( 0.0%) @0.0x, remaining 1842:19 RBU 100.0% UBU 100.0%
   19496960/4672303104 ( 0.4%) @3.9x, remaining 163:04 RBU 100.0% UBU  71.4%
   48136192/4672303104 ( 1.0%) @6.2x, remaining 70:26 RBU 100.0% UBU  67.3%
   78479360/4672303104 ( 1.7%) @6.6x, remaining 46:49 RBU 100.0% UBU  71.4%
  110592000/4672303104 ( 2.4%) @7.0x, remaining 35:03 RBU 100.0% UBU  73.5%
  141656064/4672303104 ( 3.0%) @6.7x, remaining 28:47 RBU 100.0% UBU  71.4%
  174882816/4672303104 ( 3.7%) @7.2x, remaining 24:51 RBU 100.0% UBU  71.4%
  207126528/4672303104 ( 4.4%) @7.0x, remaining 21:55 RBU 100.0% UBU  81.6%

...

 2037841920/4672303104 (43.6%) @10.8x, remaining 4:23 RBU 100.0% UBU  53.1%
 2089943040/4672303104 (44.7%) @11.3x, remaining 4:17 RBU  99.7% UBU  36.7%
 2145189888/4672303104 (45.9%) @12.0x, remaining 4:08 RBU 100.0% UBU  57.1%
 2197716992/4672303104 (47.0%) @11.4x, remaining 4:00 RBU  97.7% UBU  51.0%
 2251653120/4672303104 (48.2%) @11.7x, remaining 3:54 RBU  99.7% UBU  51.0%
 2305851392/4672303104 (49.4%) @11.7x, remaining 3:46 RBU 100.0% UBU  53.1%
 2360213504/4672303104 (50.5%) @11.8x, remaining 3:39 RBU 100.0% UBU  38.8%
 2416214016/4672303104 (51.7%) @12.1x, remaining 3:32 RBU 100.0% UBU  51.0%
 2469756928/4672303104 (52.9%) @11.6x, remaining 3:26 RBU 100.0% UBU  51.0%
 2511175680/4672303104 (53.7%) @9.0x, remaining 3:21 RBU 100.0% UBU  55.1%
 2546597888/4672303104 (54.5%) @7.7x, remaining 3:18 RBU 100.0% UBU  71.4%
[COLOR="Red"]:-[ WRITE@LBA=130080h failed with SK=4h/ASC=44h/ACQ=4Bh]: Input/output error
:-( write failed: Input/output error[/COLOR]
/dev/hdc: flushing cache
/dev/hdc: closing track
[COLOR="Red"]:-[ CLOSE TRACK failed with SK=4h/ASC=44h/ACQ=D6h]: Input/output error
/dev/hdc: closing disc
:-[ CLOSE DISC failed with SK=4h/ASC=44h/ACQ=D6h]: Input/output error[/COLOR]

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2281398 -dvd-compat -speed=12 -use-the-force-luke=bufsize:32m 

...




---

### Post by logos34 on 2008-06-06
> **mc4man said:**
> knowing you use wine why don't you test with imgburn


I'm not burning images--does it do just data dvd?

[EDIT: nm--it does, just checked.  I'm downloading it now]

---

### Post by logos34 on 2008-06-06
> **VMC said:**
> When I had problems like this, I booted up Windows and used Nero Tools. 

...

 Another thing I notice on a drive I had. When I upgraded it I had bad burns. Usually the upgrade from burners is just to allow more media to burn. In doing so they messed up my current medea.

yeah, I used Nero in windows to burn a bunch of 16x dvd's 2 yrs ago.  Same firmware version (hasn't changed since--maybe that's good in light of what you said). 

As I said I've used k3b before (just been a while) to burn 16x media, the only problem being it only goes as high as 12x (auto setting).  k3b disc info correctly ids the media -- 4x, 8x, 12x 16x capable.  (manufactuer: MCC/004, which is high-quality stuff I hear)

It's probably the drive.  I guess all is not lost if only it will continue to burn at 4x error free

---

### Post by mc4man on 2008-06-06
> does it do just data dvd
to some extent - you can add any type and combo of files and folders to a build that would then either be built as an iso and burned or burned on the fly. The limitation would be the disk is always finalized. ( no multisession)
I was thinking more as a test, the settings options and burn log are extensive/ verbose. 
 OT> It also reads (copies), and does boot, bin/cd, ect.ect. And as far as dual layer no peer (in regards to DVD Video)

edit at a slow moment go to website and ck. out change log for last version or so.

---

### Post by cariboo on 2008-06-06
There is a Nero-for-Linux available from Nero's web site. The only thing you need is a Nero serial number.

Jim

---

### Post by VMC on 2008-06-06
> **mc4man said:**
> knowing you use wine why don't you test with imgburn
2.2.0 works great, 2.4.1 works great also (can lose app window if you rotate desktop - burn continues though - may be .dll fix)
personally I think no linux iso creator / burner comes even close
[http://www.imgburn.com/](http://www.imgburn.com/)
[http://www.brothersoft.com/imgburn-75901.html](http://www.brothersoft.com/imgburn-75901.html) - 2.2.0

This is great news to me. ImgBurn was my favorite after Nero decided to include the "kitchen sink" on the newer releases. There huge.

And yes ImgBurn will burn data and anything else you throw at it. I also like the verify feature

---

### Post by logos34 on 2008-06-06
K3b has worked so well for me otherwise...I thought it was the best (it's the best native linux burner app at least).  It would really disappoint me if that was the issue (but I'd rather that than the drive). To tell the truth I'm trying to avoid using proprietary stuff (Linux Nero) and stuff on wine if I can help it.  But I'd really like to nail this problem down, so I guess tomorrow I'll try one more full speed burn with ImgBurn.  If it doesn't work it's gotta be the drive

---

### Post by mc4man on 2008-06-06
@vmc set at win nt 4.0 I'm using 2.4.1, gotta look into the flip desktop issue. 
The booktype feature doesn't work in wine but if the drive (if compatible) had been set in windows then it continues to set dvd+r/ dvd9 to dvd-rom

---

### Post by VMC on 2008-06-06
> **logos34 said:**
> K3b has worked so well for me otherwise...I thought it was the best (it's the best native linux burner app at least).  It would really disappoint me if that was the issue (but I'd rather that than the drive). To tell the truth I'm trying to avoid using proprietary stuff (Linux Nero) and stuff on wine if I can help it.  But I'd really like to nail this problem down, so I guess tomorrow I'll try one more full speed burn with ImgBurn.  If it doesn't work it's gotta be the drive

Nero came with all my drives. Of course I have to use that version with that drive.

Regarding ImgBurn. I just downloaded, and I got some errors. I think I know the problem. The Imgburn log file had this to say:
I 19:11:07 ImgBurn Version 2.4.1.0 started!
I 19:11:08 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 2)
I 19:11:08 Total Physical Memory: 2,074,152 KB  -  Available: 1,775,736 KB
I 19:11:08 Initialising SPTI...
I 19:11:08 Searching for SCSI / ATAPI devices...
W 19:11:08 No devices detected!

These two files were mentioned:mfc42.dll and msvcp60.dll
I'm not sure about the above two file, but this location tells about needing "WNASPI32.DLL": [http://ubuntuforums.org/showpost.php?p=4210199&postcount=5](http://ubuntuforums.org/showpost.php?p=4210199&postcount=5)

I found this and it fixed Imgburn. It least so far. I'll have to play with it and see how well it works:
[http://forum.videohelp.com/topic343950.html](http://forum.videohelp.com/topic343950.html)

---

### Post by mc4man on 2008-06-06
> mfc42.dll and msvcp60.dll I have those 2 in system32 (along with about 5 others (mainly for dvd-rb) - i don't think any are needed as dll overrides - will check. Did you try setting os to nt 4.0
if you need i post dll versions of above that i know work

edit didn't read link
these are the most useful additional dlls for some dvd related stuff
mfc42.dll, msvcp60.dll, advpack.dll, asycfilt.dll, comcat.dll, msvbvm60.dll, oleaut32.dll, olepro32.dll, stdole2.tlb.

The one thing i don't like about 2.4.1 is i think the default build mode is to write to device, i always prefer to build then burn. (virtually no bad burns ever with good media) To change (one way or the other) tools -> settings -> events -> on start up,

---

### Post by logos34 on 2008-06-07
well, ImgBurn fails too around 54% into the burn...sht

Tried it again at 4x.  Burn finished, but there were so many sector errors in the middle portion I finally had to kill verify

So I guess the drive has about had it.  piece of sht.

did I say sht?

---

### Post by VMC on 2008-06-07
You said it was working at 4x, now its now? Or is it that it fails at 4x using ImgBurn?
Also, I think you said that you haven't updated your flash on the drive, correct?

That's usually the reason for the upgrades. For the newer media. It won't hurt now to flash the firmware since it sounds like it going bad anyway. Just get the latest firware and try it. Can't hurt. 

Go here for help : [http://forum.rpc1.org/](http://forum.rpc1.org/)

---

### Post by logos34 on 2008-06-07
sorry, I didn't make myself clear.

The firmware is up-to-date (v.1.41 is the latest on the Asus site), which hasn't changed in 2 years.

Update: since k3b worked before at 4x, I went back and tried it again.  Success. Verified.  Why the errors in ImgBurn at same speed I have no idea.  

As long as it continues to work in k3b at 4x, I'll settle for that.

As a consolation to myself, it's interesting to note that when you burn at 16x, that's only the peak speed reached (somewhere past the middle), not the average speed.  It starts out and ends much slower.  In fact when I used ImgBurn I sat there and watched the speed up to the fail point.  It never got higher than ~11x.  (it was set at default 'auto [max]').  So I could really care less anymore, especially when verification is factored in, which still takes the same time.  

So it's not the end of the world...only made about half a dozen coasters all told (few bucks worth). At least I don't have to start shopping for a dvd burner just yet.

thanks everyone

---

### Post by marcellux on 2010-02-06
same problem here! I tried following; set not the speed at "auto", set it at 2X! it takes a lonnnng time but you will get no error messages!!

---

