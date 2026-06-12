---
title: "Can't login, possibly due to &quot;too many levels of symbolic links&quot;"
date: 2024-01-05
forum: General Help
---

### Post by JmM4RCGXwJJUCt on 2024-01-05
Hey, yeah, so I think I broke this one myself. 

I was feeling so proud of myself, having just installed an encrypted Ubuntu 22.04 on a partition of my shiny new desktop computer. I even understood everything the written guides were telling me as I was doing it. And after that I went and encrypted the Windows partition with Veracrypt. Took me days to figure out how to do all this and it was working perfectly. This sorta stuff was a huge accomplishment for me.

Today I went to start installing some programs on the new Ubuntu partition. I was feeling so clever that I didn't want to install things from the software store. I thought I must be an advanced user by now, so I was downloading programs from their official websites, extracting files, making them executable; no software store version for me, thank you very much!

I can't remember which program it was exactly... the Tor Browser maybe... I think I was trying to move the .start file thing to the /bin folder or something like that because I thought that's where it's meant to live. In the terminal it said "too many levels of symbolic links" when I tried to run it. So I just left that one and carried on installing other programs.

At some point I restarted the computer but when I went to log back in the screen went black for a few seconds and then returned me to the login screen, like is described in this post: [https://ubuntuforums.org/showthread.php?t=2485795](https://ubuntuforums.org/showthread.php?t=2485795) (only with me there is no error shown). I cannot actually log in, it just keeps coming back to the part where I enter my name and password. (Note there is nothing wrong with entering the encryption password).

I booted into recovery mode and saw there was an option to try and repair things that are broken... when I did that it said:

/lib/recovery.mode/options/dpkg: 18: env: Too many levels of symbolic links

So, yeah, I think I broke it when I was installing Tor Browser, or whatever program I was shifting the files around on. 

Apologies for my ignorance, does anyone know what I can do? I'd really appreciate any help. I can see that I can type command line stuff from the recovery mode... in root, I think they are. 

I tried reinstalling coreutils, as the post I link above refers to. (sudo apt reinstall coreutils). Didn't make any difference. 

Interestingly, as I write this, Mercury is entering the Scorpio-Sagittarius Gandanta zone, which is causing these computer difficulties for me...

---

### Post by TheFu on 2024-01-07
> **djackson33 said:**
> Hey, yeah, so I think I broke this one myself. 


We've all done it.  Helps with learning, though it really isn't usually at a convenient time.

> **djackson33 said:**
> I was feeling so proud of myself, having just installed an encrypted Ubuntu 22.04 on a partition of my shiny new desktop computer. I even understood everything the written guides were telling me as I was doing it. And after that I went and encrypted the Windows partition with Veracrypt. Took me days to figure out how to do all this and it was working perfectly. This sorta stuff was a huge accomplishment for me.

False confidence.  We all get it and get humbled.  Computers don't care about our confidence. They do what we ask - brilliant or stupid.

Before going any farther, exactly which sort of encryption did you install for Ubuntu?  There must be 10 options - more if you did it manually.

> **djackson33 said:**
> 
Today I went to start installing some programs on the new Ubuntu partition. I was feeling so clever that I didn't want to install things from the software store. I thought I must be an advanced user by now, so I was downloading programs from their official websites, extracting files, making them executable; no software store version for me, thank you very much!


You won't be "advanced" for at least 5 yrs.  Assuming you do administration work for 4 of those 5 yrs. Sorry.  It is impossible to know your own skill level.  Following instructions is beginner-level stuff.  When you are taking "ideas" from both experience and instruction guides, then merging those into completely new capabilities, that's when you are just starting to be advanced.  When 50% of the issues you have aren't trivially solved with google (and your google-fu is strong, not weak), then is when you are leaving the intermediate levels.

BTW, manually installing stuff is a bonehead move.  It will break your system.  There's no way around it.  Or worse, you will end up in "APT hell" where the only fix is a re-install.  Manually installing anything outside the repos is asking for future problems. If not today, 3-6 months later.  There is a "smart" hierarchy of how to install software.  Also, keeping large packages (mainly for servers) logically separate from the hostOS is smart.  Linux Containers are the light-weight solution for that, when security doesn't matter as much.  Sometimes a full virtual machine is needed, however.

The last option for software that you absolutely must have is to get the source to install.  Doing that means you are giving up one of the main reasons for running Linux - the entire software patching and maintenance infrastructure that is the package manager.

Always, always, remember the "new" is the enemy of "stable".  Unless you want to be an alpha tester and like having broken applications full of unknown bugs.

> **djackson33 said:**
> 
I can't remember which program it was exactly... the Tor Browser maybe... I think I was trying to move the .start file thing to the /bin folder or something like that because I thought that's where it's meant to live. In the terminal it said "too many levels of symbolic links" when I tried to run it. So I just left that one and carried on installing other programs.


Any manually installed programs belong under /usr/local/.   There's a directory structure standards document.  Wikipedia has a good summary.  Read it, at least the table that explains what belongs where.  Don't be too surprised that Canonical violates some of those standards, but you shouldn't.  The people before us weren't idiots.  They were very smart and thought of almost everything possible - things you and I have never heard about.

> **djackson33 said:**
> 
At some point I restarted the computer but when I went to log back in the screen went black for a few seconds and then returned me to the login screen, like is described in this post: [https://ubuntuforums.org/showthread.php?t=2485795](https://ubuntuforums.org/showthread.php?t=2485795) (only with me there is no error shown). I cannot actually log in, it just keeps coming back to the part where I enter my name and password. (Note there is nothing wrong with entering the encryption password).


This is where having excellent backups with a solid restore process makes any issue that can't be fixed in 60 minutes not worth our time.  It takes 30-45 minutes to get my systems back to where they were based on backups from last night or last week or 39 days ago or 131 days ago.  If your backups don't do that, you are doing it wrong.

> **djackson33 said:**
> 
I booted into recovery mode and saw there was an option to try and repair things that are broken... when I did that it said:

/lib/recovery.mode/options/dpkg: 18: env: Too many levels of symbolic links


Nobody expects you to break symbolic links at a high level, so nobody would check for that.  A true expert could look at the file system, check the links and fix it in 10 seconds - or know it isn't easily solved. Can't tell anything without facts.  

> **djackson33 said:**
> 
So, yeah, I think I broke it when I was installing Tor Browser, or whatever program I was shifting the files around on. 


You'd have to do something really bad for that to happen.  **sudo** abuse is a more likely problem, in my estimation.  People overuse sudo before they understand all the side-impacts all the time.  Only experience and time will fill in the knowledge gaps.

> **djackson33 said:**
> 
Apologies for my ignorance, does anyone know what I can do? I'd really appreciate any help. I can see that I can type command line stuff from the recovery mode... in root, I think they are. 

I tried reinstalling coreutils, as the post I link above refers to. (sudo apt reinstall coreutils). Didn't make any difference. 


Restore from your backups from before the issue.

> **djackson33 said:**
> 
Interestingly, as I write this, Mercury is entering the Scorpio-Sagittarius Gandanta zone, which is causing these computer difficulties for me...

Computers don't care about astrology. I really hope you aren't be serious.

---

### Post by JmM4RCGXwJJUCt on 2024-01-07
Just wanted to thank you for writing all that out. You've given me a lot to think about. I especially like what you say about the backups that you have. I must learn how to set them up like that. 

And yeah, I already realised I'm not going to be able to fix this, and I'll just have to reinstall Ubuntu. I had only just installed it on the computer anyway. It won't take me that long now that I've done it before and I know the steps better.

---

### Post by Rubi1200 on 2024-01-07
We've all been there. Mark it down as a learning experience. Personally, I think it will make you a better Linux user.

The first thing you should do after installing is put a backup solution in place before doing anything else.

---

