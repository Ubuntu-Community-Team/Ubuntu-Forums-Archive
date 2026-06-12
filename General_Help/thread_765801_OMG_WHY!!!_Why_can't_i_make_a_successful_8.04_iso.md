---
title: "OMG WHY!!!?? Why can't i make a successful 8.04 iso?"
date: 2008-04-24
forum: General Help
---

### Post by kdarkentity on 2008-04-24
I've tried downloading three different ubunu hardy heron 64 bit iso's all from different servers and they are all bad iso's! I've tried burning them multiple times, tried different types of cd's, tried burning with both nero and iso recorder and have tried burning them on multiple computers. ALL Failed! I do have an intel core 2 duo t7200 with 64 bit support. So why can't i get a good ubuntu 8.04 Lts 64 iso!?

---

### Post by interconnect on 2008-04-24
mine did not work the first time i burned it, despite the disc check saying it was ok.  the disc checker that is on the ubuntu disc came up with errors.  i re-burned at a much slower speed (8x) and it worked perfectly.  did you check the MD5 sums after you downloaded them to make sure the iso's you have are ok?

---

### Post by tlacuache on 2008-04-24
I tried to burn the .iso unsuccessfully several times. Finally I determined that the CD .iso is a few sectors bigger than my burner would do. I enabled overburn and then it burned ok. You can google how to overburn a disc.

---

### Post by neodude237 on 2008-04-24
Burn at a slower speed, 24X actually worked for me, and I am up and running :D

---

### Post by kdarkentity on 2008-05-05
Ok so now i have concluded that my .iso images for 8.04 are not the problem as proven by be mounting the image as a cdrom with Virual Box for windows. 

But still no matter what program i use i cannot burn either a 32 bit or 64 bit .iso correctly. 

Is there a proven method of burning the new images yet? Write Speed, program, disk etc...

---

### Post by davidpbrown on 2008-05-05
A common mistake is to think you're burning a file.. it needs to be that you are requesting the image be burnt not just copied to disk.

In all those programs there'll be an option burn .iso rather than burn data files.

---

### Post by kdarkentity on 2008-05-05
> **davidpbrown said:**
> A common mistake is to think you're burning a file.. it needs to be that you are requesting the image be burnt not just copied to disk.

In all those programs there'll be an option burn .iso rather than burn data files.

Yea i know that, i am burning it as a disk image and when i go to boot off of the cd i get the boot menu's and the timer counts down, but that's it. It never actually boots.

---

### Post by davidpbrown on 2008-05-05
Although you've mounted it, did you check the image is correct - MD5 check  as suggested above?

You might also try the trick of getting bittorrent to validate and correct only the errors..
see /. from today [Use BitTorrent To Verify, Clean Up Files]("http://tech.slashdot.org/article.pl?sid=08/05/04/2230252&from=rss")

---

### Post by gsmanners on 2008-05-05
It could also just be a bad batch of discs (doesn't happen very often, but it does happen). You might want to verify that doing other types of burns will work and eliminate the drive itself as the cause of the problems.

---

### Post by kdarkentity on 2008-05-06
> **gsmanners said:**
> It could also just be a bad batch of discs (doesn't happen very often, but it does happen). You might want to verify that doing other types of burns will work and eliminate the drive itself as the cause of the problems.

I have tried other disks, other drives, other iso and other write speeds. 

I read on one of the other posts that people are having success by burning the 8.04 iso's with brasero. So thats what intend on trying next.

---

### Post by ASULutzy on 2008-05-06
I know this isn't exactly the solution you're probably looking for, but I managed to make a bootable USB flash drive with the Ubuntu live-cd. It's more for maintenance when I break something horribly, but you can find the guide I followed here: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by jespdj on 2008-05-06
If for some reason you can't get it on a CD successfully then you could try ordering a free CD: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by Joeb454 on 2008-05-06
Are you burning from Windows? If so I prefer [imgburn]("http://www.imgburn.com") for iso burning - it's free too :)

Also don't forget to burn at the slowest speed (I tend to burn at x2 rather than x1)

---

### Post by Ameneon on 2008-05-06
I had this problem as well, 3 times at lowest speed and burning from image to disc, the burn would proceed ok to the point of closing the disc, then it would fail every time. As I dualboot in order to be able to run games I just copied the iso to my windows disc and burned it in XP/CDburnerXP instead, which worked just fine. However I guess not everybody are having this problem or it would be more of an outcry about it..

---

### Post by kdarkentity on 2008-05-06
> **Joeb454 said:**
> Are you burning from Windows? If so I prefer [imgburn]("http://www.imgburn.com") for iso burning - it's free too :)

Also don't forget to burn at the slowest speed (I tend to burn at x2 rather than x1)

I just did exactly this twice and both times failed. I know the disk image isn't bad either because i can mount it with virtual box and that works fine.

---

### Post by kdarkentity on 2008-05-06
I had a little more success by using brasero, i burned the disk at 1x and the kernel at least loads to 7% now.

What are the best settings to use with brasero?

---

### Post by wrgb2 on 2008-05-06
I don't remember what speed I used, I think the default, but I do remember that I changed Image Type from "let brasero choose" to "*.iso", and got a successful burn.  I had been having the same problem as you, I'd tried several disks, speeds, programs in Windows, but got it the first time using Brasero in 8.04 beta.

---

### Post by Bigtime_Scrub on 2008-05-06
> **kdarkentity said:**
> I've tried downloading three different ubunu hardy heron 64 bit iso's all from different servers and they are all bad iso's! I've tried burning them multiple times, tried different types of cd's, tried burning with both nero and iso recorder and have tried burning them on multiple computers. ALL Failed! I do have an intel core 2 duo t7200 with 64 bit support. So why can't i get a good ubuntu 8.04 Lts 64 iso!?

Are you using the Ubuntu servers from this site?

I know it sounds strange but I had the same problem. I went through about 9 CD's and 1 DVD. The only successful ISO+burn I got was when I downloaded 8.04 off a torrent site. 

Try that.

---

### Post by oldsoundguy on 2008-05-06
just to toss this out .. I tried several times to download and burn the HTML version of 8.04 (from the site and from several mirrors) .. no luck, bad disk every time.

Only when I downloaded via TORRENT did I get a reliable copy and the download speed was incredibly fast vs the HTML download!

Did the burn on a Windows machine using Ashampoo as the burning program and let it go with it's default settings as to speed, etc.

Disk works fine!

---

### Post by kdarkentity on 2008-05-07
> **wrgb2 said:**
> I don't remember what speed I used, I think the default, but I do remember that I changed Image Type from "let brasero choose" to "*.iso", and got a successful burn.  I had been having the same problem as you, I'd tried several disks, speeds, programs in Windows, but got it the first time using Brasero in 8.04 beta.

Alright then i'll give brasero another change, thanks.

---

### Post by quasimodo69 on 2008-05-07
> **interconnect said:**
> mine did not work the first time i burned it, despite the disc check saying it was ok.  the disc checker that is on the ubuntu disc came up with errors.  i re-burned at a much slower speed (8x) and it worked perfectly.  did you check the MD5 sums after you downloaded them to make sure the iso's you have are ok?
Interconnect-thnx for the advice-people do not realize that even though their burner is 52x..to do the max may be over taxing the computer they are burning on.And also a word of caution-burning at a lower speed will get you better burns and less bad disc's.My burner is 52x..but I always burn at 16x.I have never made a coaster since I learned this lesson.
If you are in a hurry...and you do not have a topnotch 4k$ box...slow down!Burn slower...wash some dishes while it burns!Do nothing else while it burns!Do all this to make sure you get a good burn.Check the disc when you are through.
these seem like simlpe details..and some people overlook them..but some people need to heed them!
Friends do not let friends burn coasters!
Good things come to those who wait.If this does not work..you have a source that is bad (I have found that)..you have a source that is overloaded..(I have had that also) or you need to look for compuetr or hardware problems.
Man... I hope this helps from a moron searching..and please do the CD and memory checks..ok?
quasimodo69
and I hope you do not think I am talking down to you.I wish more would do that to me!
Thanks for the best moderated forum on the net!

---

### Post by quasimodo69 on 2008-05-07
> **davidpbrown said:**
> Although you've mounted it, did you check the image is correct - MD5 check  as suggested above?

You might also try the trick of getting bittorrent to validate and correct only the errors..
see /. from today [Use BitTorrent To Verify, Clean Up Files]("http://tech.slashdot.org/article.pl?sid=08/05/04/2230252&from=rss")
davidpbrown..I am new to this..and my answer above was generic..but I do not know how to use the checksum feature...is there a site for dummies...excuse me...morons  on how to go through this chechsum?
thnx

---

### Post by quasimodo69 on 2008-05-07
Just to say..I burned my ISO the first night it was available and used a GREAT windows program (sorry) called Deep burner from Snapfiles.com.!1st download and first burn..I will say I have had bad burns that perplexed me...and it turned out a burn from another source worked.time after time I tried a burn from what I thought was a good source..and maybe it was..but a change of source did the trick?Just trying to help..

---

### Post by kdarkentity on 2008-05-08
Finally i have my solution!, i Finally made a successful burn of 8.04 by downloading the 8.04 alternate.iso and then used brasero to burn it.

---

