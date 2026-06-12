---
title: "Gutsy keeps logging out on its own"
date: 2008-02-01
forum: General Help
---

### Post by thomasyen on 2008-02-01
Hi.
Recently, while using Ubuntu Studio, I found that it would log out on its own, with no apparent reason. It would jump into terminal mode, list a few lines, then log out. Is this a bug in Gutsy itself, or is it because of some setting I did wrong?

---

### Post by musther on 2008-02-02
Sounds like X is dying or being killed.  This is exactly what happens when you hit control + alt + backspace.  Just try that (after making sure everything is saved) and see if it's the same thing.  And just to be sure (might sound like a silly question), you weren't hitting that keystroke by any chance?

---

### Post by thomasyen on 2008-02-02
Hello musther,
I tried it, and it was almost exactly the same, except that the screen didn't go all black, list a few lines of actions, the mysteriously log out. Also, by logging out on its own, I mean that I would leave it unattended for a few hours, then return only to find that it had logged out. In some instances, it would log out while I was working on something (quite sure that I didn't press Ctrl + Alt + Backspace by accident).

---

### Post by musther on 2008-02-02
So, we know that X seems to be dying unexpectedly.  I don't really know why that might be.  The one thing that's worth trying if you're having unexpected crashes, is to run memtest86.  When you get the grub menu on booting ubuntu (you may have to hit escape to get it, when it prompts you), select memory test.  The other way is to insert an ubuntu CD, at the menu select memory test.  Let memtest run for a couple of hours or so, see if it lists any errors in the bottom half of the screen.  

If memtest doesn't find anything then I personally can't suggest anything else, sorry.

---

### Post by JohnPhys on 2008-02-29
My friend and I are also experiencing this issue with gutsy installs on our laptops, both intel Core 2 Duo chipsets.  What chipset are you experiencing the problem with?

---

### Post by elemenoh on 2008-03-05
i am also having this problem. if anyone has any info please post
I have a core 2 laptop as well

---

### Post by nutz on 2008-03-05
Were you viewing anything offensive? Perhaps the computer got offended and cut you off. This happens when I fire up one of my necropyrobeastiality videos. I think my computer may be trying to censor my activities.

---

### Post by trey85stang on 2008-03-05
I had the same thing,  I determined it was the power save mode... disabled that and had no problems since.  Of course this was only happening when I left the computer and came back a few hours later.

---

### Post by elemenoh on 2008-03-05
> **trey85stang said:**
> I had the same thing,  I determined it was the power save mode... disabled that and had no problems since.  Of course this was only happening when I left the computer and came back a few hours later.

No, this is happening only while I'm on the computer, it only displays lines in the terminal for a second but I think what it says is

Starting anac(h)ronistic cron anacron --- Done
Starting deferred execution scheduler ATD ---Done
Starting Periodic Command Scheduler --- Done
Checking battery state --- Done
Running local boot scripts /etc/r.local --- Done

I found that after googling what I thought I saw which was anachronistic cron anacron and that message seems to match up, however no article I found was even remotely relevant- except someone saying they had overheating issues and their computer shut down. Mine doesn't shut down, it just takes me to the login screen, and I've never had a problem with overheating. I can leave the computer running all night on my table and it doesn't do this. I'm really perplexed.

and lol @ looking at something offensive... no, :P just writing email and chatting on pidgin.

---

### Post by elemenoh on 2008-03-08
OK, so, bump for a resolution to this, someone must know more about cron and anacron than me. I've been working on this problem for a while now with no sucess- I'm guessing because cron is a task scheduler that it is executing some bs command that is logging me out. What I'm going to do is uninstall anacron- since it assumes that because the computer is a laptop it will miss the regular scheduled tasks cron does-- I guess i'll update when or if I figure this out. 

Any help would be appreciated.

---

### Post by elemenoh on 2008-03-19
OK, so in the past while I learned a lot more about ubuntu and grep and all that. 
Suffice to say, if you're using an nvidia driver download this: [http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run)

chances are that the error you're getting (check system>administration>system log and the time in military time that your computer logged itself out) for me the error was:
gdm_slave_xioerror_handler: Fatal X error - Restarting :0

If that's the error you're getting you can either uninstall emerald or install the driver above and your problem should be fixed. If not that try uninstalling the gnash flash plugin if you have it installed and your restarting problems happen while you're on firefox.

One of those solutions should hopefully work for you! I'm logout free for now :)

---

### Post by misterhead on 2008-03-27
I might also tend to lean towards the overheating side of things. Mine does the same thing with Hardy. I'm thinking about switching back to Gutsy because of it. It sucks HAVING to have a high powered desk fan 1/4 inch away from my laptop at all times, blowing accross it, between it and the dock, and into the open PCMCIA slot and out the cd tray on the other side. You can REALLY feel the heat coming out the other side to.  No problems with XP pro though. Dual boot.

---

### Post by c00ch on 2008-04-20
Hi. I experience logouts on my machine as well. 

In my case it happens when I've got Google Earth running and the 3D screensaver tries to kick in. Obviously a x server crash.

---

