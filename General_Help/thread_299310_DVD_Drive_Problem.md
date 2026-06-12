---
title: "DVD Drive Problem"
date: 2006-11-13
forum: General Help
---

### Post by dut1979 on 2006-11-13
Hi I am having a problem with my DVD drive and am running out of ideas of how to fix this and am hopeing someone here might know what I need to do or might a least have some suggestions that I have not thought of or found on forums.
The Drive is a Matshita UJ-831Da DVD/CD combo drive on a Sony Vaio VGN-FS550 running XP SP2.
Here is the problem(s) I am having, 
1. If I start up my computer with the dvd drive empty after the bios startup the dvd drive starts spinning and all I get is a blinking cursor in the upper left of the screen.  
2.If I have a disc in, I end up with an all black screen and no cursor.  
However if I press the eject button on the drive before the bios start and leave the drive open XP starts up just fine.  I then can close the drive and everything runs fine. If I then put a dvd in, the dvd plays fine in XP,  but 
3. I cannot eject dvd by pressing the eject button or if I right click the dvd drive in my computer to eject the disc it freezes up the entire computer.

I recently tried useing the Ubuntu desktop CD that "allows you to try Ubuntu without changing your computer at all" and immediately started haveing these problems after checking out ubuntu, so I think this is was the initial cause of the problem.  I previsously did not have any issues.

Here's what I've tried so far to correct the problem.
-Complete System Recovery, I thought this would have solve the problem.
-Uninstalled and Installed the DVD drive(r)
-Tried change my bios to read the hard drive before the optical drive at start up.
I contacted sony support and they gave me no support at all, just to uninstall and then restart the computer, I told them I already did that and they said to send the computer in for service, meaning I would be out several hundred dollars and a laptop for about 3 weeks.   
I really do not want to resort to doing that but I want a properly functioning dvd drive so any help would be greatly appreciated.
Thank You

---

### Post by igknighted on 2006-11-14
> **dut1979 said:**
> Hi I am having a problem with my DVD drive and am running out of ideas of how to fix this and am hopeing someone here might know what I need to do or might a least have some suggestions that I have not thought of or found on forums.
The Drive is a Matshita UJ-831Da DVD/CD combo drive on a Sony Vaio VGN-FS550 running XP SP2.
Here is the problem(s) I am having, 
1. If I start up my computer with the dvd drive empty after the bios startup the dvd drive starts spinning and all I get is a blinking cursor in the upper left of the screen.  
2.If I have a disc in, I end up with an all black screen and no cursor.  
However if I press the eject button on the drive before the bios start and leave the drive open XP starts up just fine.  I then can close the drive and everything runs fine. If I then put a dvd in, the dvd plays fine in XP,  but 
3. I cannot eject dvd by pressing the eject button or if I right click the dvd drive in my computer to eject the disc it freezes up the entire computer.

I recently tried useing the Ubuntu desktop CD that "allows you to try Ubuntu without changing your computer at all" and immediately started haveing these problems after checking out ubuntu, so I think this is was the initial cause of the problem.  I previsously did not have any issues.

Here's what I've tried so far to correct the problem.
-Complete System Recovery, I thought this would have solve the problem.
-Uninstalled and Installed the DVD drive(r)
-Tried change my bios to read the hard drive before the optical drive at start up.
I contacted sony support and they gave me no support at all, just to uninstall and then restart the computer, I told them I already did that and they said to send the computer in for service, meaning I would be out several hundred dollars and a laptop for about 3 weeks.   
I really do not want to resort to doing that but I want a properly functioning dvd drive so any help would be greatly appreciated.
Thank You

Sounds like a BIOS issue to me... if you changed the boot order when you tried Ubuntu to try to boot DVD first then try changing it back.  Unless you physically changed something the Ubuntu live cd cannot possibly mess something like that up... it's either bios or a hardware malfunction

Another thought... I'm sure a local computer shop could help you out much quicker and far cheaper than SONY would, I would try them before I shipped it out

---

### Post by dut1979 on 2006-11-14
Thanks for the suggestions, I have did try changeing the boot order in BIOS, but that did not solve the problem.  
If I have to take it somewhere local I probably will, but would like to fix it myself if possible.
I just tried to make a XP startup CD so I could try running FIXMBR and when I went to burn the image the drive would not burn. So apparently it will play but it will not burn.  
Not sure if that helps in determining what may be wrong.  Device manager shows the drive as being ok.  I'm def stuck on this one.
Thanks Again

---

### Post by dut1979 on 2006-11-14
Hi thank you for the suggestion.  
I i think I have resolved this issue.
So far my drive is functioning properly.
If this post will be left for future reference this is what I did to correct the issue in case others encounter this same problem.
I had to create an XP Start Up CD ROM.  
I followed the instructions in the link below to do this as you can only download floppies from microsoft which are of little use if you dont have a floppy drive. (I was able to get my drive to burn by doing a few work arounds to get it to read media)
[http://tips.vlaurie.com/2006/recovery-console-for-those-without-an-xp-disk/](http://tips.vlaurie.com/2006/recovery-console-for-those-without-an-xp-disk/)
I then rebooted and ran the repair tool and ran FIXMBR.
And my problem appears to have been solved.  
It appears the Ubuntu live CD created a non standard boot record  and FIXMBR changes it back to the standard record for XP.
After doing this my drive has been working properly since then.

---

