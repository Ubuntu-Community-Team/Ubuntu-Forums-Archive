---
title: "ies4linux"
date: 2008-05-14
forum: General Help
---

### Post by niceguy123 on 2008-05-14
Asides for web design, I need to access a couple of websites that only seem to work on Internet Explorer. 

I have ies4linux installed and on my desktop, but it doesn't seem to browse anywhere or it just gets stuck. Do I need to reinstall or what.

What other possibilities might there be? I've been looking for and trying firefox ie addons and have tried running the sites on Opera and konqueror, but these problematic sites.

---

### Post by ardvark71 on 2008-05-14
Hi...

What are the web pages you're trying to access, out of curiosity?

When I was using 5.10 (breezy badger,) I installed ies4linux to continue on with a survey site that required, with no exceptions, IE 6 or 7. I'm assuming because of the WINE layer, it ran as slow as molasses and almost freezing it up entirely when it needed the Java plugin. I never was able to get the survey site to work at all with it.

To my knowledge, Ies4linux is probably the only "easy" way to get IE on a linux distribution. I've read of another extremely difficult and complicated method of getting IE to work but I have long forgotten where the formula was located on the web.

You would probably do better by creating a dual boot system if you have a (legal) copy of windows lying around.

Best Regards...

---

### Post by niceguy123 on 2008-05-14
Dual boot? I don't know, I'm not real excited about having windows on my computer. Doesn't it take up a lot of diskspace. (btw-how do I check to see how much disk space I'm using in Ubuntu?)

---

### Post by ardvark71 on 2008-05-15
> **niceguy123 said:**
> Dual boot? I don't know, I'm not real excited about having windows on my computer. Doesn't it take up a lot of diskspace. (btw-how do I check to see how much disk space I'm using in Ubuntu?)

I think Windows XP is around a gigabyte (maybe less,) Vista will require at least 15 GB's, perhaps more. Windows 98 is around a 100 MB's depending upon the type of install. 

It's been a while since I've used Ubuntu, but check around under the admin menu, it should be there in one of the listings.

Best Regards...

---

### Post by GolanTrevize on 2008-05-15
> **niceguy123 said:**
> 
I have ies4linux installed and on my desktop, but it doesn't seem to browse anywhere or it just gets stuck. Do I need to reinstall or what.

In the past also had this effect frequently. I could not figure out the reason why, but somehow I got it running anyway.

Some things I did wrong where:

* Do not install two or more IEs at the same time. This overwrote my old browsers and they did not even start any more.
* Check where you got the install script from. I used to have three different IE4Linux scripts lying around and lost the overview which one to use. Messing old ones with new ones propably is no good idea
* between two installation trials it would be good to delete the wine and install-directories (but don't do that if you have a elaborate wine-configuration running or you will end up reinstalling everything)

For more support I think it would be better to check [www.tatanka.com.br/ies4linux](www.tatanka.com.br/ies4linux)

> **niceguy123 said:**
> 
What other possibilities might there be? I've been looking for and trying firefox ie addons and have tried running the sites on Opera and konqueror, but these problematic sites.

You do not have that much choices. ie4linux is one of them. 

Another would be CrossOver Office:[www.codeweavers.com](www.codeweavers.com)
Used that once for office, macromedia a.s.o and it worked perfect.
It costs 37$ but if you have the necessity to collaborate extensively with M$ products it's worth every cent. (that's as much as 2 1/2 crates of beer - so it's not that expensive)

The third method would be to install 

apt get install virtualbox-ose

and install a full blown windows in it. This also works pretty well, though I could not get the registration key in it and had to reinstall after one month. 
Anyway I regard this as a workaround, but at least you don't have to boot up everytime you change something.

I don't think that you got more options than these

---

### Post by niceguy123 on 2008-05-15
> **GolanTrevize said:**
> 
* Do not install two or more IEs at the same time. This overwrote my old browsers and they did not even start any more.
* Check where you got the install script from. I used to have three different IE4Linux scripts lying around and lost the overview which one to use. Messing old ones with new ones propably is no good idea
* between two installation trials it would be good to delete the wine and install-directories (but don't do that if you have a elaborate wine-configuration running or you will end up reinstalling everything)



Who do I figure out if I have it installed more then once and how do I uninstall wine?

---

