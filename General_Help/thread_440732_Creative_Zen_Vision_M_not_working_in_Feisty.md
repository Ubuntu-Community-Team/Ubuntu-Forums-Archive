---
title: "Creative Zen Vision M not working in Feisty"
date: 2007-05-11
forum: General Help
---

### Post by rekahsoft on 2007-05-11
Today i went out and bought myself a creative Zen Vision M. Ubuntu is not able to detect it and i have not been able to read it with both gnomad2 (from the repos and build from source), amarok, and banshee built with mtp support. The device does not even get registered or mounted...how do i get my creative Zen Vision M working in feisty?

---

### Post by rekahsoft on 2007-05-12
I have been debugging for 2 hours or so now and i have found what is happening...for some reason the player freezes as soon as i connect it to a my linux laptop...i tried connecting it to a windows pc and it worked fine...how can i fix this?

---

### Post by Ariox on 2007-05-15
Hi, 

I had the exact same problem. A bit of Googling told me that updating the firmware should fix this problem. You can find the latest firmware on the official site, which comes in the form of a simple exe. Obviously you'll need to use your windows install to do this. I just upgraded to version 1.20.02 and Gnomad 2 does a fine job of uploading music now. 8) 

The only qualm I have is the unpolished nature of the Gnomad 2 software; it's buggy. Still, it should do fine. 

Hope that helps. 

--Ariox

---

### Post by rekahsoft on 2007-05-18
> **Ariox said:**
> Hi, 

I had the exact same problem. A bit of Googling told me that updating the firmware should fix this problem. You can find the latest firmware on the official site, which comes in the form of a simple exe. Obviously you'll need to use your windows install to do this. I just upgraded to version 1.20.02 and Gnomad 2 does a fine job of uploading music now. 8) 

The only qualm I have is the unpolished nature of the Gnomad 2 software; it's buggy. Still, it should do fine. 

Hope that helps. 

--Ariox

yes, after some time i figured i needed a firmware update so i did it and all was well...as for software support in linux it is not as good as it could be...it is alpha/beta support...i did not like Gnomad2 and it worked like crap so i built banshee 0.12.1 from source with mtp enabled. It works reasonably well but i have had a couple of crashes which is reasonable because it is still beta software. One thing that is really bothering me is that no matter what software i use to upload my music to the Zen it for some reason cannot read some ID3 metadata...with banshee the songs actually go on the player so i can view them normally but when i look at them from the computer (windows or linux it makes no difference) they show up as blank or "<Unknown>". Very annoying.

---

### Post by fettuohi on 2007-06-19
Was it necessary to build banshee from source? Don't the feisty packages have mtp enabled?

Regards

André

---

### Post by FuturePilot on 2007-06-19
You could try Amarok. In Feisty it was compiled with MTP support. It works quite well I think. I have a Zen MicroPhoto and it works great with Amarok,

---

### Post by rekahsoft on 2007-06-19
lol...i gave up...brought the thing back..MTP is slow (i got it working through banshee) and it does not fit what i want :S

---

### Post by fettuohi on 2007-06-19
> **FuturePilot said:**
> You could try Amarok. In Feisty it was compiled with MTP support. It works quite well I think. I have a Zen MicroPhoto and it works great with Amarok,

Yeah but you can't transfer files with filenames including german umlauts for some reason. Not that is a problem but it's a bit irritating.

Regards

André

---

