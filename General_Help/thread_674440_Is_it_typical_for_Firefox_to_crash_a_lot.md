---
title: "Is it typical for Firefox to crash a lot?"
date: 2008-01-21
forum: General Help
---

### Post by Frederick J. Harris on 2008-01-21
I'm going to be sticking with 6.1 Edgy Eft for several months yet.  Installed it about 9 months ago, but just got ADSL and managed to get connected (couldn't get dial up working).  Anyway, I really am enjoying the daylights out of Ubuntu, but my Firefox crashes an aweful lot.  I don't have this problem with anything else, just Firefox.  Just basic site navigation doesn't cause it, but logging in to sites, buying anything, that sort of thing.  It gets so bad at times I dual boot to XP to do what I need to do.  My computer has all the latest updates.  I just installed Ubuntu on another computer and it crashes there too.  Is Firefox just a poor and lousy app?  I'm particular to Netscape.  That's what I always used with Windows.  It never acted so badly.  I'm just looking for general info here.  I'm surprised about it.:confused:

---

### Post by shauncdjs on 2008-01-21
its not very typical of firefox to crash often? check and make sure u have the latest release of firefox. if that doesn't work try running an anti-virus program to make sure everythings okay.

---

### Post by glotz on 2008-01-21
Firefox is a direct descendant of Netscape. And mine never crashes. The usual suspects are the Java plugin and especially the flash plugin. Also some extensions can make it crash.

---

### Post by Sidewinder1 on 2008-01-21
Welcome fellow Pennsylvanian! I've been using Firefox for a long time in Windoze and now in ubuntu without any crashes. I'm even running it with "no script" and "Adblock Plus"Once in a while it would 'grey out' but that was before I increased my RAM from 512 to a gig. Best $32.00 I ever spent.
HTH

---

### Post by Frederick J. Harris on 2008-01-21
this is the version i'm using.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20060601 Firefox/2.0.0.11 (Ubuntu-edgy)

Don't know how for sure to check if a newer version is available.  I'll go to Synaptic Package Manager and let it do its thing...:)

---

### Post by amdalex on 2008-01-21
Firefox crashes a lot on my one computer running Edgy Eft and only 256mb of RAM. It would be nice to solve the problem.

---

### Post by tgalati4 on 2008-01-21
I've noticed some flash and java applications have memory leaks.  When your RAM and swap disk get filled, Firefox either freezes or crashes.  A good example is the music player and flash-chat client at [http://www.cocgospel.com](http://www.cocgospel.com).  Run that site for 10 to 20 minutes (try playing the radio) and it's guaranteed to crash.

---

### Post by NT4usB on 2008-01-21
Firefox is rock stable.
That said, I built a new box for mom with 7.10 and Firefox refuses to get driving directions from Yahoo Maps.
Click the [COLOR="Green"]GO[/COLOR] button and Firefox disappears...

I tried various versions of flash and numerous other fixes, reinstalls, etc. and no joy.

I've used it since day one on half dozen different boxes and OS and another 20 or so machines at work, and this is the first one that's been flaky.

I gave up and installed Firefox 3.0 granparadiso on it and Yahoo Maps works now.

Usual culprits are Add-ons, Flash, Corrupted profiles, etc.

Try running in safe mode:```
$firefox --safe-mode
``` If it's better, try creating a new profile: ```
 $firefox --profilemanager (or --profile-manager?)
```
Also try (with Firefox closed), rename localstore.rdf in your profile. Open Firefox it will be recreated.

Flashblock, Adblock, and noskript are your friend...

---

### Post by jesushero on 2008-01-21
Yes, it surely is typical for Firefox to crash 15 times per hour on my computer.. The problem is the Flash plugin and sometimes maybe Java. If I'm working on pure html sites there's never any problem. But flash can make firefox crash so fast it isn't even funny!! 

I have not found any way around this yet, so I just avoid flash websites... Oh, how I sincerely miss the good old days of PURE HTML and nothing but HTML!!!! 

The biggest cause of the problem I believe is bad flash programming. When something's not right in a flash thingie, firefox disappears! 

So I can think of two solutions I'm willing to try: Either force EVERYONE IN THE WORLD to switch back to PURE HTML websites so Firefox will not crash, or fix that f****** flash plugin if I find a good way to do so...

---

### Post by RRS on 2008-01-21
I occasionally get a crash with heavy flash usage, like when jumping thru several YouTube videos, but it's only a minor annoyance.

What bugs me though is I can freeze Firefox at least once a day by visiting these forums. I've got it set up to log me in automatically and it seems to do that fine but locks up just about the time the page finishes loading.

I have no idea why Ubuntuforums.org seems to be the only place that consistantly gives Firefox a headache.

BTW, running fully updated Gutsy with default Firefox, only a few extensions, and never had the problem on my other machine that used Gutsy from Alpha1 thru release, very odd.....

---

### Post by y-lee on 2008-01-21
Firefox seldom crashes on me using dapper with 512M memory. 

Ya might want to see  [Clean up your downloads]("http://www.firefoxtutor.com/36/downloading-freezes-firefox/"), [delete your flash cookies]("http://www.ghacks.net/2007/05/04/flash-cookies-explained/"), and [adjust FF's memory usage]("http://kb.mozillazine.org/Reducing_memory_usage_(Firefox)"). Clear your private data while your at it.

---

### Post by glotz on 2008-01-22
Just remove the silly flash plugin if you installed it. Only ads and other crap use it really.

---

### Post by LaRoza on 2008-01-22
> **glotz said:**
> Just remove the silly flash plugin if you installed it. Only ads and other crap use it really.

Or get Adblock.

---

