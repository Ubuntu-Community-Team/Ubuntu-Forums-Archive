---
title: "Ubuntu for seniors"
date: 2006-12-08
forum: General Help
---

### Post by cgl72 on 2006-12-08
Hi all,
I have been scouring the net trying to find a distribution that I could install for my mother and father, both in their mid-sixties and get really panicky when a window pops up in XP saying something is wrong... But I have not found any distribution that would be tailored towards seniors. Here are a couple of things I found:

[http://www.meeswa.com/easyPC.htm](http://www.meeswa.com/easyPC.htm)
[http://tektrekgamer.wordpress.com/2006/05/27/ubuntu-for-your-grandmother/](http://tektrekgamer.wordpress.com/2006/05/27/ubuntu-for-your-grandmother/)
This did not really help that much, except I now know others have done it...

So I gathered up my courage and decided that I could probably customize ubuntu myself... Upon second thought, I decided the best thing to do was to ask for some tips before wasting too much time. 

Can someone point me to some ressources on the web I would have missed, or ideally where someone has done this customization and could share the steps. Thanks

Christian

---

### Post by bodhi.zazen on 2006-12-08
What do they use the computer for, what are their needs ?

If not Ubuntu, try [Zenwalk](http://www.zenwalk.org/), [Mepis](http://www.mepis.org/), or [PClinuxOS](http://www.pclinuxos.com/page.php?6)

My wife is the same way and I set her up on zenwalk 6 months ago, no problems.....

---

### Post by OffHand on 2006-12-08
> **cgl72 said:**
> Hi all,
I have been scouring the net trying to find a distribution that I could install for my mother and father, both in their mid-sixties and get really panicky when a window pops up in XP saying something is wrong... But I have not found any distribution that would be tailored towards seniors. Here are a couple of things I found:

[http://www.meeswa.com/easyPC.htm](http://www.meeswa.com/easyPC.htm)
[http://tektrekgamer.wordpress.com/2006/05/27/ubuntu-for-your-grandmother/](http://tektrekgamer.wordpress.com/2006/05/27/ubuntu-for-your-grandmother/)
This did not really help that much, except I now know others have done it...

So I gathered up my courage and decided that I could probably customize ubuntu myself... Upon second thought, I decided the best thing to do was to ask for some tips before wasting too much time. 

Can someone point me to some ressources on the web I would have missed, or ideally where someone has done this customization and could share the steps. Thanks

Christian
If you set it up for them you can make it as easy as you like. No need for another/new distribution. My dad even installed Ubuntu himself (he's 62) after hearing me talking about it.

---

### Post by bsussman on 2006-12-08
this is an interesting project.

Different seniors will have different ergonomic, technical and application set needs.

I like linux and especially ubuntu for it's basic design and I think it is pretty much ready for seniors but attention must be paid to:

1.  default screen resolution which needs to be altered in xorg.conf.
2.  choice of fonts.
3.  some customization to mouse behavior, to reduce the sensitivity of movement and the doubleclick timing.
4.  contrast and color issues.
5.  Depending on your location(s), implementation of VNC to allow you to take kb/mouse control to demonstrate things remotely and SSH to possibly do some maintenance.

What other areas do you feel need customization to meet senior needs?

---

### Post by wieman01 on 2006-12-08
Don't laugh (this is a serious post), but I had to increase the font size in order for my mother to find it a bit more usable. Sorry I cannot contribute more. I found this very funny in the first place, but at the second glance it makes sense, doesn't it?

---

### Post by ColinG on 2006-12-08
I rather suspect this thread will not be welcomed by those seniors with good eyesight and a wealth of IT experience under their belt. There are many of them.

As a matter of interest how long has Linux been around? Take that number away from your example 62 year old and well.............

I appeciate this thread may have started in an endeavour to be helpful but it does rather paint a general picture and one I think is flawed (my opinion only).

---

### Post by OffHand on 2006-12-08
> **ColinG said:**
> I rather suspect this thread will not be welcomed by those seniors with good eyesight and a wealth of IT experience under their belt. There are many of them.

As a matter of interest how long has Linux been around? Take that number away from your example 62 year old and well.............

I appeciate this thread may have started in an endeavour to be helpful but it does rather paint a general picture and one I think is flawed (my opinion only).

He was talking about a solution for his parents. I'm pretty sure he knows what they are up to when dealing with computers.

---

### Post by ColinG on 2006-12-08
That is how it started true. But it (the thread) has become somewhat generic imo.

You may not agree with me, and your opinion is as valid as mine, but that is how I see it :)

---

### Post by bsussman on 2006-12-08
> **ColinG said:**
> I rather suspect this thread will not be welcomed by those seniors with good eyesight and a wealth of IT experience under their belt. There are many of them.

So what you're saying is the folks who are likely to be most aware of the issues involved would not want to see a proper discussion of them?

I don't think so.

You should learn about accessibility issues and the requirement that they be discussed.   Most of the solutions are actually valid (or at least need to be reviewed) for applicability to the general computing population.

Accessibility discussion is always welcome, as far as I can tell, along with the other issues likely to affect 'seniors' more than others, such as the remaining challenges of the linux <-> user interface which is still not quite as much of a no brainer as what comes from the Gates of Microsoft.

---

### Post by squrl on 2006-12-08
Why do you pups insist on putting a limit on the abilities of seniors. Most of their limitations are by their own desire.  

I have four "kids"?? and a flock of Grandkids who insist on screwing with my and my wife's computer to "make it easier". 

When the geriatric crowd wants help they will ask for it. 

Well past 75

---

### Post by bsussman on 2006-12-08
> **wieman01 said:**
> Don't laugh (this is a serious post), but I had to increase the font size in order for my mother to find it a bit more usable. Sorry I cannot contribute more. I found this very funny in the first place, but at the second glance it makes sense, doesn't it?

As someone who needs new glasses I am last to laugh :D

Exactly how did you do it - in the x config? individual app defaults?

What about contrast/color issues?

What about mouse stuff?  I had to reduce the sensitivity, doubleclick parameters, etc for my mother.  Also had to teach her that it was legal to use the mouse with her left hand (especially, that she needed to insist, at the library, that they provide her a pc where the mouse could be placed on the left).  I do not advicate switching the buttons, as this can be confusing to right handed folk that visit, but reaching across or using the wrong hand simply ain't right.

---

### Post by ColinG on 2006-12-08
Accessibility is not about seniors or any other age related category of person - it is about disability and that is quite different.

A dialogue on helping those less fortunate is always welcome.

---

### Post by bsussman on 2006-12-08
> **squrl said:**
> When the geriatric crowd wants help they will ask for it. 

Point taken.

But even non-seniors may not know how re-jiggering some of the parameters can make life easier.

I personally adjust mouse, screen and keyboard things to my needs and I am willing to demand that the parameters be there to adjust :)

I view the discussion as one of facilities, applicable to anybody that wants them but requiring education so that all are aware that the adjustments are there to be made.  And a sensivity to what members of the community might need to be exposed to the possibilities.

---

### Post by OffHand on 2006-12-08
> **squrl said:**
> 
Well past 75

That's pretty awesome!

---

### Post by squrl on 2006-12-08
Sorry for my smart mouth people. I have learned to appreciate what handicapped people go through and it can be maddening. Everyone wants to help and thats nice but it does get old after a while. 

From someone who is there, show the elderly needing help where to learn about it. Don't just do it for them. 

Remember if you live long enough you may also be among the old and frustrated.  :mrgreen: ](*,) 

Well past 75

---

### Post by wieman01 on 2006-12-08
> **squrl said:**
> Sorry for my smart mouth people. I have learned to appreciate what handicapped people go through and it can be maddening. Everyone wants to help and thats nice but it does get old after a while. 

From someone who is there, show the elderly needing help where to learn about it. Don't just do it for them. 

Remember if you live long enough you may also be among the old and frustrated.  :mrgreen: ](*,) 
But this does not hold true for all "elderly". I get your point, a Chinese saying goes:"Give a person a fish and they will fish for a day; teach a person how to fish and they'll eat for a lifetime." Sadly some folks don't have the patience or ability (I am definitely referring to my parents here) to learn more than is necessary to use a customized(!) PC. Albeit your valid argument, reality looks a bit different, at least as far as my family is concerned. Default accessibility plays an important role.
> **bsussman said:**
> As someone who needs new glasses I am last to laugh :D

Exactly how did you do it - in the x config? individual app defaults?

What about contrast/color issues?

What about mouse stuff?  I had to reduce the sensitivity, doubleclick parameters, etc for my mother.  Also had to teach her that it was legal to use the mouse with her left hand (especially, that she needed to insist, at the library, that they provide her a pc where the mouse could be placed on the left).  I do not advicate switching the buttons, as this can be confusing to right handed folk that visit, but reaching across or using the wrong hand simply ain't right.
The font size in KDE can be changed using KControl & is set "globally". The colors do not really matter much. As for the mouse, I remember that we faced the same problem. So all programs open now with a single click (I got used to that as well & I have begun to prefer it). 
Another important thing was to make the menus simple & place a number of program icons on the desktop. That did make a huge difference. 

To conclude, I don't think we will have the same discussion 30 years down the road as younger generations that have grown up with computers grow older.

---

### Post by wpshooter on 2006-12-08
Heck, most of the persons in the office I work at are 35 or under and most of them do not know how to operate M/S windows O/S very well might less Ubuntu !!!  

I have been working in that office over 15 years now and am a good bit older than the average employee there and I hate to say that we still have employees there that still do not know how to set their default printer.  

I don't expect to many of them to be using Ubuntu in the near future !!!!

---

### Post by gjtoth on 2006-12-08
Now, I know you find this difficult to believe but, I'm over 60 and I *TEACH* this stuff to folks that are in their 20s and 30s.  I've probably forgotten more than they know about PCs in general!  I also teach it to other old fogies that are my age.  Know the difference?  *I*, unlike many my age, saw the paradyme shift and shifted with it 25 years ago.  While they were saying stuff like, "It'll never catch on." or, "Computers.. who needs 'em?" or, "I refuse to use those new-fangled things!", I embraced it and learned my a** off!

What's the old adage?... "He who laughs last, laughs best".  Those same hotshots that scoffed at me 10 years ago are now politely asking my assistance to fix their boxes.  Most of the time it's a virus in Windoze that they got by surfing their favorite porn site.  Idiots.

My advice?  Just put the box in front of 'em with Ubuntu on it.  Don't tell them it's not Windoze.  Chances are they won't even know the diff.  And, if they do... so what?  What are they gonna do... install Windows?  Not likely otherwise YOU wouldn't be doing what you're doing.

<click> soapbox mode off. :-D

---

### Post by Tim_Olaguna on 2006-12-08
This whole discussion has been most amusing to me.

I'm now 58 years old, retired after 28 years in state government service.  Some 20 of those years were spent in information technology; 12 as a supervisor of other IT staff, including a PC support help desk, e-mail management team, and our state department's web team.  My last three years I served as a senior analyst helping other department units initiate and manage short and long term IT system development projects.

I am also a life-long physically handicapped person.  I have cerebral palsy and use an electric wheelchair for personal transportation.  My wife also has cerebral palsy.  She manages all of our family business through the help of her trackball equipped iMac.  So accessibility issues have always been important to me.

Having managed a help desk team I am acutely aware there will always be people who need a system which is far more easier to use than what is now available on any platform.  Let's face it; compared to what computers should be and will be some day, we're all still puttering around with the equivalent of an antique model T Ford auto.  So we all need to help folks with these things whenever we can.  But we must also never make assumptions about another person's apparent limits.  You do that at the wrong time and one of us just might run you over.  Accidentally, of course.  These electric wheelchairs and scooters just keep getting faster, powerful, and more prevalent every year.

---

### Post by ardvark71 on 2006-12-08
;) > **gjtoth said:**
> 
My advice?  Just put the box in front of 'em with Ubuntu on it.  Don't tell them it's not Windoze.  Chances are they won't even know the diff.  And, if they do... so what?  What are they gonna do... install Windows?  Not likely otherwise YOU wouldn't be doing what you're doing.

<click> soapbox mode off. :-D

They'll notice a difference all right :mrgreen: 

(......*yells* HEY! Why won't [insert windows program from internet or CD here] install on this thing???!!!!):lol: 

Seriously though, I'm glad you're only venting... as your advice would get yourself and others in a lot of trouble. ;) 

:KS

---

### Post by gjtoth on 2006-12-09
> **ardvark71 said:**
> ;) 

They'll notice a difference all right :mrgreen: 

(......*yells* HEY! Why won't [insert windows program from internet or CD here] install on this thing???!!!!):lol: 

Seriously though, I'm glad you're only venting... as your advice would get yourself and others in a lot of trouble. ;) 

:KS

Only half-venting.  Actually, if you are the one supporting them (especially for free -- of course, family members are always free), and they are the ones coming to you for advice then, tell 'em (as I do):  If they are so savvy, put Windoze on their system and say something like, "Ok, here's your precious Windoze.  BUT, I'm warning you right up front:  I no longer use it because {insert your list of reasons here} and haven't used it for {insert your time period here}.  As with all things, use it or lose it.  I'm starting to forget things about how Windoze operates and one day, I'm not going to be able to help you when you {insert their usual boner here}.  On the other hand, I'm learning more and more about this system called Linux and so are a LOT of other folks.  You've already missed one paradyme shift by starting so late in life on computers.  Are you prepared to be left in the dust again?"  This has two effects:  1.  It wakes them up to the realization that they, indeed, have fallen behind (again) and it's their fault/choice.  2.  If they persist in their ways, they are going to be PAYING for tech support.

They are looking to you as their computer "expert" just as they would turn to their doctor as their health "expert" (don't sell yourself short -- that's exactly what you are!).  If they fail to follow the doctor's advice, what are the consequences?  A caveat here:  Be sure to INSIST upon them backing up their data.  Show them how.  Make sure they know how to do it on their own before you walk out that door.  That way you are "double-covered" - you've warned them about Windoze and you've saved their sorry butts when they persist in doing dumb things you've told them not to do.  If they fail to heed your "expert" advice, they've done it by their own choice.  Granted, it's going to be YOU to come back in for the reformat and reinstall.  But, maybe this time they'll have learned that they aren't the "computer savvy techwiz" they had themselves envisioned to be.  Sitting down behind a mouse and clicking on IE makes you as much an expert as putting your car in "drive" makes you a mechanic.

I've been this route.  I have friends (yes, they are still my friends) that have gone back to the dark side.  They no longer call me for tech support.  They know what I'm going to say and they don't like the sermon. Believe me, it doesn't hurt my feelings and I have more time for ME.  So, they PAY for tech support or have found some M$ chump willing to provide them with free support.  On the flip side, I have friends that have been using Linux in one form or another for quite a while now and have told me (and the friends that went back to the dark side) that their computer is not the time bomb it once was and it's once again fun, more productive, and a LOT more stable.

As for "get me and a lot of others in trouble", *I* get me in trouble over *my* choices.  *They* get themselves into trouble over *their* choices.  All I'm doing is giving them a choice.  It's up to them.  I can't be held responsible for their bad choice and vice-versa.

---

### Post by ardvark71 on 2006-12-09
Hi gjtoth...

I can tell you are seriously ticked though...sounds like your friends and loved ones have been a huge source of frustration over this. :( 

I've been down the same route myself. In an individual's mind, a computer has a set number of purposes, and like you've alluded, they can either be good....or they can be bad. And a lot ot times, it's extremely difficult or impossible to tell (or teach) them otherwise. I've had to clean up or reinstall many a copy of Windows because of spyware and/or viruses because they weren't willing to give up doing what caused those "infections" in the first place. Each time, I would shake my head and think, "ok, it's your money." But after a while, though, these people would stop calling me, I assume, because they got tired of having to shell out money to keep fixing the same thing.

To be honest, I never tried to sell Linux to any of my customers because there is still no way an average user is going to begin to understand or put up with the "command line" or any of the other Linux complexities.

Best regards...

:KS

---

### Post by JimS on 2006-12-09
...
I'm 68 years old and have been using computers since the 60s.

I say set up Ubuntu, Xubuntu, Kubuntu, DSL, or Puppy
and let them run with it.
Show them via "livie CDs".

IMHO - once set up - Linux is just as easy as Windoz
and without the headache of virus attacks.

Set up only those programs they need.
Show them how to use them, if required.
Clear away the rest.

My wife uses both Linux and Windoz and sees no real difference 
except that Ubuntu boots up quicker and runs faster,
even thou it is on the slower PC.
She just uses the PC for email and paying bills.
Thunderbird and Firefox is all she needs.

KISS = keep it simple......

...

---

### Post by mhenriday on 2006-12-18
**Tim_Olaguna** and other contributors to this thread might find a recently published article, '[Microsoft stranglehold on disabled market is broken]("http://blogs.zdnet.com/open-source/?p=882"),' by ***ZDNet***'s Dana Blankenhorn, of interest...

Henri

---

