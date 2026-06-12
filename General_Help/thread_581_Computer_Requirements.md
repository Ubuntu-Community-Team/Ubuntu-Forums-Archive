---
title: "Computer Requirements"
date: 2004-10-14
forum: General Help
---

### Post by Infatuated_iPod on 2004-10-14
Hey, i was wondering what are the minimum requirements to run Ubuntu on a computer? I have an old computer sitting in the middle of my room and i wanted to see if i could put it so some use with Ubuntu.

---

### Post by Mindstab on 2004-10-15
I've installed it on a p 266mhz and a computer that was slower than that

I'm sure it will be "fine".  It'll work, but something might take a bit.
Visually, it will priobably look better and be a bit faster when the switch to xorg and composite (less redraws)

so make a /home partition so you cna upgrade (or y'know, us the other way with apt or something that i'm totally unfamiliar with)

---

### Post by Infatuated_iPod on 2004-10-15
I am about to buy a IBM on ebay, it is PII 350mhz. 64 MB Ram, 6 gig HD.. is that going to work out?

---

### Post by triad169 on 2004-10-15
Do you have a model Number for the IBM?  The CPU, Memory &amp; HardDrive requirements are adequate (Might want to bump up memory a little just to increase performance of the system).  The reason I ask about the Model number is they might have some wierd Hardware configurations that might not be compatable with linux.  

Triad

---

### Post by Infatuated_iPod on 2004-10-15
I actually found a compter on ebay that is a little better, here is a link. I cant seem to find the model number, but maybe you can tell something by the pic...
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&amp;category=51110&amp;item=5129152983&amp;rd=1&amp;ssPageName=WDVW](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&amp;category=51110&amp;item=5129152983&amp;rd=1&amp;ssPageName=WDVW)

---

### Post by triad169 on 2004-10-16
Hmm they give you a model Number of IBM PC 300PL unfortunatly there are like 8 different varities of these IBM PC.  From looking at a few of the manuals it appears the Video Card might not be supported by Linux.  Its like a S3 Trio which from what i can tell on XFree website is not supported.  I would think you might have a tough time installing Ubuntu on this.  Sorry to be kind of Vague but with know the specefic version of this Model tough to disect the hardware in it.

Triad

---

### Post by Infatuated_iPod on 2004-10-16
Well, thanks for your tip!  A powerpc g3 would support linux right? Since all the cards on macs are generally the same? Because i got this other great deal with a powerook+powerbc combo, that would be pretty sweet to have ubuntu on one or both of those. :)

here is the auction link, if you could give me some advice i would greatly appreciate it. 
[url]http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&amp;rd=1&amp;item=5130521152&amp;ssPageName=STRK:MEBI:IT    
[/url]

---

### Post by triad169 on 2004-10-16
*Powerbook 1400c:*

This is a NuBus based machine, which makes putting linux on there very hard.  Doesnt look like the Popular PPC based distro's like yellowdog dont support it. You might want to look at this link:

 [http://www.clivemenzies.co.uk/nubus_woody.htm](http://www.clivemenzies.co.uk/nubus_woody.htm)

It doesnt specifically talk about the 1400c but ity does explain howto setup debian using Apple MkLinux Booter on Nubus PowerPC.  the killer too is that the 1400c has very little memory so would need to upgrade that too.   IMHO You might be able to get going but I have not found any conclusive proof that someone has.
[i]
Power Mac G3 Desktop 233 MHz[/i]

This one looks like you can get Linux to run on.   Now the question to be asked will Ubuntu work on it.  I am sure you can get going but you probably will have to do some Tweaking and research before you jump into it.

Oh well hope this helps out a bit.  I never tried to get Linux Going on a PPC  so my responces above are a little vague.  Most of the information was gleaned from the mailing List and googling.

Triad

---

