---
title: "Major Problem!: Installed cpudyn , now Ubuntu freezes seconds after boot!"
date: 2007-03-12
forum: General Help
---

### Post by mibs on 2007-03-12
Ok, I'm going to try and explain this as best as possible.  This all just happened at once and it is 1 am but I will do my best!

So here is the story, I installed Ubuntu 6.10 to dual boot with XP about 4 months ago.  I'm just running the basics, gnome, whatever was the default with the release.  I also have an ATI Radeon x1900gt, and I always found that the fan on it seemed to increase in speed very much when I was on Ubuntu, compared to XP.  So I spent some time searching these forums for a reason why this was happening, and also a fix. 

I posted this thread [http://ubuntuforums.org/showthread.php?t=376362]("http://ubuntuforums.org/showthread.php?t=376362") a week ago, and i finally got an answer recently.  As you can see I was informed that installing cpudyn from the package manager could fix it.  So I went ahead and did this.  The package manager said it would be replacing something, which I can't remember what it was because I didn't think it would be a big deal.  So I read the description of cpudyn and the other thing and said sure replace it what harm can it do?

Well it turns out it did a lot of harm.  A few seconds after I got the update complete message, my computer suddenly froze.  So I waited, waited some more, tried pressing some keys I thought might trigger something, but nothing happened.  So I shut down the computer, booted up again in Ubuntu.  Seconds after entering my password the same thing happened.  So I thought something must be up with my video card since I installed cpudyn.  I turned off the computer, removed my video card, booted up, but the same thing happened.

Then I noticed that the very loud fan that runs at startup was still happening, all the while I thought this was my video card.  With this currently out of the computer it lead me to believe that the fan that was spinning very loudly during my normal Ubuntu fan was never the video card fan but in fact the CPU heatsink fan.  

So now here I am, not being able to boot Ubuntu, luckily I had windows to fall back on.  I haven't put the video card back in yet, but I doubt it will make a difference.

So does anybody have any ideas, suggestions, or solutions?  This is really important to me as I have a lot of files under Ubuntu that I use for school, and I just would really like to be able to use the OS again!  I'm sorry for the long story but I felt it was necessary to fully explain my problem.  So any help would be appreciated, thank you.

EDIT: I put the video card back in, and everything ran the same.  So I guess it rules that out.  I think it was the CPU Heatsink fan all the while.

---

### Post by mibs on 2007-03-13
I just booted into safe mode and removed the cpudyn package.  I'm now on ubuntu once more.  Everything seems to be going just like it was before.  I would be interested in knowing why installing cpudyn caused my sytsem to freeze like that.  Also, now that I know it is my cpu heatsink fan that is speeding up so much and not my video card fan, does anybody have any suggestions as to how I could make the fan stop doing that?

---

