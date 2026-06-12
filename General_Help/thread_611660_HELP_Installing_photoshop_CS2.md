---
title: "HELP: Installing photoshop CS2"
date: 2007-11-13
forum: General Help
---

### Post by RealEmotionX on 2007-11-13
I have seen some stuff online, All WINE related about installing CS2, involving registry Keys and all sorts of stuff.

I have tried a few methods but nothing seems to stick but I know its possible. 

When I try to install from Photoshop_CS2.exe in wine, wine opens up a black box, this box once opened some sort of downloading dialouge

when I followed this method
[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)
the part where I recode the .reg file gave me errors, I skipped over it and photoshop opened but with a black window and visable tool-bars.

anyone with some straight forward answers?

---

### Post by sonofusion82 on 2007-11-13
btw, unless you are really serious with professional graphics, why not try FOSS alternatives like gimp or krita. :-)

---

### Post by anaconda on 2007-11-13
search the net for "portable photoshop" You will find instructions how to make your photoshop portable (or where to find a readymade version) , and then that should work with wine.

---

### Post by RealEmotionX on 2007-11-13
> **sonofusion82 said:**
> btw, unless you are really serious with professional graphics, why not try FOSS alternatives like gimp or krita. :-)

I am in college, I am pursuing Graphic Arts as a career. gimp and Gimp shop just terrify me 

[www.RealEmotionX.net](www.RealEmotionX.net)

---

### Post by mikerobinson on 2007-11-13
I had the same problem. Even with PS7, which should run basically perfectly under wine, had a few annoyances. I just ended up installing VirtualBox with CS3 on it. That way I can run basically any windows program that doesn't work in wine. I then set up an FTP server on Ubuntu to transfer files since networking didn't work correctly.

---

### Post by trishacupra on 2007-11-21
Try using Crossover and Portashop - I've posted a way to get a fully functional CS2 mostly working under Crossover (not WINE) on these forums. Here's the relevant post:

[http://ubuntuforums.org/showthread.php?t=207430&page=2](http://ubuntuforums.org/showthread.php?t=207430&page=2)

This is as good as I think it can get at the moment. The text tool is a bit buggy, but most of the time it's ok.

I can load and play Actions, but the actions I loaded disappear next time I open it. In fact, no new settings really seem to stick consistently - it's kind of like opening up CS2 after a fresh install each time.

If you can run CS2/CS3 in Virtualbox or something similar, I would do that. My laptop doesn't seem to like Virtualbox, so I'm stuck with dual boot for the times when CS2 in Linux gets too annoying.

---

### Post by hikaricore on 2007-11-21
> **RealEmotionX said:**
> I am in college, I am pursuing Graphic Arts as a career. gimp and Gimp shop just terrify me

What exactly (and I'm talking about pre-Bloat here, meaning Photoshop 7) can Photoshop do that GIMP can't do (and better), aside from CMYK colour?

I won't touch Photoshop after about version 7 (and barely that) with all the useless crap and restrictions they've placed in it.

---

### Post by desudesudesu on 2007-11-26
> **hikaricore said:**
> What exactly (and I'm talking about pre-Bloat here, meaning Photoshop 7) can Photoshop do that GIMP can't do (and better), aside from CMYK colour?

I won't touch Photoshop after about version 7 (and barely that) with all the useless crap and restrictions they've placed in it.

Better UI that has a lot more plugins, effects that are not hidden in endless amounts of menus, a simple and unbloated side bar, and a feature to record and playback actions to recreate effects on various images.

I'm not going to relearn to use GIMP with it's GIMPed UI just because it's free and open source.

Seriously, I'm noticing that more and more linux users are becoming as smug as Mac-zealots. 

He is asking how to install an industry standard program that he is very familiar with, yet you have to go and sidestep the question and answer him with another question.

Let me ask you this. Why do you use Linux?
What can linux do that OS X can't do (and better) aside from being free?

See, not only did you not even bother to help answer his question, but you also insulted him, and a lot of other Photoshop junkies.

I am sorry that I am being so blunt and harsh, but I am offended.

---

### Post by Slakker on 2007-11-26
And you're just as much a fanboy as he is...The GIMP is a perfectly suitable program, and the interface is, in my opinion, a lot more intuitive than Photoshop.  That said, I understand that Photoshop is the industry standard, and in a lot of ways more powerful than The GIMP, however, if you need to run Photoshop for a professional purpose, it'd be best to set up a dual-boot with Windows XP so that you can run it in its native environment.  I'm probably going to get flamed for suggesting windows, I know, but software compatibility is definitely a benefit.

---

### Post by hikaricore on 2007-11-26
> **desudesudesu said:**
> Better UI that has a lot more plugins, effects that are not hidden in endless amounts of menus, a simple and unbloated side bar, and a feature to record and playback actions to recreate effects on various images.

"Better" is all a matter of opinion.  I myself haven't seen anything better about Photoshop since version 7 was released.  It was a beautiful fully functional interface that had everything that you'd come to expect from photoshop, and I had a great amount of respect for Adobe at the time of its release.  However after that it went downhill.  More functions that weren't really true to what Photoshop had become known to be, it became bloated and slow and *gasp* overrated.

I STILL to this day use only Photoshop 7 at my office, alongside GIMP it's everything I'll ever need.

Plugins for photoshop have always been available direct from Adobe or even third parties for pretty much anything you can imagine.  Just because Adobe stopped selling most of them as a separate product impressed you?  Come on give me a break. 

True that the GIMP interface has long been awkward and had a learning curve to it, but it's improved since the last time you've more than likely used it.  All the effects as you call them are finally localized, and did I mention you can write your own with a simple text editor if you learn the API?  I'd love to see the day you can write Photoshop plugins in Notepad.

But anyway as you can see, what's better for you may not be better for some.  I suggest you lighten up.

> **desudesudesu said:**
> I'm not going to relearn to use GIMP with it's GIMPed UI just because it's free and open source.

That's fine no one's forcing you to.

> **desudesudesu said:**
> Seriously, I'm noticing that more and more linux users are becoming as smug as Mac-zealots. 

Look at the pot calling the kettle black.  You just attempted to rip me a new ******* for asking a simple question.  If you want to be a PS fanboi and get your nickers in a twist every time someone questions you almighty Adobe, more power to ya.  But I suggest next time you rethink making it a public spectacle just to get people to pay attention to.  The members of this forum have little tolerance for this sort of chite, and I have even less.

> **desudesudesu said:**
> He is asking how to install an industry standard program that he is very familiar with, yet you have to go and sidestep the question and answer him with another question.

If you didn't notice, others had already pointed him/her to appropriate reading material on the subject of installing unsupported software via WINE.  There was no reason for me to go any further into it and just be redundant.  However I did notice the thread and I was curious for an answer, which by the way is perfectly within my right... so not really caring one way or the other or even expecting a response from the OP, I bothered asking anyway.  Are you getting the point yet.

> **desudesudesu said:**
> Let me ask you this. Why do you use Linux?
What can linux do that OS X can't do (and better) aside from being free?

I can't believe you have the balls to ask me that.  I also don't have time or the interest in writing you a 5 page essay on my personal/business computer needs and why Ubuntu/Linux/FOSS works for me.  You my friend are a hopeless troll, and I won't waste any more time responding. (note this was the last section I replied to, below is the first)

> **desudesudesu said:**
> See, not only did you not even bother to help answer his question, but you also insulted him, and a lot of other Photoshop junkies.

I am sorry that I am being so blunt and harsh, but I am offended.

I didn't insult anyone.

Personally I'm insulted that Adobe caved to the US government and implemented scanning restrictions (before scanner manufacturers did) on what can be scanned.  Not that I have any use to ever scan US currency, but it's still the point of the matter that they did what they did.  I can't tolerate censorship of any kind and I lost all respect for Adobe and their products when they sold out. 

On the topic of you being an ***.  I don't really mind.  But next time you have a problem with a question I ask in an issue you aren't involved with, please send your flames to me VIA PM.

--Aaron

---

### Post by RealEmotionX on 2007-11-27
Wow. . .

I just like programs I am familiar with, I dont auctually run Windows XP anymore besides for  Final Fantasy XI. I am in College classes that teach me in Photoshop, I am not going to go around and relearn everything I learn in class IN Gimp.

And Truthfully the comment you posted was very condescending. . . I like Photoshop, I dislike Gimp. I diddnt ask for people to come in here and get all Pro-Open source or whatever on me. I want to be able to use Linux to its highest potential and for me that means using photoshop.

---

### Post by RealEmotionX on 2007-11-28
After a sleepless night, I got Photoshop CS2 running in Linux, only problem I encounter is even with Microsoft core fonts, when I use the font tool, it crashes.

any suggestions?

---

### Post by Joe.Kent on 2007-12-07
Very well put Aaron, besides, isn't this an *nix based forum? On a side note, I love GIMP, but at work I'm forced to use PS, and I'm trying to get them to make the switch, so my question is this: Is there a way to run GIMP on XP?

---

### Post by ragadanga63 on 2008-01-08
There's a Windows version of GIMP.

---

