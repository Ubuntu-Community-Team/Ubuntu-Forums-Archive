---
title: "When will the graphics issues in Firefox 3 on ubuntu get fixed?"
date: 2008-06-26
forum: General Help
---

### Post by sancho panza on 2008-06-26
The page zoom feature on firefox 3 on ubuntu is broken compared to firefox 3 on WinXP as [compared here]("http://farm3.static.flickr.com/2162/2481984708_dedc30e9df_o.png").

This problem is due to a bug in X.org, as [discussed here]("http://blog.vlad1.com/2008/03/18/a-little-more-cairo-just-for-you/").

The bug seems fixed in the forthcoming version of x.org, but does anyone know when that would happen? Can anyone suggest simple ways to fix this graphics issue in firefox 3 without breaking x.org or the gui?

Cheers!

---

### Post by sancho panza on 2008-06-29
bump?

---

### Post by overdrank on 2008-06-29
> **sancho panza said:**
> bump?
> The page zoom feature on firefox 3 on ubuntu is broken compared to firefox 3 on WinXP as [compared here]("http://farm3.static.flickr.com/2162/2481984708_dedc30e9df_o.png").

This problem is due to a bug in X.org, as [discussed here]("http://blog.vlad1.com/2008/03/18/a-little-more-cairo-just-for-you/").


Hi and I am a little confused. The first link you posted shows bad graphics in Ubuntu firefox. But the seconded link the graphics look bad in windows not Ubuntu. Is this just a issue with you resolutions in Ubuntu. :confused:

---

### Post by Pjotr123 on 2008-06-29
I think this can be repaired by letting Firefox zoom only the text:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 6 )

---

### Post by vanadium on 2008-06-29
> I think this can be repaired
This is a workaround rather than a repair.

When it will be fixed? In Open Source, the "when" is always unsure. Could be tomorrow, could be two years from now.

---

### Post by sancho panza on 2008-06-29
> **overdrank said:**
> Hi and I am a little confused. The first link you posted shows bad graphics in Ubuntu firefox. But the seconded link the graphics look bad in windows not Ubuntu. Is this just a issue with you resolutions in Ubuntu. :confused:

The second link discusses the latest updates in firefox/windows/ubuntu which look good. But those updates have not been applied to the current release of ubuntu. My question is as to when those latest bug fixes would reach mainstream, and if there's any way I can apply those updates myself.

The text only zoom screws up the page formatting on most webpages and is a poor substitute to page zoom.

Thanks,

---

### Post by Morientes on 2008-07-01
I am also very interested in this!

I tried Firefox 3 on Windows XP and was very happy with the new zoom.
So getting Firefox 3 was actually the main reason I upgraded my 7.10 to 8.04.
Therefore I am quite disappointed with the fact that the zoom is somewhat worthless as it is now. Just zoom in one time and all images look really ugly.
I know I could use the text zoom, but the other feature is really cool.
I hope it will get fixed in the near future.

---

### Post by soccerboy on 2008-07-01
If the problem has been fixed upstream, it will be fixed in ubuntu in the next release (8.10)

---

### Post by jimv on 2008-07-01
I don't understand the problem.  It works just fine for me.

Chances are that it's a problem with your machine, not something systemic in Firefox or Ubuntu.

EDIT

OK, I now see what you're talking about.  This ISN'T a problem or a bug, Windows appears to be smoothing the image as you zoom in, and Ubuntu enlarges the image without smoothing so you see the pixels.  It's just a difference in the way Windows/Xorg renders graphics.

They may add a feature that makes things smoother in another Xorg release.

---

### Post by Morientes on 2008-07-01
Hm, if it is a problem with our machines, I wonder what might be the cause.
Could it be the drivers used? (I use Nvidia 173.something) or the xorg conf? Or somehting similar? OR something completely different?

EDIT: ok I saw that the post above was edited. I believe that the images in Win XP look WAY better. You could be right about the smoothing, but it would be nice if the same effect could be achieved in Ubuntu!

---

### Post by sancho panza on 2008-07-01
As mentioned in the [second link in the first post]("http://blog.vlad1.com/2008/03/18/a-little-more-cairo-just-for-you/"), the issue lies with the xorg server which renders the page zoom. That link also mentions that the issue has been fixed, but would only be available in the next xorg release.

I'm hoping someone reads the details in that second link and can figure out a way to fix this problem without having to wait for the next x.org release.

Cheers!

---

### Post by cariboo on 2008-07-01
Have you gone here:

[http://www.x.org/wiki/](http://www.x.org/wiki/)

to find a fix?

Jim

---

### Post by sancho panza on 2008-07-01
> **cariboo907 said:**
> Have you gone here:

[http://www.x.org/wiki/](http://www.x.org/wiki/)

to find a fix?

Jim

I had poked around there a little bit, but did not find enough stuff on how exactly to actually fix the issue. Since I'm not too familiar with linux internals and since x.org is a major component, I wouldnt try fixing this unless I find a detailed how-to that wouldnt break my system.

Thanks,

---

### Post by sancho panza on 2008-07-09
This seems to be on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908") and [Mozilla]("https://bugzilla.mozilla.org/show_bug.cgi?id=422179"), but looks like its going nowhere. Why is this not a priority, Hardy being an LTS and firefox page zoom looking so ugly?

Is there anything I can do besides debugging code to fix this issue?

---

### Post by eival on 2008-07-09
ive noticed that photos dont look as clear and crisp as they did in XP, even tho i set my nVidia settings to max quality, so i have no doubt that if you were to enlarge the photo past its native size that it would look even worse. im betting this is most likely an Ubuntu issue not Firefox, cause Opera for Ubuntu has the same slight degrade in picture quality as well.

---

### Post by sancho panza on 2008-07-10
The issue also exists with page zoom in Opera.
There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908"), but it doesnt seem to be going anywhere. 

I think the issue is with xorg server, but I'm not sure how I could add that info to the bug report, as there are many xorg related packages and I dont know which one is buggy.

---

### Post by asac on 2008-07-22
there are some claims that a new pixmap would fix this. Can you please test if this issue is gone in intrepid? if its fixed there we can look whether a backport is feasible ... or even a SRU if we can extract a minimal patch for this.

Thank you!

---

### Post by sancho panza on 2008-07-22
> **asac said:**
> there are some claims that a new pixmap would fix this. Can you please test if this issue is gone in intrepid? if its fixed there we can look whether a backport is feasible ... or even a SRU if we can extract a minimal patch for this.

Thank you!

The links in my posts above and in the [bug report here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908") do indicate that the bug has been fixed in pixman/xorg. I'm an amateur and I tried updating (config, make, make install) to the latest patched pixman library in hardy, but it didnt work at all. 
I dont have intrepid, so i'll try to ask someone else or try to get the latest iso (?) if i can. 
EDIT: I have posted in the [Intrepid forums here]("http://ubuntuforums.org/showthread.php?t=867161").

Thanks for looking into this.

Cheers!

---

### Post by sancho panza on 2008-07-23
[The post here]("http://ubuntuforums.org/showthread.php?t=867161") claims that this bug exists in Intrepid.

EDIT: That thread also has a parallel discussion on this topic, since it also affects Intrepid.

---

### Post by MadMan2k on 2008-07-23
ubuntu needs a new version of libpixman and the x server recompiled against that. but intrepid has still the same version as hardy.

---

### Post by lusiads on 2008-08-12
You can help promote the idea about solving this problem on Ubuntu Brainstorm [http://brainstorm.ubuntu.com/idea/12125/](http://brainstorm.ubuntu.com/idea/12125/)
:guitar:

---

### Post by sancho panza on 2008-08-12
Thanks to whoever went thru the trouble of posting it on brainstorm. But I think it'll be shot down soon as its not an idea...its a bug. 
[Look here]("http://brainstorm.ubuntu.com/idea/8354/") at what happened when I posted the same problem on brainstorm a while ago.

Cheers!

---

### Post by Morientes on 2008-09-12
bump!
Any news on this?

---

### Post by sancho panza on 2008-09-17
From the lack of activity on this bug on launchpad, looks like this bug will remain in Intrepid too...The actual bug has been fixed upstream, apparently. Despite this, why it hasnt been merged into ubuntu is beyond my understanding.

This bug is seriously affecting my daily browsing as I view most web pages with page zoom as I have a high ppi display.

---

### Post by chris-at on 2008-09-18
If this bug is fixed upstream could somebody please write a tutorial on how to apply this fix yourself?

I've set the default zoom level at 125% because most websites are otherwise unreadable on my 1920x1200 17" display - I'd really appreciate a fix/workaround to get at least the same quality that you get when using Firefox on Windows.

thanks!
chris

---

### Post by sancho panza on 2008-09-18
From what I have seen, it may not be that easy. The fix involves the pixman library used by xserver. Replacing the pixman library does not fix the issue. I think there are some other related files (including xserver) that might need some tweaking and recompilation for ubuntu.
But still, if someone can write a detailed guide, I'd be interested. Whats the most disappointing is that this issue has somehow remained unresolved in Intrepid.

---

### Post by Morientes on 2008-10-20
I agree, if the bug is still in the new Ubuntu, it will be very disappointing.
It is things like this that need to work if Linux is to compete with Windows.

---

### Post by Morientes on 2008-10-31
...and it is in the new (k)ubuntu unfortunately. It's a shame. Let's hope it get's fixed in the not so distant future...

---

### Post by vipseixas on 2008-11-03
> **Morientes said:**
> I agree, if the bug is still in the new Ubuntu, it will be very disappointing.
It is things like this that need to work if Linux is to compete with Windows.

It is really a shame, I am migrating from Windows to Ubuntu now and this bug is forcing me back, since I use FF with zoom in almost all pages because I have a wide-screen notebook, and most of the pages are very small on my display.

There are people that might think this is a minor problem, but it is not! It feels like you are shortsighted person without glasses, very annoying.

[]s!

Vinicius

---

### Post by sancho panza on 2008-11-04
You can also post on the brainstorm page (link in a post above) and the launchpad bugreport. I was hoping that would help, but its taking long to get people to respond there too.

---

### Post by hypnotux on 2008-11-05
I finally switched from Vista to Intrepid 2 days ago which is my first contact to Linux as a user, before I always was "very interested" but too much of a coward to really do the step changing the OS.

Althoug I am very confident with it now, this picture-rendering problem is very very annoying because I use page-zooming on almost every site and I am afraid to get eye-cancer or something worse from this pixeled graphics.

To me this is the only thing that doesn't work as well or even better as with Windoofs.

I read several threads also in other forums describing this issue for Hardy and the bugreport 217908 on bugs.launchpad.net dealig with it and there it was said "A fix is availiable upstream" can s.o. translate this for a Linux-Noob, plz?

As I understand there is no fix or even a workaround that solves this issue, does this "upstream" mean its still in developement? *guess*

I already tried fiddleing around with grapic-card drivers and the xserver-configuration but nothing helped...

Zooming just text is not an option for webpages that have a predefined width cuz then you have just 2 words/line what doesn't make reading easier for me...

Thx and "Hello Community" !

---

### Post by FranMichaels on 2008-11-08
Some people are having problems on the other end.
[http://forums.mozillazine.org/viewtopic.php?f=23&t=664257](http://forums.mozillazine.org/viewtopic.php?f=23&t=664257)

I use the page zoom heavily, it is a great feature.

I think (as one poster in the thread I linked mentioned) is that there should be interpolation for fractional zoom, but not integer.

[Pixel art]("http://en.wikipedia.org/wiki/Pixel_art") best illustrates how ugly the zoom is at like 1.5 without interpolation. Misshapen stuff. At 2x or 3x, it looks perfect.

Unfortunately, if firefox on linux did interpolate, any zoomed image would be "blurred", it should look good for most everything, but not pixel type art...

So in the meantime, just grin and bare it, or go to about:config, type zoom, and change the values it scrolls through.
The problem is a site may be better for viewing overall with a fractional zoom...

The thing I can't get over is, if you click and drag the image on the webpage, the version that floats around, is smoothed... So I dunno honestly what the heck...

The ideal thing would be to use a better algorithm for image smoothing, and make it customizable to toggle on/off for the times where you don't want it (which would probably be rare...)

P.S. For those that want to test to see if they really have this issue
Try this image
[http://mother3.fobby.net/wp-content/uploads/2008/05/may29_c.png](http://mother3.fobby.net/wp-content/uploads/2008/05/may29_c.png)
Zoom, and keep an eye on the text in the image as you zoom.
If it blurs/blends, then you've got interpolation, but it just won't be as sharp as before scaling...
Lastly, running Intrepid Ibex, with firefox *minefield* (the nightlies, so it's about as new as one end-user like me can get!)

---

### Post by sancho panza on 2008-11-12
> **FranMichaels said:**
> 
The thing I can't get over is, if you click and drag the image on the webpage, the version that floats around, is smoothed... So I dunno honestly what the heck...



That...is truly weird. If firefox can zoom it just fine for click-n-drag images, why cant it do it for the regular images? I always keep getting the feeling that the bug-fix for the problem is easier than it first seems.
I'd really appreciate everyone who cares about this bug vote for it [on brainstorm]("http://brainstorm.ubuntu.com/idea/12125/") and [comment/vote on launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908").

---

### Post by not a pipe on 2008-11-19
I hope this gets fixed soon.

---

### Post by Morientes on 2008-11-20
I would also REALLY REALLY love if this was fixed. I think the page zoom feature of Firefox, when I use it in Windows is great. But in Ubuntu it is very bad. My zoom is slow and the images look horrible.

---

### Post by sancho panza on 2009-01-20
UPDATE:
The [bug relating to this issue]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908") is being worked on and needs your help.

All users interested in helping, specially those using the closed source nvidia/ati driver (preferably on intrepid), please run the test described in [this comment]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217908/comments/33") and post the output, along with which version of ubuntu you are using and you display driver (output of the "lspci | grep Display" command or "lspci" command if the first doesnt work) and post your response under that bug-report.

Thanks,

---

