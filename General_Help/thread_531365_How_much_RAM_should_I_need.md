---
title: "How much RAM should I need?"
date: 2007-08-21
forum: General Help
---

### Post by ashughes on 2007-08-21
Hey all!  I am planning on an upgrade but right now cannot decide on 4GB of 2GB of RAM.  What I plan to do with my computer is to run VMWare with XP, Vista and Linux VMs, Open Office, Songbird, Firefox, Video/Audio encoding (divx, mp3, etc), Wine for gaming.

The pros and cons of the 4GB plan that I see is that I will have to go for 64bit Ubuntu meaning compatability issues (flash, codecs, hardware, etc) but having 4GB will make my system future proof.

The pros and cons of the 2GB plan that I see is that I will be able to run 32bit Ubuntu which I have experienced to be very stable over the last couple years but will 2GB be enough.  This plan also saves me $100.

Any advice here would be greatly appreciated.  Thanks.

---

### Post by strabes on 2007-08-21
2gb. 4gb is ridiculous and unnecessary, even for amature video editing. I have 1gb and audio/video encoding works really fast. Linux is simply far faster than windows and needs far less hardware and fewer resources.

Virtualizing vista might prove troublesome, by the way.

---

### Post by ddrichardson on 2007-08-21
> **strabes said:**
> 2gb. 4gb is ridiculous and unnecessary, even for amature video editing. I have 1gb and audio/video encoding works really fast. Linux is simply far faster than windows and needs far less hardware and fewer resources.

Virtualizing vista might prove troublesome, by the way.

You know, I saw a very similar comment many years ago regarding someone upgrading to 16Mb of RAM. ;-)

On a more useful note - more memory is often helpful when it comes to video editing or running multiple VMs simultaneously but strabes is right in that for your needs, especially with divx encoding its processing power that counts.

---

### Post by ashughes on 2007-08-21
As far as the Vista VM, I run Vista in VMWare server with no problems on my Centrino Duo laptop with 1.5GB of ram.

keeping that in mind, I plan on upgrading my desktop to a Core2Quad Q6600 so the processing worries you mentioned should be taken care of.

Thanks for your help.  2GB it is!  I guess if I really need more I could always add another gig.  AFAIK 32-bit supports 3GB right?

---

### Post by ddrichardson on 2007-08-21
The 4 Gb/3 Gb is predominantly a windows problem to do with reserving pages.

32 bits theoretically prvides enough addresses to access up to 4 Gb so 3 Gb would be OK.

---

### Post by ashughes on 2007-08-21
Thanks for your advice.

---

### Post by fragos on 2007-08-21
Check out the "free" command in a terminal window.  It will tell you if you're using swap space.  Systerms that swap can benifit from more memory, particularly when starting new applications.  On my system, 1GB give me enough memory to avoid swaping.  I don't do VM but assume that would add memory requirements.  I'd get 2GB and use "free" to determine if more memory will help.  Sticking with the 32 bit kernel is a good idea.

---

### Post by logos34 on 2007-08-21
> **ashughes said:**
> Thanks for your help.  2GB it is!  I guess if I really need more I could always add another gig.  AFAIK 32-bit supports 3GB right?

I agree with the above poster, I think it's an issue with windows which seems to have trouble recognizing all the RAM when you put in 4GB.  If you upgrade to 3GB (in a 4 slot layout) just make sure you get the right dimm slot or use dual-channel kit (check the mobo manual) otherwise you'll back in single-channel mode.  (Intel is this way)

---

### Post by andrew.46 on 2007-08-21
Hi,

 This is a discussion that rages throughout forums on so many different Operating Systems / Linux distros. Perhaps it all started when Bill Gates supposedly declared that nobody would ever need more than 512k ?

 My own thoughts? For a *new* system I would get 2 gig of RAM (although my *existing* system runs well with 1 gig). But if RAM was especially cheap at the time I would get more. It would be a mistake to spend a l*ot* of money chasing beyond 2 gig IMHO though.

                Andrew

---

