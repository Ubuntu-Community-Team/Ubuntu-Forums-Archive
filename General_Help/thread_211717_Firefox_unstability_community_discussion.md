---
title: "Firefox unstability community discussion"
date: 2006-07-08
forum: General Help
---

### Post by nix4me on 2006-07-08
Firefox and Flash still has issues.

I am growing tired of the random crashes of Firefox when viewing flash content or sometimes for no reason.  There are numerous posts on these forums about the problem.  There are also numerous posts on the Debian, Fedora and Gentoo forums about the same issue.

We as a community need to come up with a way to find a solution to the problem.  I think it is the fault of both Firefox and the flash plugin.  I also think Firefox has sold out to the Windows environment because they don't seem to be interested in the problem at all.  There are numerous posts on their bugtracker and nothing has been done.

I would like to use this thread as a discussion place to perhaps come up with some options/solutions.

Any ideas?

nix4me

---

### Post by Jasper Houtman on 2006-07-08
Set it up to clear all private data everytime you close firefox. Mine had a habit of crashing and slowing down when the cache was filled up to it's limits.

---

### Post by nix4me on 2006-07-08
Mine crashes randomly after being open for like 2-3 days.  Sometimes all by itself.  Other times it will last 5 or more days.

Perhaps its time to start considering Epiphany.

nix4me

---

### Post by Culito on 2006-07-08
Mine doesn't take that long.  It usually crashes once or twice a session - I don't think it's strictly related to flash on my end.

I'm lovin' that "restore crashed session" feature.

---

### Post by Boomy on 2006-07-08
Firefox seems much more stable for me after installing the "fasterfox" extension. It's pretty stable on my system, I had a few crashes before installing the extension, but nothing major.

---

### Post by dartakaum on 2006-07-08
> **Culito said:**
> Mine doesn't take that long.  It usually crashes once or twice a session - I don't think it's strictly related to flash on my end.

I'm lovin' that "restore crashed session" feature.

what feature is that? how to activate it?

---

### Post by vem0m on 2006-07-09
mine doesn't crash it did in windows but that is due to windows itself it lags up due to a script(flash i belive) so its not firefoxe's nor mozilla's, nor Linux problem, its Macromedia and thier refuseal to put decent support out there for Flash on linux and at least make a hot fix till they make a new plugin it all lies in thier hands till either an opensource project gets a decent one running or they release a newer player(they have no plans till 9)

---

### Post by aysiu on 2006-07-09
Mine doesn't crash, but I have seen a few threads where it has crashed for other people. It appears to be a real problem, if not a widespread one.

In other words, I don't think it's something everyone's experiencing, but it's not one or two isolated incidents, either.

---

### Post by kripkenstein on 2006-07-09
I wonder if the crashes are related to the Gecko rendering engine, or the rest of the FF code.

Perhaps the people experiencing these crashes could try Epiphany for a few days. It uses the same Gecko engine. Then we would know where the problem lies.

---

### Post by vem0m on 2006-07-09
see we all use flash as does most pages it is with the flash i can say that with 75% surity as it causes FF to freeze up and crash it has only done that on flash sites but anyways u guys do a lil more testing i am off to bed :P

---

### Post by Arisna on 2006-07-09
I experienced the Flash-crash issue under Gentoo (I don't have, or want, Macromedia's flash plugin on my Ubuntu install).  This is the solution I got from Gentoo's forums:

```
cat 'export XLIB_SKIP_ARGB_VISUALS=1' > /etc/env.d/09flashfix
```

However, Ubuntu does not have any /etc/env.d, so I do not know if/how that might help this discussion.

I also noticed while browsing some SVG clipart recently that other types of SVG content seem to trigger the crash, too, not just Flash.

Further, the same thing happened to me when I used Epiphany.

---

### Post by nanotube on 2006-07-09
well, i have seen firefox misbehave due to flash, (sometimes due to the mplayer plugin, too.)
but you can "almost" lick this problem if you install the "flashblock" extension. that makes firefox not load flash, unless you specifically tell it to. that way you won't be getting a dozen flash things trying to load at once, and can only look at the necessary ones. 

so i run firefox for weeks at a time, without any crashing, probably in no small part thanks to flashblock.

---

### Post by nix4me on 2006-07-09
Interesting comments.  It seems more widespread than I thought.  I do not think blocking flash is a viable solution though, its only a bandaid.

nix4me

---

### Post by mlind on 2006-07-09
I think the problem is with flash plugin, not firefox itself. I rarely browse on flash sites and firefox haven't crashed for me since Dapper flights.

---

### Post by hanexar on 2006-07-10
> **Arisna said:**
> I experienced the Flash-crash issue under Gentoo (I don't have, or want, Macromedia's flash plugin on my Ubuntu install).  This is the solution I got from Gentoo's forums:

```
cat 'export XLIB_SKIP_ARGB_VISUALS=1' > /etc/env.d/09flashfix
```

However, Ubuntu does not have any /etc/env.d, so I do not know if/how that might help this discussion.

I also noticed while browsing some SVG clipart recently that other types of SVG content seem to trigger the crash, too, not just Flash.

Further, the same thing happened to me when I used Epiphany.



Try to add this line to your /usr/bin/firefox

```

export XLIB_SKIP_ARGB_VISUALS=1 
```

Put it right before the exec line (the last line).

I have to put it back everytime there's a firefox update, otherwise I'm experiencing random crash.

---

### Post by guine on 2006-07-10
Since upgrading firefox to version 1.5.0.4 through automatix firefox has become very unusable for me due to constant crashes and the loss of the ability to close tabs with a middle click was quite annoying.  I didnt have any of these problems before upgrading and I have been forced to switch to opera because of how much firefox is crashing right now.

---

### Post by s|k on 2006-07-10
It happens with Epiphany as well, same crashes. It will usually be Flash, or it can be Evince, or mplayer. I think there is a bug, and it's not necessarily with just the Flash binary. With Epiphany it's not so bad though because sessions are usally restored, unless I was logged into something. I wish this problem was fixed though.

---

### Post by hanexar on 2006-07-10
Just realise that I still have random crashes even with the export line...  It mainly occurs when I am away and I got multiples message in gmail (chat).  Could it be associate with the aoss sound device?

---

### Post by WorLord on 2006-07-10
The aoss sound device workaround (to get sound in flash) can make FF VERY unstable - UNLESS one stops using ESD altogether (see "how to make sound work properly in GNOME" section of ubuntuforums.org).  

In fact, if one makes FF use "aoss" as the sound device, one can force FF to hang usually by watching a Flash movie, and then navigating the page to something else (either the back button, or forward button, or new address).  Sometimes this just makes the FF window vanish entirely.

WITH the ubuntuforums dmix/no-esd fix, my FF has been very stable, flash works very well, sound is mostly syncronized (I see maybe 5% of all flash movies that are out of sync with the video).

But, yeah.  I think its definitely flash-talking-to-sound issue.

---

### Post by Polygon on 2006-07-10
> **WorLord said:**
> (see "how to make sound work properly in GNOME" section of ubuntuforums.org).  


where can i find this post? i tried searching and couldent find it

---

### Post by dirtvoyles on 2006-07-10
I have been experiencing the crashes with FF since the *.4 update.

Flock does not have the same issue, and I have the same extensions in both. I wonder what all has been changed and if that has anything to do with it.

---

### Post by Tasu on 2006-07-18
IMHO it's flash plugin fault! A prove for that is this site:

[http://www.lacunacoil.it/etc/flash/main/main.htm](http://www.lacunacoil.it/etc/flash/main/main.htm)

It crashes either in Firefox or in Konqueror at the same animation (about 30seconds after the animation starts.
Those crashes happened even before I had to format... and the only constant was the flashplugin-nonfree... since I used more than one browser... and both borwsers crashed.

This said... what can we do? A part from revolutions? ;-)

The problem is the closed sourceness of that crappy player and the widespread adoption of flash content on the web... seen that's a flash problem, we can do nothing, we have non code to fix! -_-

---

### Post by curtis1005 on 2006-07-18
I used to use the firefox package from respo, some extension were working strangely, like html validator
Binary from mozilla.org works slightly better, however both of them consume too much system resources.

Anyone use "swiftfox"?? it is a cpu optimized version of firefox..I've been using for few months...it works much better than the original one.

It runs smoothly, even I have 60+ extension installed. :-D

---

### Post by Skia_42 on 2006-07-18
I have come across crashes in firefox when visiting certain web pages. I cannot view Myspace profiles in Firefox or the program with quit on me. Opera however does not crash, I am curious if Opera solves anyone elses problems. Any experiences?

---

### Post by _simon_ on 2006-07-18
Just viewed that site in the latest weekly opera build. It doesn't crash the broswer but the content crashes to a grey box after playing for a short while. Probably requires the latest flash.

---

### Post by Erunno on 2006-07-18
> **dartakaum said:**
> what feature is that? how to activate it?

Hope that the OP still reads this thread :) 

Anyway, Firefox doesn't have build-in session management but I read that it is planned for Firefox 2.0. In the meanwhile I'd suggest to use the excellent [Tab Mix Plus]("https://addons.mozilla.org/firefox/1122/") extension which adds basically Opera's tab and session functionality to Firefox (and some additional options to boot).

Or you could use Opera in the first place which is an excellent browser (far better than Firefox in my opinion) if you aren't a zealot who refuses to use closed source programs.

On topic:

I have nothing really to add other than my Firefox also tends to crash on certain flash sites.

Cheers,
Erunno

---

### Post by vem0m on 2006-07-18
i have since then had to move over to Opera becuase of the frenquent lockups with firefox that last anywhere from 5-15 seconds to the speed really being slow all the way to the last reason of it not being quite right

---

### Post by petertc on 2006-07-18
I have found that when my son is playing flash games on the BBC children's web site it can crash, 
it does seem random as to when it crashes. 

some times it does crash when you are pressing a key that makes a sound, 

I had to get the oss setup to get any sound at all from firefox with flash

---

### Post by Afief on 2006-07-18
Wouldn't Gnash be an option?

The none-free flash player only plays V7 flash movies. That's the very same version Gnash plays, and it is open source, so if something DOES crash fixing it is possible.

Gnash isn't available in the ubuntu repositories though, so it is not trivial for everybody to install it. Since i don't deal with many flash webpages i haven't tried it but it's definitly an option.

Only my 0.02$

---

### Post by bruenig on 2006-07-18
The memory leaking is the root, I believe, of many of the problems. Everytime firefox crashed, I opened up the System Monitor and found that it is taking up some crazy amount of memory. Whereas it is normally running conservatively at 50 MiB, when it locks up on me I have seen it as high as 150 MiB.

I use swiftfox now and although it has the same problems, I have found that it happens much less frequently.

---

### Post by vem0m on 2006-07-18
> **Afief said:**
> Wouldn't Gnash be an option?

The none-free flash player only plays V7 flash movies. That's the very same version Gnash plays, and it is open source, so if something DOES crash fixing it is possible.

Gnash isn't available in the ubuntu repositories though, so it is not trivial for everybody to install it. Since i don't deal with many flash webpages i haven't tried it but it's definitly an option.

Only my 0.02$


its a 0% usable option as it is uncompatible with most flash movies and does not work that well at all and from what i gather beyond that known stated fact from the developer is that it is in EARLY development and unstable/unusable

---

### Post by Skia_42 on 2006-07-18
> **bruenig said:**
> The memory leaking is the root, I believe, of many of the problems. Everytime firefox crashed, I opened up the System Monitor and found that it is taking up some crazy amount of memory. Whereas it is normally running conservatively at 50 MiB, when it locks up on me I have seen it as high as 150 MiB.

I use swiftfox now and although it has the same problems, I have found that it happens much less frequently.
I am happy you mentioned looking up your memory in Sytem Monitor after a crash. I get a spike in memory after a crash as well.

---

### Post by zba78 on 2006-07-19
I use swiftfox and I do believe that the problem is related to sound + Flash. My swiftfox shortcut always launches **aoss swiftfox** and although most flash is ok some sites (like the cebeebies website mentioned earlier ([http://www.bbc.co.uk/cbeebies/)](http://www.bbc.co.uk/cbeebies/))) can cause swiftfox to crash altogether.

One thing that has really helped is the FlashBlock extension. I especially like the feature to remove the flash altogether (although that has nothing to do with this topic)

---

### Post by deadgobby on 2006-07-20
My FF crashes all the time. It can be when I DL a ISO file or just on Yahoo. I would love to fix this crash problem. Can any give any put how to solve this problem? It has happen to me just typing a message on Ubie forums.
Gobby

---

### Post by Mykewl on 2006-07-24
I have  been using swiftfox (with fasterfox installed)
and have had very few, like 2 or 3 crashes. I dont remember
if they occured on flash intensive sites though.

---

### Post by viciouslime on 2006-07-25
So many people here seem to have frequent crashes with FF, but mine has crashed three times in the last 5 months. All three were because of flash, but generally speaking it is extremely stable. I use the computer (and firefox) every day. It seems weird that you all have such major issues with it. Could it possibly be something else causing this to happen? Or is it that you all use an awful lot of flash sites? :confused:

---

### Post by viciouslime on 2006-07-25
Lol I just tried the cbeebies website and guess what. Yup, my fourth crash in 5 months. I hope adobe get a move on with flash 9...

My sister happens to use that site a lot under windows as well, so now I know I can't put ubuntu on her PC :(

---

### Post by slimdog360 on 2006-07-25
With the session saver, in both firefox and opera, I watch how much ram it uses and when it gets to about 100MB i just close the browser and then restart it. It only takes a second and free up a lot of ram and stops it from crashing.

---

### Post by hanexar on 2006-07-27
All the crashes involve flash + sound. I am using aoss sound setting with firefox. Does other people crashing use the same setting for the sound?

I'll make some test next week.

---

