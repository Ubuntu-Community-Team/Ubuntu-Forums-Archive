---
title: "libgpod &amp; amarok are so bad at the moment"
date: 2006-11-07
forum: General Help
---

### Post by Old Pink on 2006-11-07
Amarok copies files to the iPod fine, but doesn't tell the iPod where they are, so the iPod can't play them, and they are seen as orphaned. 

I asked around, and apparentley this can be fixed by installing amarok against libgpod-0.4.0, the latest version. 

Installed this, but can't remove libgpod0 without removing ubuntu-desktop etc!!! How do I get around dependencies? Sometimes they are so crap.

Ahh I'm so ******* annoyed. Can't it just be easy?!

---

### Post by hikaricore on 2006-11-07
Dependencies are put there to protect you from yourself, tho you can safely remove ubuntu-desktop but it's not recommended as it can affect system upgrades and distribution upgrades.  If you're comfortable with this go for it, but if something breaks you've been warned.

One thing about libraries (just to let you know) almost every library can be replaced, but never ever replace libc6 or you're just asking for trouble.

---

### Post by Old Pink on 2006-11-07
So I'm having to reinstall ubuntu-desktop and alot of other applications just to fix Amarok? That seems a wee bit ****. In fact, it seems like a Microsoft style fix.

---

### Post by Old Pink on 2006-11-07
Haha, Open Source rules... some quick hacking and all dependencies were forgotten. :)

---

### Post by hikaricore on 2006-11-07
... no i just said that it's safe to remove ubuntu-desktop if needed, just remember there are issues that this causes.  It doesn't remove your desktop or anything silly like that, it's just a package group that represents other default packages on your system.

---

### Post by hikaricore on 2006-11-07
lol yea I do that too I even made a bash script for it (/bin/dpkgedit) :P


> #! /bin/bash
sudo gedit /var/lib/dpkg/status


you wouldn't believe how many times a week i use it

---

### Post by Old Pink on 2006-11-07
All went well, dependencies removed, old libgpod removed and replaced with libgpod 0.4.0, and it turns out that's not even the problem. 

Even using the updated libgpod, I have the same amaroK issues. amaroK is truly crap software at times, it's always the most substantial features that fail when you need them the most, when the stupid little things never break. 

Anyway, emailed amaroK, awaiting reply. <_<

---

### Post by Old Pink on 2006-11-07
Time to get 2 albums onto an iPod... 

Windows & iTunes: 2-5 minutes
Ubuntu & gtkpod & libgpod & amaroK & Sound Juicer & YamiPod: Roughly 6 hours

ALOT more effort needs to be put into iPod - Ubuntu functionality. Why is it possible for iTunes to be so perfect in every way whilst the best linux developers can come up with is half assed attempts that don't even compare. I know I'm being ungrateful and a bit harsh, but seriously, nothings stopping them, if anything they have more at their disposale with the open source element.

---

### Post by PriceChild on 2006-11-07
Never had a problem with Amarok myself...

Are you sure you haven't got dodgy 3rd party packages installed?

---

### Post by Old Pink on 2006-11-07
> **PriceChild said:**
> Are you sure you haven't got dodgy 3rd party packages installed?

Example...? 

And which version of amaroK are you using? The previous one worked well with my iPod, but I had to upgrade to the latest because it didn't work well with my actual collection, every time it scan it crashed and complained to launchpad.

Fix one thing, break another... :rolleyes:

---

### Post by Old Pink on 2006-11-07
[B][SIZE=6]AAAAAAHHHH!!!!! :mad:

[/SIZE][/B][SIZE=6][SIZE=2]Now, all of my cover art has gone. Sometimes, I wonder what will break my window first, the Ubuntu CD, or the computer itself. 

... and all the libgpod fiddling has destroyed gtkpod. If this isn't fixed soon, I'm going to flip. This is ridiculous.
[/SIZE] [/SIZE]

---

### Post by PriceChild on 2006-11-07
Personally i think that it is your meddling causing the problems... Changing /var/lib/dpkg/status for example... its just asking for problem!

---

### Post by Old Pink on 2006-11-07
> **PriceChild said:**
> Personally i think that it is your meddling causing the problems... Changing /var/lib/dpkg/status for example... its just asking for problem!

Who cares if I cause a problem? All I know is a started off with a problem I needed to fix. It was a problem, it couldn't get any worse, and hasn't. I'm still in the same situation. I only meddle with things if I know I can't possibly make the situation any worse. If all was working fine, I wouldn't meddle. Therefore, it is completley and utterly _not_ my fault.

---

### Post by PriceChild on 2006-11-07
Well i reccomend you undo all your meddling and return all package states to the official versions.

Asking for help with custom/dodgy/3rdparty packages isn't the best idea.

---

### Post by Old Pink on 2006-11-07
> **PriceChild said:**
> Well i reccomend you undo all your meddling and return all package states to the official versions.

Current reinstall count for libgpod, amarok, amarok-*, libgpod-* and anything else related is now aproaching 6,000,000,000 in the past hour.

---

### Post by hikaricore on 2006-11-08
...and this is why I stole the only mp3 player I've ever owned from Adi's (poor people food/junk store).  Simple model with 256mb flash card that it read data from.  Plug-in, copy, unplug.  End of story.  Even worked on windows 98 first edition.  :P

---

### Post by nalmeth on 2006-11-08
> ALOT more effort needs to be put into iPod - Ubuntu functionality. Why is it possible for iTunes to be so perfect in every way whilst the best linux developers can come up with is half assed attempts that don't even compare. I know I'm being ungrateful and a bit harsh, but seriously, nothings stopping them, if anything they have more at their disposale with the open source element.
Which open source element? Ipod firmware is not open source. 
So thats one thing all but stopping *them*, and time is another constraint, I'm sure. The two aggregate eachother aswell.

I had considerable trouble getting an ipod going, and I almost got as snotty as you :p

The solution was to compile the latest gtkpod, File->Create Directories

From then on, it worked marvaleously in whatever program I used. I don't know that this is what you should do, I carried this out on a fresh, unused Ipod.

My friend had a problem with his ipod shuffle, and believe it or not (this was not my advice) he just formatted it over and over and over again, and it finally caved and worked.

So, my advice probably isn't that useful to you, I don't advise that you use it. I figured you might want to hear it anyway though.

---

### Post by drobvice on 2006-11-09
I recently installed edgy just for the newer packages.  I installed gtkpod from the repos and am syncing fine with my ipod video.  I have one video podcast that gtkpod will not sync but others are fine.  No problems.  Totally not bragging as I have been in gridlock before.  Just saying 6 hrs is rediculous.  I synced my collection of ~19gb in about 25min.  Trying to get the artwork on there is another question.

---

### Post by ajm2005 on 2006-12-19
> **hikaricore said:**
> ...and this is why I stole the only mp3 player I've ever owned from Adi's

why did you steal it? not that I have a problem with shoplifting, just curious. :P


I also have been having terrible problems with amarok making my ipod Shuffle unplayable.

Even worse, the most recent version of gtkpod either would not start, or would not work with my shuffle (giving an obsure "segmentation fault" error). The 'solution' to getting gtkpod to work was to go back to an older version - 0.88.1-1 - by downloading a .deb binary from the debian people - this tip was from a thread here on ubuntu forums):


The BEST solution I have found for my shuffle is an excellent python script called the iPod shuffle Database Builder:

[http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

Place the script onto your shuffle and run it with the 'python' program, e.g.,

**python /mount/ipod/rebuild_db.py**

This script scans the contents of the Shuffle, locates all music files, and inserts them into the shuffle database.

The script seems to repair whatever damage is done by amarok. I.e., if I transfer files to my shuffle using amarok, then disconect, the shuffle is unplayable. If I plug the shuffle back in the usb port, and run this script, then remove safely, the shuffle will now play.

There is also a version for (non-shuffle) ipods called reTune which uses a similar approach, maybe people here having troubles with amarok/ gtkpod/ libgpod might benefit from reTune:

[http://retune.sourceforge.net/](http://retune.sourceforge.net/)

---

