---
title: "How do I do this? Is there a tutorial for this?"
date: 2007-03-06
forum: General Help
---

### Post by ardchoille42 on 2007-03-06
I am trying to make a livedvd which includes the Dapper and Edgy livecd's. I know it's possible to make a multi-distro livedvd because others have done it. How does one go about doing this? Is there a tutorial or walkthrough somewhere?

I suppose once I learn how to do this, I could have a nice livedvd which includes Dapper, Edgy, System Rescue CD, DSL and others. I would be limited to 8Gb of data which is compressed to 4gb, I think.

---

### Post by SuSUntu on 2007-03-06
Give CDShell a try.

[http://www.cdshell.org/](http://www.cdshell.org/)

I see from an earlier thread of yours that you had previously used the Nautopia script, but are aware that its website is down now.

Have fun.

---

### Post by ardchoille42 on 2007-03-06
Thanks for the reply. I'll have a look at CDshell and see what I can learn :)

---

### Post by tagra123 on 2007-03-06
I use reconstructor for remastering.

---

### Post by ardchoille42 on 2007-03-07
> **tagra123 said:**
> I use reconstructor for remastering.

Can reconstructor allow me to take several small live cd's (DSL, sysresccd) and put them all on the same livedvd? I thought reconstructor was only for Ubuntu.

---

### Post by SuSUntu on 2007-03-07
> **ardchoille42 said:**
> Can reconstructor allow me to take several small live cd's (DSL, sysresccd) and put them all on the same livedvd? I thought reconstructor was only for Ubuntu.

I was thinking what he meant by posting about reconstructor was that you could use it to customize your Ubuntu images (make them smaller mostly) before using something else like CD Shell to combine all the images onto a single DVD. That way you could get more images on the DVD.

Otherwise, I'm not sure what he meant because I didn't know reconstructor could be used to make multiple-boot DVDs; I thought it was just to make custom images (kind of like nLite if you've ever used that on a Windows machine for slipstreaming).

By the way, here's another link with instructions for creating mult-boot DVDs without a script. It's just step-by-step using **isolinux**:

[http://www.pcquest.com/content/enterprise/2005/105070101.asp](http://www.pcquest.com/content/enterprise/2005/105070101.asp)

---

### Post by tagra123 on 2007-03-07
I thought you was talking about having a live cd with xubuntu, kubuntu. -- I believe this is doable with reconstructor.  

You can make larger images with reconstructor -- not just smaller.  You can install the software you want installed.  I made a cd with persistence --one for the kids with edubuntu on a normally ubuntu machine --  added the  persistent option as the default boot option and some tools like partimage too. You can even add vmware to the remastered cd.

I will follow this thread because the idea is sound.  A multiboot dvd with sysrescue and ubuntu could be very good indeed.   I sure this is possible from messing with cd in the past.  Sysrescue is very easy to add to a partition on the harddrive -- has to be a way.

---

### Post by ardchoille42 on 2007-03-08
> **SuSUntu said:**
> I was thinking what he meant by posting about reconstructor was that you could use it to customize your Ubuntu images (make them smaller mostly) before using something else like CD Shell to combine all the images onto a single DVD. That way you could get more images on the DVD.

Otherwise, I'm not sure what he meant because I didn't know reconstructor could be used to make multiple-boot DVDs; I thought it was just to make custom images (kind of like nLite if you've ever used that on a Windows machine for slipstreaming).

By the way, here's another link with instructions for creating mult-boot DVDs without a script. It's just step-by-step using **isolinux**:

[http://www.pcquest.com/content/enterprise/2005/105070101.asp](http://www.pcquest.com/content/enterprise/2005/105070101.asp)

After looking at the link you posted, it looks rather easy. Dapper and Edgy as well as the System Rescue CD all use isolinux, so this should work. I don't think this is going to be a problem at all and I will post my results as soon as I can.

---

### Post by ardchoille42 on 2007-03-08
> **tagra123 said:**
> I thought you was talking about having a live cd with xubuntu, kubuntu. -- I believe this is doable with reconstructor.  

You can make larger images with reconstructor -- not just smaller.  You can install the software you want installed.  I made a cd with persistence --one for the kids with edubuntu on a normally ubuntu machine --  added the  persistent option as the default boot option and some tools like partimage too. You can even add vmware to the remastered cd.

I will follow this thread because the idea is sound.  A multiboot dvd with sysrescue and ubuntu could be very good indeed.   I sure this is possible from messing with cd in the past.  Sysrescue is very easy to add to a partition on the harddrive -- has to be a way.

I looked at reconstructor but I don't think I will be able to use it for what I wanted. I plan to make a liveDVD with Ubuntu Dapper, Ubuntu Edgy, Damn Small Linux and System Rescue CD. [This link that SuSUntu posted]("http://www.pcquest.com/content/enterprise/2005/105070101.asp") looks like it will work for my needs. I'll update this thread when I have finished working with it.

---

### Post by ardchoille42 on 2007-03-08
Ok, after working on this for several hours, I have learn a couple of things:

1) This is way too much trouble and too difficult to understand
2) This is an entire waste of time due to the fact that you can burn ISO's individually

hehe, now I see why more people don't do this.

Too bad there isn't an app or script that makes this easier or more understandable. I'm halting this project until I find an easier way to do it.

---

### Post by SuSUntu on 2007-03-08
> **ardchoille42 said:**
> Ok, after working on this for several hours, I have learn a couple of things:

1) This is way too much trouble and too difficult to understand
2) This is an entire waste of time due to the fact that you can burn ISO's individually

hehe, now I see why more people don't do this.

Too bad there isn't an app or script that makes this easier or more understandable. I'm halting this project until I find an easier way to do it.

That's pretty funny.

This morning I was reviewing both links I provided as well as looking up some other related material, and although I thought the second link described a fairly easy process (we all know how that goes once you get into it, though), I was thinking why in the world would anybody need to do this except in very specialized cases? I can burn and carry a lot of optical disks with far less effort. :)

Nevertheless, I'm sorry to see you have given up because I was interested to know if the instructions that were provided were concise and accurate enough to actually carry one through to completion of a project without a lot of hiccups. Maybe I'll set aside a day in the not too distant future and I'll post back. I wouldn't hold my breath waiting, though. :)

---

### Post by ardchoille42 on 2007-03-08
> **SuSUntu said:**
> That's pretty funny.

This morning I was reviewing both links I provided as well as looking up some other related material, and although I thought the second link described a fairly easy process (we all know how that goes once you get into it, though), I was thinking why in the world would anybody need to do this except in very specialized cases? I can burn and carry a lot of optical disks with far less effort. :)

Nevertheless, I'm sorry to see you have given up because I was interested to know if the instructions that were provided were concise and accurate enough to actually carry one through to completion of a project without a lot of hiccups. Maybe I'll set aside a day in the not too distant future and I'll post back. I wouldn't hold my breath waiting, though. :)

Well, I got far enough into to have the files copied over to the remastering directory. But, when I saw all of the things I needed to edit, and the possibility of wasting too many blank dvd's after making mistakes, I no longer saw the benefit. As you said, "I can burn and carry a lot of optical disks with far less effort" and that was a very good point.

---

### Post by g45uk2 on 2008-04-07
> **ardchoille42 said:**
> Well, I got far enough into to have the files copied over to the remastering directory. But, when I saw all of the things I needed to edit, and the possibility of wasting too many blank dvd's after making mistakes, I no longer saw the benefit. As you said, "I can burn and carry a lot of optical disks with far less effort" and that was a very good point.

you could always test the .iso in VMWare to save on dvd's

---

