---
title: "problem watching streaming flash (youtube, veoh, etc)"
date: 2007-07-26
forum: General Help
---

### Post by awong on 2007-07-26
On my laptop, an ibm thinkpad r31 with a celeron 1.2 with 640megs of ram, I am having problems with watching streaming flash videos on both kubuntu and ubuntu with any browser, swiftfox, konqueror, and opera.  For the most part the videos play fine for 20 minutes, but for some reason after a while the the video begans to get choppy and navigating the browser becomes very slow, I close the browser, but it seems that the browser does not seem to flush any of the memory and I have to do a hard reboot in order to get things back to normal.  Usually its only flash video sites like youtube, veoh, etc.  I can browse on the internet with no problems, but when I want to watch any of those sites, the pc gets all choppy, hd is making more noise  

A few things I noticed, the xorg seems to jump up in memory like over 200 megs and the browser memory goes up too, and I tried to kill the processes, but only the browser I can kill and even then its still very choppy.

I am wondering what my problems and if anyone else experienced it.  Previously I had xp installed on this laptop and the same thing occured watching streaming flash, I was thinking it was a problem with flash itself, but I am not so sure.  I dont think my specs should be a concern either.  For one thing, before the memory shoots up, I can multitask fine like using gaim and watch videos.  Would a new hard drive improve performance?  Mine seems fairly loud and how about upgrading to 1gig of ram?  But it seems there is a memory leak

I am not sure if I am explaining things cleary, if so let me know, I really want to fix this problem so that watching streaming videos online dont force me to restart.

edit:  I ran HTOP, while the video I was watching veoh and noticed that the memory was ok, it was the cpu cycle shooting up to 100% and staying above the 50% mark, not sure if that has anything to do with my problems, but before the video ran it was under 10% after the video was closed, it never got under 20% and was still shooting up to 100% at times

---

### Post by Happy_Man on 2007-07-26
I am inclined to think that your processor may be the bottleneck here (I have less memory than you, probably the same version of flash, but I'm ok). Perhaps there is a memory leak... but I've never experienced it. The fact that it used to happen on WIndows too is where I'm getting my conclusions from. For the same problem to happen on two different OS's.... has to be hardware.

---

### Post by awong on 2007-07-28
thats what I am worried about, everything else works fine, but the minute I run flash for a 30 minute show, it bottlenecks down.  I guess I may try to get a p3 as an upgrade and hope to see improvement.  I guess what really bugs me is how for 20minutes of the show, no problems then all of a sudden it gets slow and  I cant prevent it.  

WIth windows, the celeron, the videos were only watchable using IE6, firefox was slow, and opera inbetween, on ubuntu, the problem was not as bad as windows,

could my hard drive be a bottle neck?

---

### Post by basher on 2007-07-28
I've been dealing with the same issue.  Here's my conclusion, it has to be a Flash player issue on lower end systems.  When I try to play a 0:30 second YouTube video, the sound is fine and the video is choppy as heck.  So I booted up to XP from a different hard drive and went to the same video in IE and Firefox and have the same results, choppy video, good sound.  Here's my specs:

AMD Athlon XP 3200+, 1Gb Memory, GeForce4 MX 400, 40Gb 7200RPM HD.

But less than a year ago this same computer was my primary computer and I had no issues, it boggles my mind that XP nor Ubuntu can play a Flash video with out jitter????  Is Flash 9 just that bloated??

On this machine I have Desktop Effects enabled with no problems and can run everything else with no issues. I watch full length movies with no problems at all.  My problems come when a web browser and Flash come in to play, on both Windows and Ubuntu.

So I dont' think its a Ubuntu issue but a Flash player issue??  Any ideas?

---

### Post by awong on 2007-07-30
I am thinking a flash issue too.  My desktop is a P4 and running xp and using veoh. full length shows, it runs ok, but I cant move the mouse without the video getting choppy.  But at the same time I can exit veoh or youtube and the memory flushes ok and I can browse normally.  

running the no scripts on swiftfox is a bit better not a total improvement, just to general browsing it is

---

### Post by awong on 2007-08-07
an update, I think I figured out the issue, it seems to be related to what kind of surface my laptop is on, when its on a hard surface like a table or using a text book on my lap with the laptop on it, I dont have much issues with it freezing when watching flash videos and its quite stable.  But say its on a soft surface like a couch, I have the problem occure more often.  I think there is not enough ventiliation for the air flow so its possibly on a soft surface like a couch the fan is covered and it makes the cpu processes jump up.

---

### Post by zimmett on 2007-08-07
If Youtube Is Too Choppy Try This.  Bring Up The Program You Are Trying To Watch And Immediately Put It On Pause For About Three Minutes.  Then Hit Play And It Does Work.

---

### Post by patr547 on 2007-08-17
Try disabling the Desktop Effects.

I was also having this issue and turning off desktop effects made everything work fine. I would assume this is a bug with the Compiz system and not ubuntu or flash specifically, can anyone else verify that?

---

### Post by anatolyv on 2008-03-04
indeed.  disabling visual effects in system>preferences>appearence 
makes the streaming video smother.

what gives?  i miss my animated effects..

---

### Post by simonfishwick on 2008-03-05
I have the same problem. Turning off desktop effects improved it to almost 90% of its quality with other O/S WINXP, but still chopping.

---

