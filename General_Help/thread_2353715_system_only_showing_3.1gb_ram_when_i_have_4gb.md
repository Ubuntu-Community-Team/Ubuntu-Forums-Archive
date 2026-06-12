---
title: "system only showing 3.1gb ram when i have 4gb"
date: 2017-02-24
forum: General Help
---

### Post by grahamadgo on 2017-02-24
Hi

I have 4 x 1gb ram fitted but under SYSTEM/DETAILS it is only showing as 3.1..
OS is Ubuntu 16.10 64 bit
Graphics Nvidia GT520 using Nvidia driver from ADDITIONAL DRIVERS
RAM and graphics are both DDR2
motherboard -
    Manufacturer: Intel Corporation              
    Product Name: D915GUX   
All ram is showing as good in memtest       

2GB of the ram is new but is the same specs and manufacturer
since  putting the new RAM in i am getting this gumph when its loading. the top info about the USB is the same but the rest didn't come up before.
I haven't[IMG]http://i1065.photobucket.com/albums/u396/grahamadgo/2017-02-24%2013.27.27_zps2gbhyjyd.jpg[/IMG] checked the RAM amount before so its possible hat it has always shown 3.1 GB

Is it normal for the RAM to show less than 4gb or is not fully utilizing whats there?

P.S. sorry about the Monstrously large image :)

---

### Post by Bucky Ball on 2017-02-24
> **grahamadgo said:**
> P.S. sorry about the Monstrously large image :)

[s]There is no image, so no need to apologise,[/s] just attach large images rather than putting them in the body of your post.

Use 'Adv Reply' or 'Go Advanced' button at bottom right of post and use the paperclip icon in the toolbar there to attach your large pics. Cheers.

*** Ah, *now* there's a large image. As above. Better to attach. Think of potential helpers with slow connections and vision issues. ;)

Yes. It is normal for not all the RAM to be available to the system, but probably not .9 of a Gb. Where is it showing 3.1Gb of RAM? What software? Run 'top' in a terminal (just type that and hit return) and see how much memory that returns at the top of the screen.

---

### Post by oldrocker99 on 2017-02-24
Are you running a 32-bit system? That would explain the system not seeing all the 4GB of RAM. There are some kludgey workarounds, but you're best off installing a 64-bit system. A 64-bit system can access **far** more RAM than a 32-bit system.

---

### Post by Bucky Ball on 2017-02-24
> **oldrocker99]Are you running a 32-bit system? That would explain the system not seeing all the 4GB of RAM.[/QUOTE]

Third line, first post ...

[QUOTE=grahamadgo said:**
> 
OS is Ubuntu 16.10 64 bit


---

### Post by Perfect Storm on 2017-02-24
Are you sure it's 64-bit, you could have installed 32-bit by mistake.

```
uname -a
```

---

### Post by grahamadgo on 2017-02-24
Hi, thanks to all for the replies.

I got that figure from SYSTEM SETTINGS...DETAILS
I have attached the image from 'top' I assume the KiB memory is the one that I am looking for  > 3208268 total  (image more moderate size this time)

Definitely running 64 bit system  ~$ uname -a
Linux agg-desktop 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Autodave on 2017-02-24
I hope that someone has a better answer than I do for you, but you could possibly have a bad CPU.  I have such a machine here: 3.4 quad core running 64 bit. If I try to put 4 gig in in it, it throws all knids of error messages usually. However, when I can get it to boot and run, it only recognizes 3 gig regardless of whether I have 4 or 8 gig installed.

You said that you added 2 gig: are there now 2 of the 2 gig chips in it or 4 of the 1 gig chips, or something else?

---

### Post by grahamadgo on 2017-02-24
hi autodave,

theres 4 x 1 gig chips

---

### Post by oldrocker99 on 2017-02-24
Have you run Memtest86+ on the RAM? It runs from the GRUB boot menu. It is unlikely, but possible that you have a bad RAM stick. If you do get errors, pull one stick out and run it again. If you still get errors, that's the bad stick. Or if it doesn't return errors, the stick that's out is the bad stick.

Let us know the results.

---

### Post by grahamadgo on 2017-02-24
hi old rocker,

Yes, i ran memtest from the GRUB. It took an outrageously long time to do but found no errors

---

### Post by grahamadgo on 2017-02-24
would it be worth me firing it up with the two original RAM chips in and do the same test?  then just the 2 new ones and do the same........ or would that be unnecessary fiddling?.. and just addle its brains

---

### Post by Autodave on 2017-02-24
Try removing the last stick and see what memory the machine reports with just 3 gig in it.

---

### Post by grahamadgo on 2017-02-24
Ok removed the last stick and it is showing 2.9 gb.  it came up with a lot of messages similar to the first image that i posted and a warning about unbalanced memory,  then took about 7 mins to boot, don't know if that is relevant.

---

### Post by Bucky Ball on 2017-02-24
Personally, I'd take out the two old ones. You know they work. Why have them in to test?

Put in one of the new sticks. Boot up. You have RAM? If so, great. Take out and stick the other one in. If not, you either have a dead stick or the contacts are a little icky from the manufacturer. They sometimes need to be pulled and reseated a few times.

You can also gently rub the contacts with an eraser (yes, that's right, a 'rubber' that you use to erase pencil) and that removes the factory gunk, then try again. You should be testing the two new sticks. Forget about the ones you know are working.

And as they are dual, they need to work in pairs. The slots for a pair are usually marked with colour or by some other means. Take note, that the pairs DO NOT generally go in logical order, i.e. slot 1 and 2 are the first pair. It is often slot 1 and 3 are the first pair, 2 and 4 are the second.

There is another possibility. Dead RAM slot. It happens and I've had it happen. Best way to check that? Stick one of the old sticks in the first slot. Boot. Works? Great. Second slot. Works? Great ... and so on. No other sticks in, just use one stick you know to be functional A1.

> **grahamadgo said:**
> would it be worth me firing it up with [s]the two original RAM chips in and do the same test? then[/s] just the 2 new ones [s]and do the same........[/s] or would that be unnecessary fiddling?.. and just addle its brains

Yes, two new ones and no; it is *_necessary_* fiddling if you want to get to the bottom of your RAM issues. And again, no. This will not addle any brain (computer don't have one :)).

---

### Post by grahamadgo on 2017-02-26
Hi Buckyball,

Thanks for the reply.

I had tried the 3 stick idea first before i saw your reply. Unfortunately t went as mad as a box of frogs when I did that with a good 15mins of warnings on the boot screen followed by another 10 mins or so for the OS to load. Also it couldn't see either of the two hard drives attached or he USB's.  Maybe nothing to do with removing the stick, It could have just been on the brink of madness anyway,

However I bore with it and removed the two older sticks and fired it up using just the one stick in each slot individually...I wasn't screen watching as i'm sure you can imagine with my new found 1/2 hour booting time.  All seemed to be ok.. Also gave them a clean as suggested :)

I also started it with the two original sticks and checked the memory .. showing as 2GB (good sign)  and then the new sticks  2GB (also good)
I then put all four back in and ran memtest again (see image)  showing 3.2 GB as before

I also booted from another hard drive using Elementary and checked, (this was also pretty slow to load but nothing like I was getting on the Ubuntu disk) this also showed 3.2GB.

Finally.. concerned about the huge boot-up time and the inability so see any other drives I backed everything up and reinstalled the OS.. Now everything seems to be working ok with regards to boot up time and other hard drive visibilty.. 

The memory is still showing as 3.2 but i'm inclined to go along the 'Heigh- Ho its working fine, leave it alone' route. If it is a hardware anomaly or incompatibility  with the RAM or the M Board maybe just cant handle it for whatever reason, then  there could well be very little that I can do to affect it. 

Thanks to all though for your input and help  Much appreciated and definitely worth the investigation

Cheers

Graham[ATTACH=CONFIG]273905[/ATTACH]

---

### Post by grahamadgo on 2017-02-26
Just an afterthought but could it be that  on board graphics are utilising the .9GB ?  or doesn't it work like that?

---

### Post by Autodave on 2017-02-26
I am beginning to think that my first thought was correct: you have a bad CPU.  I have a 3.4 quad core desktop here that does the same thing. As long as I limit it to 2 gig RAM, life is good. Anything over that and error messages everywhere, sometimes it eventually boots and sometimes it doesn't. When it does boot, RAM shown is anywhere from 2 gig to amounts larger than installed.  Bad CPU.  Fortunately, for my workbench, it is all I need and will live there until it dies.

---

### Post by Bucky Ball on 2017-02-26
> **grahamadgo said:**
> Just an afterthought but could it be that  on board graphics are utilising the .9GB ?  or doesn't it work like that?

Possible, but doubtful. Still, haven't used on board gpu in awhile so maybe that's how much they eat now. If you boot to the BIOS and have a look around in there, it should tell you how much the internal graphics is using of the RAM. You should also be able to adjust that.

---

### Post by Yellow Pasque on 2017-02-27
[https://en.wikipedia.org/wiki/PCI_hole](https://en.wikipedia.org/wiki/PCI_hole)

> Product Name: D915GUX 

It's an old mobo, so even though it supports 64-bit operation, it probably doesn't support remapping hardware addresses above 4GB and you're stuck with 3.2GB. It's very common, especially with the the Intel chipsets made in the dawn of the 64-bit era (915/945 chipsets).

> Just an afterthought but could it be that on board graphics are utilising the .9GB ? or doesn't it work like that? 
It doesn't work like that when you have a discrete GPU.

---

### Post by Yellow Pasque on 2017-02-27
> **Autodave said:**
> I am beginning to think that my first thought was correct: you have a bad CPU.

I have no idea how you reached that conclusion.

---

### Post by grahamadgo on 2017-02-27
OK, thanksyou to all for your info and advice

---

