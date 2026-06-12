---
title: "ATI Radeon X1400 ??"
date: 2007-05-30
forum: General Help
---

### Post by JC_510 on 2007-05-30
I know there are some help topics on ATI X xxxx graphics cards, but I have seen a computer with an **ATI Mobility Radeon X1400 HyperMemory** graphics card, and simply wanted to ask whether or not anyone has got it up and running with Ubuntu, and if you have, was it relatively straightforward, or did it require special geek powers?

Thanks :D

---

### Post by pertti on 2007-06-01
I have that very same card on my Dell 6400/E1505 laptop. There was a problem with Feisty Fawn, which prevented Ubuntu from starting normally. It may have been already resolved with the updates, but since the Feisty Fawn Live CD hasn't been updated you'll still have to sweat a bit to get the card working. Maybe you could try installing first Edgy Eft and the update to Feisty (I had no problems with my X1400 updating to Feisty).

So, all in all it's not really hard, but it's not straightforward either.

---

### Post by JC_510 on 2007-06-02
Thanks for the reply.

By "You'll have to sweat a bit..." how much do you mean?!

I've never used a command line properly (followed a few web tutorials with CMD on windows, but thats about it), and Ive never used Ubuntu either.

I'm also looking at the Dell 6400 laptop. Is the ATI card much better than the other Nvidia one? (i.e. is it worth getting?)

If it genuinely is worth the upgrade, and its not **too** hard to get it working properly and as it should, then I'll get it.

---

### Post by Ub1476 on 2007-06-02
If you have ATI X1400 128mb and 512 extended (HyperMemory) you may swet. If you have ATI X1400 256mb with 512 extended, you may not.

Anyways, follow this guide if X server crash: [Linky]("http://ubuntuforums.org/showthread.php?p=2684704#post2684704")

No need for super-geek powers.

Oh and, Beryl works really smooth with X1400:D

---

### Post by JC_510 on 2007-06-03
Thanks for the tips. I will not pretend to be an expert, because I am far, far from it, but are you saying that all I have to do is follow the instructions on that link, and all will be fine?

Im a complete noob with configuring hardware and similar stuff, so if it is going to cause a great deal of pain and head-scratching, I may just not bother and go for the  (admittedly not-as-good) Intel 950 alternative on the Dell website.

Having said that, if the improved graphics really will be worth it for gaming on the XP partition of my laptop, then i'll give it a try :confused:

---

### Post by helliewm on 2007-06-03
In the last month I bought a Dell Inspiron 9400 it has an X1400 ATI Graphics Card. There was a problem with Feisty so I downloaded Drapper upgraded to Edgy then upgraded to Feisty. I did this to ENSURE I had a working internet connection. I then followed theie instructions EXACTLY  ( I did not obviously need to use a Feisty Installation disc, so skipped the bit about about installing the Live Feisty disc and booting it up etc) by typing them into the terminal. The key thing is copy all the instructions EXACTLY into the terminal. It will be a black screen with name of the computer and a dollar sign, its just a terminal screen that you will automatically get after upgrading from Drapper to Edgy and Edgy to Feisty. When you get this terminal screen just type all the commands exactly as in the thread below. You need a live internet connection for this to work hence why I kept upgrading from Drapper.   

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

The x1400 ATI Card works brilliant with, no problems at all. Go for it and post on the forum with any problems.

I was lucky as I also have a Desktop computer was able to refer to the forums from that whilst installing Feisty by upgrading from Drapper and typing the commands in the terminal.

Go for it, the problems are solvable, just require a little patience. The end result is brilliant I have a laptop that works out of the box now. Beryl works too. I am really really pleased with it.

Helen

Ps I have just noticed you are the UK try EComputers on Ebay you will get the same brand new Dell with full warranty etc cheaper than buying it from the Dell website. I paid £500 for by Dell Inspiron 17 inch screen. It was advvertised in The Times last week ( the absolute exact same machine) for £679! EComputers service was excellent.

PPs If you are looking for a Desktop try Palicomp on Ebay they purpose built my Desktop to my specification last year I paid £675 for about £1000 machine.

I would go back to both these companies both are excellent and are far cheaper than the UK High Street. I would not go down the High Street again after these 2 excellent deals.

---

### Post by Ub1476 on 2007-06-03
Just follow the steps in my guide:p.. [This one]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

No need for internet connection, and the steps are very clear, I've even made examples.;)

---

### Post by helliewm on 2007-06-03
I had tried that it did not work for some reason. This one did though.

[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

Helen

---

### Post by intMain on 2007-06-03
I have an Acer Travelmate 4674WLMi with a Mobility Radeon x1400 with up to 512MB HyperMemory and I just followed the wiki guide from the Ubuntu website to get XGL and Beryl/Compiz running.  But if you don't care for candied desktop you would just have to enable the Restricted ATi drivers and you will be ready to go.

Only crappy thing is that XGL and gaming is not fun.  Must go back to default Gnome desktop to play 3D games.

---

### Post by JC_510 on 2007-06-03
Thanks for all the replies :)

From what everybody has said, I think you've managed to change my mind about ATI! All I saw on the forums concerning ATI cards was bad news, but as there are some people here that have obviously got this card working without any hitches, I think I'll give it a try!

[quote=helliewm]Go for it, the problems are solvable, just require a little patience. The end result is brilliant I have a laptop that works out of the box now. Beryl works too. I am really really pleased with it.[/quote]I was also looking at Beryl, so Im glad to see that it works ok! :D

[quote=helliewm]Ps I have just noticed you are the UK try EComputers on Ebay you will get the same brand new Dell with full warranty etc cheaper than buying it from the Dell website. I paid £500 for by Dell Inspiron 17 inch screen. It was advvertised in The Times last week ( the absolute exact same machine) for £679! EComputers service was excellent.[/quote]Thanks for the info, I'll have a look at them!

[quote=intMain] Only crappy thing is that XGL and gaming is not fun.  Must go back to default Gnome desktop to play 3D games.[/quote]Games will play ok on Windows with this card though wont they? I was planning to dual boot my laptop with Ubuntu and XP.

---

### Post by intMain on 2007-06-18
> **JC_510 said:**
> 
Games will play ok on Windows with this card though wont they? I was planning to dual boot my laptop with Ubuntu and XP.

Yeah the X1400 will play OK in Windows.  No amazing performance.

---

### Post by rleblanc1812 on 2007-12-07
Hi. I'm new to Gutsy and I'm having a few problems getting my ati x1400 to work. I've looked all over this forum (it's huge!) and I've tried several things, but I still can't get my video driver working correctly.

I have a dell Inspiron 9400, ati x1400 256MB.  I've tried Envy as well but it just comes up with a white screen after I boot. I can still move the mouse, but everything is white. I ended up dropping to command line to un-install envy's ati driver.

Can someone please just point me to a page/guide/link that will help me get my video working??

Thanks

---

### Post by KeeNeR on 2007-12-12
I don't know if it can help ...

If you have enabled the restricted ATI drivers in gutsy and it doesn't work,

you can try to follow [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").


I got my inspiron 9400, ati x1400 working on Gutsy with the drivers at the page mentioned above. (solution 2). The problem is the hibernate has stopped working with the last kernel version and this driver.

---

### Post by rleblanc1812 on 2007-12-14
Thanks, I've tried that link before without any success. But I'm happy to say everything is working fine now. It took a few tries but I believe that the problem had to do with my external monitor! When I enabled restricted drivers after a fresh install and my external monitor was plugged into my laptop it would set the resolution to 640x480 and I couldn't change it. At that point I would un-install the restricted driver. But I tried it again without the monitor plugged in and it worked perfect! Strange. I was going to try a fresh install to see if it would do the same thing again, but I'm too afraid to mess up my system :P Works perfect with compiz right now. 

Just suspend not working, but I can totally live with that...


Thanks

---

