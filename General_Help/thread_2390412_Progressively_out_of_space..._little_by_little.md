---
title: "Progressively out of space... little by little"
date: 2018-04-28
forum: General Help
---

### Post by hipogrito2 on 2018-04-28
Hi,

10 year+ Ubuntu user... not super-expert but I've seen a bunch of things in my different Ubuntu distros during these years so, not newbie. This thing is new to me.

Ubuntu 16.04 Desktop with Gnome
1 TB of hard drive in one big partition. Some smaller partitions for Ubuntu stuff...

I was getting a message that the disk is running out of space, less than 1 GB.

So, I go and I deleted stuff.

Few days later.... again...

huh, I didn't recall storing too much new stuff...

Few days later... again...

And so on until one day I was, WTF, why is this still happening... so I started to check for what was taking space and I saw that my user home folder was just like 50 GB! 

So, I tried to run 

 sudo du -sh -- * .*

to give me the sizes of everything in the disk, and it gets stuck after lost+found... for hours...

I tried to do it with individual folders and I don't see anything big....

Yes I cleaned up old Ubuntu versions, packages, the typical stuff you do in these cases.

By the way,

df tells me:
/dev/sda1      955151124 898138440   8470732 100% /


So, Where's that stuff????

I'm starting to wonder if the disk is going bad....


Any ideas?


Thanks,
Regards,
Hipo

---

### Post by hipogrito2 on 2018-04-28
Hi,

One last comment.... I don't believe I'm being hacked and I don't want to be paranoid... but, what if some external hacker is using my disk to store stuff? Is that a thing? and, if so, can it be detected easily?

Thanks!
Regards,
Hipo

---

### Post by kazakore on 2018-04-28
You could try running the find command with options to only show files modified after a certain time, or over a certain size.

In my experience this kind of thing is most often something generating a log and not doing the housekeeping of removing old files, or the log files generating very quickly as the same error is repeated every few seconds into the log. Although that's more when dealing with serverside stuff than home desktop software.....

---

### Post by 1clue on 2018-04-28
Have you had any loss-of-power events? You're shutting down the system properly right, not just turning the machine off?

lost and found directory is for when you boot and Linux checks the filesystems before mounting them. If there's any inconsistency the lost or damaged files go into lost & found in case you want to clean that up or recover something.

I wouldn't suspect malware of doing this so much as some kind of app crashing regularly, or losing power, or effectively yanking the plug over and over.


WRT to hackers using your system, that entirely depends on the type of intrusion. People make a career out of this sort of thing, and if you're really good at it you can make good money. There are some things you can do, but there's no quick and dirty thing you can do without sitting down to learn how and why.

I would start with [https://www.google.com/search?q=ubuntu+security+checklist](https://www.google.com/search?q=ubuntu+security+checklist) and pretty much take it how it shows up there. Make a pot of coffee and tell your spouse or significant other that you'll be stuck in front of your screen for a few weeks.

You should also discover any issues with your router. Become fluent in navigating cve databases for all of your networked devices:  Router, computers, phones, TVs, blu-ray, smart home devices, whatever.

Unfortunately much of the malware that can affect Linux requires an educated and actively cautious user. One user is careless and the whole system is compromised. From there the attacker can get at everything on your network or anything your network can touch. Linux is not any more inherently safe than Windows or Mac OS or any other OS. Each OS can be MADE to be safe, and each OS has certain types of malware which work better than others. Windows suffers from viruses and Linux pretty much does not. But there is plenty of malware which can affect Linux and a stunning amount of stuff that affects people and tricks them into breaching their own security. There is nothing anyone can do about that except learn and teach your family.

Now, you can either take the blue pill and go back to your false sense of security, or you can take the red pill and see how it is....

---

### Post by hipogrito2 on 2018-04-30
Hi,

Thanks for the comments.

Well, it turns out that the problem is with an external hard drive... that is NOT connected!

I have a folder in the /media folder that has the name of my external hard drive... but the external hard drive is not connected. 

When I tried to delete the directory, apart of taking forever (still going) if I open another terminal window and type df repeatedly, I can see the available space grow and grow and grow... go figure!

Now, why did this happen? And it kept growing? I don't have a clue... but that was eating my space...

Thanks for the replies!!!

Regards,
Hipo

---

