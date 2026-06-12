---
title: "Watching Movie/DVD not working anymore"
date: 2008-07-03
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-07-03
Hi @ all.
I wanted to watch a movie tonight, but guess what. It's not working anymore. :confused:
It's been a while since I last watched a DVD on my laptop. So, I can't really say if that is due to an update because there have been a few since the last movie. Usually I watch DVD's with VLC. But the player is just opening the video for a fraction of a second and that's it. With another DVD I tried VLC is simply closing.
So, I thought, I'm smart and just use another player. Might be a bug in the current installed VLC version. I tried Kaffeine but no luck either. It tells me something about maybe not having rights. (See attached screen shot)

Hello? I haven't changed any settings, how can I not have the rights to play this DVD? :confused:
Can anyone help me to get the DVD players back? I wanna watch a video... 
:popcorn: is ready, but at the moment all I can do is cover them with :cry:

---

### Post by Linux&amp;Gsus on 2008-07-04
No one any idea? :(
Anyways, I figured out that it seems to be Region Code specific. I have DVD's from 3 different regions but only the Australian ones are working. I thought VLC doesn't care about the Region Code? Do I miss something?? :confused:

But really, all I want, for crying out load, is to watch the movies I legally bought in DVD stores. :mad:

Anyone know what I'm doing wrong here? I mean, I worked before, no warning about Region Code lock in or anything. It just stopped playing the DVD's.

---

### Post by llib1234 on 2008-07-04
Try go to Medibuntu repo and download dvdcss which will decrypt the commercial encrypted movies.
If that doesn't work then I don't know

---

### Post by Linux&amp;Gsus on 2008-07-04
Well, as I said in my 2nd post, it does work. But only DVD's with a specific Region Code. Actually it took me a while to figure that out. But that's really it.
So, how do I get VLC, or any other player for that matter, to play DVD's from all regions again?

Thanks anyways.

---

### Post by dacorr on 2008-07-04
i had this problem too...

all i did was check the /etc/fstab

terminal type sudo gedit /etc/fstab

and for the DVD drive entry check for UDF or something similar

i removed it and it worked.

Dac

---

### Post by Linux&amp;Gsus on 2008-07-04
So, that's the entry here: 

```
/dev/scd0   /media/cdrom0   udf,iso9660   user,noauto,exec  0         0
```

I assume you mean to only erase the "udf" entry, not the rest of the line. Do I need to reboot afterwards or do anything else before I can test it and be sure about the results?

Oh boy, get the :popcorn: ready...

---

### Post by dacorr on 2008-07-04
yup UDF

i don't remember if i restarted, it should not need it as long as there is no disk in the drive when you do it.

When you insert a disk it will use the fstab to mount it.

Dac

---

### Post by jocko on 2008-07-04
Just delete "udf," from that line (although I'm not sure what that does... ).
The new settings should be used next time you insert a dvd, no need to reboot.

I remember when I used windows I could see in the properties for my dvd drive "The dvd region will be locked after 5 more disks" or something like that. And when it was locked I upgraded the firmware in the drive (because of some other problem) and it got unlocked again. So I guessed the dvd region code specificity was set by the actual dvd drive, not in the software or operative system... But I may be wrong.

---

### Post by dacorr on 2008-07-04
UDF stands for Universal Disk Format. It is essential a filesystem for optical media.

With it in the fstab it is telling ubuntu that this is the file system. Resulting in it tying to read italian when it is written in german because the fstab says its italian.

Dac

---

### Post by Linux&amp;Gsus on 2008-07-04
OK, I deleted UDF, popped in a DVD but still not working. Region 4 DVD's are, but not Region 2.
I even double checked the fstab, no more UDF entry.

Any more tricks?

---

### Post by dacorr on 2008-07-04
what region code is your DVD drive?

---

### Post by Linux&amp;Gsus on 2008-07-04
How would I find that out? Besides, shouldn't VLC ignore that, anyways? I haven't been in Windows for quite a while, but as far as I remember there should be at least 1 more change left over. If not even 2.

Well, anyways, is there a way I can check what's it set to at the moment?

---

### Post by solitaire on 2008-07-04
Stick in a DVD and open a terminal window and try the following command "regionset"
```
sol@europa:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:

```

---

### Post by dacorr on 2008-07-04
from terminal use regionset

be warned you can only change it a limited amount of times.

i would see if i can rip the dvd to hard drive,

Dac

---

### Post by Linux&amp;Gsus on 2008-07-04
Region 4, 2 changes left...

```
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 2
drive plays discs from region(s): 4, mask=0xF7

Would you like to change the region setting of your drive? [y/n]:n
```

OK, so, I could change it here a couple more times. But still, AFAIK VLC should ignore that. Region lock in is a no-no since have different DVD's and putting them on HD, well besides that I don't know how to do that (isn't that embaracing??) I simply don't have the space to have all of them on my HD. It's a laptop. So, space is always a bit limited, compared to a desktop, anyways.

---

### Post by dacorr on 2008-07-04
external DVD maybe, internal region 2 external region 4?

---

### Post by Linux&amp;Gsus on 2008-07-04
Nice try, but then I need 2 external drives. I have DVD's from 3 different regions. (Region 2,3 and 4). There must be another solution.

---

### Post by solitaire on 2008-07-04
You might need to get new firmware for the drive to make it region free.

---

### Post by Linux&amp;Gsus on 2008-07-04
Sounds like that would be a hacked firmware...?

---

### Post by mc4man on 2008-07-04
first put back the udf in fstab - that's not your problem. Run ```
sudo lshw -C disk
``` to get name, model of your drive. If it's a Matshita drive then you are out of luck as far as playing titles from a region other than the one the drive is set for. This is a known 'feature' of these drives, when a region mismatch occurs the _drive will not allow access _to encrypted sectors, ie. no playback. There is no regionfree firmware for most laptop models. You could ck. here [http://forum.rpc1.org/index.php](http://forum.rpc1.org/index.php)
_If it's not a Matshita drive_ you should be able to get playback from regions other than what the drive is set for. I'd open vlc from the terminal, try to open the disk and see what errors show up.

---

### Post by Linux&amp;Gsus on 2008-07-04
Well, who would have guessed it...

```
lshw -C disk
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-841S
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```


VLC from command line looks like this:

```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: GONE_IN_60_SECONDS
libdvdnav: DVD Serial Number: 39EB4D9D
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/john/.dvdnav/GONE_IN_60_SECONDS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000026e
libdvdread: Elapsed time 0
etc
etc
etc
libdvdread: Found 31 VTS's
libdvdread: Elapsed time 6
[00000288] main playlist: nothing to play
[00000288] main playlist: stopping playback
```

That doesn't really tell me anything. :confused:
I assume it's checking all the available (video?) files on the disk. But then nothing to play even though found 31 files?

---

### Post by mc4man on 2008-07-04
> product: DVD-RAM UJ-841S
       vendor: MATSHITA

> when a region mismatch occurs the drive will not allow access to encrypted sectors
As I mentioned with MATSHITA you can't playback titles from a region other than what is set on the drive, period. The reason vlc can 'see' the disk is the .ifo's aren't encrypted, playback (or ripping) of the encrypted sectors is not going to happen.

Edit; a quick search shows no rpc1 firmware available for that drive. MATSHITA are the worst and unfortunately the most common laptop drive

---

### Post by Linux&amp;Gsus on 2008-07-04
If so, why then have I been able to play DVD's from different regions earlier?

I guess I don't really understand that. Not that I don't want to believe the Matshita issue. But I definitely played DVD's from different regions. And the earlier mentioned "regionset" wasn't even installed. So, no way I could have even accidentally messed with the settings.

---

### Post by mc4man on 2008-07-04
> If so, why then have I been able to play DVD's from different regions earlier
If the titles didn't/don't have RCE protection ( or are all region titles) then the drive will allow access. If they do (most recent mainstream titles) then it won't.
Side note: you have changed the region 2 times from an orig. setting. You get 5 to start - one is used to orig. set and you've changed it twice from there.

---

### Post by Linux&amp;Gsus on 2008-07-04
I changed that in Windows not in Linux. And I haven't changed anything in Windows for a while. I can't even remember when I booted Win last time, specially to watch a movie.

Besides, movies that did play before in Linux with VLC don't play any longer. This is the drama I have with it. It did work, nothing changed since then, now it doesn't work.

---

### Post by mc4man on 2008-07-04
I think we're beating a dead horse here, If you find a way to play _that disk with that drive with the current region mismatch_ I'd love to know. here's a post i just found from the author of anydvd concerning Matshita drives (nothings changed since then)(for the most part you could substitute anydvd with vlc in the comments)
[http://club.cdfreaks.com/637240-post2.html](http://club.cdfreaks.com/637240-post2.html)

---

### Post by rokytnji on 2008-07-04
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Use the libdvdcss2 install after installing         sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list     


Then install w32codecs in the next part of help doc. This worked for me in Gxine and VLC and I have 2 dvd drives in desktop. One of them works only in vlc and both work in Gxine.

---

### Post by Linux&amp;Gsus on 2008-07-04
OK, I tried it all now (@rokytnji, I checked and installed all the codecs, etc). But still no go.
I might have had some luck before. Why ever. Coincidence?? I don't know. Maybe I'll never know. Anyways, I guess I give up on this and enjoy a "normal" non-region-free DVD experience from now on. :roll:

Thanks for all your effort and help.

---

### Post by rokytnji on 2008-07-05
I have had real good luck with IBM DVDRW's using Linux when you decide to purchase a replacement.:popcorn:

---

### Post by Linux&amp;Gsus on 2008-07-05
Well, actually I never had any trouble until now. But it's a laptop. So, most likely I'll never by a replacement until the whole machine needs to be replaced.
Good thing I still have a desktop. No probs there. If I would have I would be screwed. No TV in the house...

---

