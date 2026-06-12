---
title: "Tool bar question"
date: 2007-02-14
forum: General Help
---

### Post by tacm on 2007-02-14
I have a problem with my tool bar icons moving by themselfs and disapearing.  The one that bothers me the most is the "off button" and clock on the uper tool bar, sometimes the off button is in the upper right hand corner other times it is 1.5 inches too the left, and the clock is in the corrner.  Locking the icon to the tool bar has no effect.  Any ideas? ver. 6.06

---

### Post by tocleora on 2007-02-15
I had a similar problem... I think mine related to Notification Area Applet growing when icons would go into it, would push icons around. Moving it to a different place fixed the problem.  If you are (or aren't) using the Notification Area Applet, you might try rearranging your icons and then locking to panel and see if that helps.

---

### Post by kolinab on 2007-02-15
I posted regarding this issue a few weeks back and nobody seemed to know what was going on. I think tocleora is right with his suspicions about what makes it happen. It doesn't really bother me anymore. I'm running Edgy.

I have my a few icons in the notification area that move in and out depending on what I'm working on. This seems to affect the position of the power button for me sometimes. It's fairly unpredictable!

---

### Post by fragos on 2007-02-15
I haven't seen this problem and my notification area changes sizes as required.  Stop, Date, Volume and the notification area are all locked in the panel.  The notifications I've seen are software update, restart required, mail and gaim.  Perhaps your problem related some particular notification.

---

### Post by kolinab on 2007-02-15
It's kind of an interesting problem for some reason. [Here's a screenshot]("http://members.shaw.ca/aweighks/toolbarpos.png") of how mine looks now. I'll try to get another one when it's mucked up if I see it happen today.

BTW - I've got everything 'locked to panel,' except the mozilla new mail icon. There doesn't seem to be an option for that one but I remember having that problem before I used the mozilla icon anyway.

[edit]

Here's the link to the thread in which I asked the same question a while ago in case anyone is following that . . . [http://www.ubuntuforums.org/showthread.php?t=344275](http://www.ubuntuforums.org/showthread.php?t=344275)

---

### Post by tacm on 2007-02-15
Well I was kinda pissed last night when I could not get a responce on the forum, now it seems that many people are having this problem, I have a friend on here whom I consiter a "power user" He has helped me a lot, Ill look him up and ask him to reveiw this post.  Thanx Steve

---

### Post by fragos on 2007-02-15
> **kolinab said:**
> It's kind of an interesting problem for some reason. [Here's a screenshot]("http://members.shaw.ca/aweighks/toolbarpos.png") of how mine looks now. I'll try to get another one when it's mucked up if I see it happen today.

BTW - I've got everything 'locked to panel,' except the mozilla new mail icon. There doesn't seem to be an option for that one but I remember having that problem before I used the mozilla icon anyway.

[edit]

Here's the link to the thread in which I asked the same question a while ago in case anyone is following that . . . [http://www.ubuntuforums.org/showthread.php?t=344275](http://www.ubuntuforums.org/showthread.php?t=344275)

If I'm not mistaken notifications never have locks, only the panel itself locks.  Things on the right hand side of my applet bar are locked and were so by default.  The various applets and applications I've added to the applet bar are not locked but I can't conceive how that would make a difference regarding the right hand side of the bar.  Do you ever change screen resolutions for something like TVout?

---

### Post by tacm on 2007-02-15
I dont.....but a couple of us chave chimmed in

---

### Post by kolinab on 2007-02-15
On my panel, the network monitor, volume control, calendar, and the power button all have locks and they are selected. I do change resolutions sometimes I guess - when a game opens up fullscreen or something. Just tried it twice and things appear normal. It's one of those things that I don't notice until it's been like that for a while . . .

---

### Post by tocleora on 2007-02-16
> **fragos said:**
> I haven't seen this problem and my notification area changes sizes as required.

Well, that's what I was saying, once I got the icons in a certain order it stopped doing it, so mine doesn't do it anymore either.  Or I believe at some point I killed it, created a new one, put my icons back up there and that might have been what fixed it. Or maybe I just removed all the icons and readded them and that fixed it.  Gnome's panel's have been quirky for me for years, worse case scenario if I have a quirky panel I can just delete it and readd it and that seems to resolve whatever problem I'm having if nothing else has.

To do this, right mouse click on your existing panel, click "new panel".  Let it go to the bottom or wherever it goes at first.  Right mouse click on the new panel, click "Add to Panel".  You'll add "Clock", "Quit...", "Volume Control", "Menu Bar", "Notification Area", and look through there for any others you might need/want.  Then once you have everything you want on it and it seems to be working correctly, remove the old panel by right mouse clicking on it and clicking "Delete this Panel".  Right mouse click on the new one and click "Properties".  Under the general tab, set "Orientation" to "Top".  Remember to "Lock to Panel" your icons and that *should* ultimately resolve your problem.  If not... let us know. ;)

---

### Post by agatha on 2007-02-16
> **tocleora said:**
> To do this, right mouse click on your existing panel, click "new panel".  Let it go to the bottom or wherever it goes at first.  Right mouse click on the new panel, click "Add to Panel".  You'll add "Clock", "Quit...", "Volume Control", "Menu Bar", "Notification Area", and look through there for any others you might need/want.  Then once you have everything you want on it and it seems to be working correctly, remove the old panel by right mouse clicking on it and clicking "Delete this Panel".  Right mouse click on the new one and click "Properties".  Under the general tab, set "Orientation" to "Top".  Remember to "Lock to Panel" your icons and that *should* ultimately resolve your problem.  If not... let us know. ;)

Just noticed your reply in this thread while I was looking for answers to my own problem.
You may be able to help me.
I run Ubuntu dapper on an old laptop. Seams to me that a malfunctioning mouse corrupted my Gnome Panel. At first it would travel all over the screen and lastly when I dragged it back to the top it lost the Alacarte icon and the Applications-Places-System Menu. In my frustration to get things back to normal I eventually decided to delete the panel so I could make a new one, when there should really be a simple command to restore a default panel. Anyway I deleted before adding a new one, which I realised after reading your reply was not a good thing to do.
I can open a launcher with Alt F2 but when I run gnome-panel it says it can't because there is one already running. I've also tried killall gnome-panel without effect.
Can you help me get the Panel back?

---

### Post by tocleora on 2007-02-19
> **agatha said:**
> Can you help me get the Panel back?

Do you still have the bottom one, or one anywhere on your screen?  They are both gnome panels so you can just right mouse click on it and do a "new panel".  In my version (2.16.1 on Edgy) "delete this panel" is gray'd out if it's the only one is why I said it, so if you have one somewhere on your screen then you can recreate it from it.  If you don't have a panel at all anywhere on your screen (you just have the desktop) then right-mouse click on the desktop, do a "create Launcher", command is "gnome-terminal" and name can be "terminal". Save that to your desktop.  Clicking it should bring up your terminal window.  Do this:

ps x | grep gnome-panel

and see if you get a result for gnome-panel.  When I do it I also show a "grep gnome-panel" so exclude that if it's the only one.  If you see gnome-panel in there try your "killall gnome-panel" from in there and then try "gnome-panel &" and see if you have better results.  If you don't, you may try posting to Gnome's support forum here:

[http://gnomesupport.org/forums/](http://gnomesupport.org/forums/)

Good luck.

---

### Post by fragos on 2007-02-19
I have a recommendation that may not fix this problem but will help to avoid some problems.  Check out System-> Preferences-> Sessions.  On the "Sessions Options" tab make sure "Automatically save changes to session" isn't checked.  That way some problems we create for our selves won't become normal operation and rebooting will bring us back to a baseline desktop rather than the failed one we ended up with.

---

### Post by kolinab on 2007-02-20
That's good advice, Fragos. I checked to see and I didn't have 'save changes to session' checked. Also good advice here on how to rebuild the panel - I'll try one day. Really this situation isn't a big deal - I don't REALLY care where the power button is, but it is a curiousity.

Just spotted it now - something made it move so I did a [quick screenshot]("http://members.shaw.ca/aweighks/gotit.png"), because I said I would. I am sure this is the same phenomenon others are experiencing?

K

---

### Post by tacm on 2007-02-21
Yep, thats the problem.  it is no big deal, it just irratates me.  I made a new Pannel, locked everything, and saved sessions.  It has not happened again

---

### Post by girard on 2007-03-14
is there a quick way or command to lock and unlock items to the panel? i find it troublesome to have to right click on an item, unlock it, right click again and select move, then drag it to wherever i want to place them. plus i'd have to unlock all items it would be passing by for it to get there.

---

### Post by fragos on 2007-03-14
It can be a bit teadious.  I don't lock the icons anymore and its a little simpler since only move is required.

---

### Post by tocleora on 2007-03-14
Well, and once you get them set, they don't need to move around a lot do they?  I don't think it's designed for daily or hourly changes. ;)  But I didn't design it so I'll just keep my mouth shut! Hah!

---

### Post by girard on 2007-03-15
> **tocleora said:**
> Well, and once you get them set, they don't need to move around a lot do they?  I don't think it's designed for daily or hourly changes. ;)  But I didn't design it so I'll just keep my mouth shut! Hah!

haha... it's true.but i just realized the actual need for it also... when i again came across the exact same tedious procedure when i realized there wasn't a separator between items i wanted to be together. oh well, eventhough our systems try to make things changeable, there are minute things we'd have to live with. 

got them all locked in place now!!!... until i decide to add one more. :)

---

### Post by fragos on 2007-03-15
I group my icons by task and use separaters between groups.  For me it makes access more intuitive and faster.  I leave them all unlocked so I can move in new icons withour having to move the others.  Makes sense for the way I use them.

---

### Post by tocleora on 2007-03-18
I have my primary app icons, arranged in the order of the desktop I use them on.  Then I open each app in its own desktop, so I keep them completely separate from each other, plus I can just click on the 4th desktop to get to the 4th app, etc.  Oh and I have 8 desktops. :)  No tedious alt-tab'ing. Oh, and I don't have a start bar (whatever it would be called in Gnome) and then if I'm working on something I'm not suppose to be I just avoid that desktop when the boss isn't around. ;)

---

