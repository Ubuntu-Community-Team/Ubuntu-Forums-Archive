---
title: "Reinstall windoze in a partition after Ubuntu"
date: 2007-09-18
forum: General Help
---

### Post by nobodie on 2007-09-18
A sad sad story. My daughter is dual booting Windoze and Ubuntu Studio. She uses Windoze for the Sims and I use it for Chessmaster. We are in China, just arrived and the "IT specialist in our apartment just hooked up the internet to the Windoze partition and added a script that rewrote the config.msi file and fried Windoze totally.

Cool huh? So I want to reinstall windoze on this partition, it would be even cooler if I could just get in and repair it, but I don't know how. It seems like I should be able to start it on the Windoze setup CD and run repair from there, but the setup CD tells me that there is no HDD. I am guessing that grub reports it in a way that this (pirated) CD can't recognize. 

So, is there a way to get the install CD to boot just on that partition, and could I get some walk through on it. I am guessing that grub will do it, but looking at the man file didn't help. And I really don't want to fry the partition totally. 

Thanks

---

### Post by Rage10898 on 2007-09-19
Nobodie,

I've got a few questions, but we should be able to nut this out.  Even a pirated CD should see your HDD, GRUB should have no effect on whether your disk sees it or not, it's just a boot loader. 

Can you reburn your disk (if burned from an .iso) or get another copy?  Was this the disk you used to install windows initially?

Are you using separate partitions on one disk or two disks?  If two disks, can you mount your Windows partition under Ubuntu or have you fried that drive?

Let me know the answers to above and we can go from there.

rage

---

### Post by nobodie on 2007-09-19
Thanks for the help, i'll interlineate below:

 **Even a pirated CD should see your HDD, GRUB should have no effect on whether your disk sees it or not, it's just a boot loader. **

OK, that makes sense, see below

**Can you reburn your disk (if burned from an .iso) or get another copy? Was this the disk you used to install windows initially?**

Ummmm, I live in Asia, I have 3 or 4, maybe five or 6 various pirated copies of various versions of windoze. (they only cost about $2.50 here) so I don't really know. It was definitely an XP SP2 version, but that could be any one of a number. I was thinking of trying one of the others, but I thought this one had been good before.

**Are you using separate partitions on one disk or two disks? **

Ummm, another tricky one. Originally I had 4 partitions on this single 80 G disc, 3 windoze and one fedora. then i migrated the two fat32 data partitions to a new, larger disc on another computer that i just built in April. then i consolidated those partitions into one larger one, expanded the windoze partition and installed ubuntu studio on the ext3 partition and set this up as my daughter's graphics station. In the process of setting up the ubuntu though i created a part table that had  Windoze as SDA 1, /boot as SDA2, swap as SDA3 and / as SDA4. At least that is how I remember it now. 

[B]
If two disks, can you mount your Windows partition under Ubuntu or have you fried that drive?[/B]

So, the physical drive is not fried, only the config.msi file (as far as I can find using DOS chdsk) is corrupted. This is why I hoped to use the repair function in the install Windoze disc. This would maintain all the setup I had (two or three years worth of stuff in cubbies and crannies) and just fix the config file. If I lose it, well OK, but then I don't want to lose the Ubuntu as well cause that is chockfull of my daughter's graphics work as well as all the data I moved out of the windoze partition when all this started. 

The problem, as I see it from what you've said is that the install disc should find the drive and recognize the fat partition that windoze is in and let me repair it. If so then maybe I just need to unpack another windoze copy and try that, which I will do when I get back home.

[B]
Let me know the answers to above and we can go from there.[/B]

ok, that is it, if you have some ideas after, i will check my discs before i come back here,

and thanks again

---

### Post by nobodie on 2007-09-20
OK, I tried 4 different windows install discs and they all return the same message: no HDD on which to install windows. They suggest running the manufacturer's setup disc for the HDD as a solution (hahahahaha)

In fdisk manual I noticed a mention of DOS/Windoze expecting to find a blank 512 byte space at the beginning of the HDD, this space is not there. I checked my layout with gparted:

SDA 3: first partition : /boot about 125 M
SDA 1: second partition: C: drive fat32, about 28G
SDA 5: extended partition that houses SDA 4
SDA 4: Swap: about 550M
SDA 2: Final partition ext 3 : / about 47 G I think

I guess the question is how to run windows install just in the partition for windows, which would let me run their repair function which might or might not work of course. Actually, experience with windows says it won't but who knows? It was trying to run restore that actually did the deed or maybe it was the blue screen of death while it was trying to restore. I just love windoze!

Ideas?

---

### Post by Rage10898 on 2007-09-20
Hmmm.

Can you boot windows into safe mode and do a system restore from there?  I meant to ask this morning but forgot to.

As to the rest, it just seems odd that it doesn't recognise that there is a drive there.  I'm assuming that Ubuntu still boots?

It's not really an issue of running the windows boot on a particular partition, as it should see the whole drive and then give you the option of installing on whatever partition.  Your Ext3 and swap partitions should just come up as an unrecognised file system.

Do you have an old hard drive lying around?  Can you swap that into your pc and see if windows will recognise that drive and install onto that, then transfer your files/settings from one to the other, then use GRUB to boot into windows on the second disk?

I'm starting to run our of ideas about ways around this!!  It would seem that the windows install disk is corrupted if it can't see the hard drive at all, but if you've tried several, that won't be the case.

These issues with windows are the reason I jumped ship in the first place!

I'll keep thinking and throw it around with one of the guys at my local Pc shop and see what we can work out for you.

---

### Post by nobodie on 2007-09-20
OK, let's see what I can do with this thing: When I try to boot into windows I go from grub to the windows start screen, then I get the log-in screen then I get a light blue screen that my daughter says is the colors that the Sims use for their blue motief (i don't know if this is true, just reporting here)

[B]Can you boot windows into safe mode and do a system restore from there? I meant to ask this morning but forgot to.
[/B]

I will try safe mode, but I have serious doubts, here is a more complete history: the system became really unstable due to a script that the local "IT specialist" put in. I tried to do a system restore to a point before we came to China, back in July. I got blue screened in the middle of the restore process (not exactly sure where, but definitely before it finished. On restart it chkdsk'ed and gave out a list of corrupted files that it was changing. 

Then, I restarted again and it hung. a few restarts later it finally allowed as how the restore was screwed and did i want to try again. i did, and restored to the first day in China, four days before and before the script was installed. It restored but on restart hangs with this funky blue screen and a mouse pointer that does move around.  

Checking the config.msi file (because that was the one that the chkdsk said was "corrupted" I found a mess of symbols and numbers that look like ascii reps of chinese, which makes all too much sense. That is the full history if it helps.

**As to the rest, it just seems odd that it doesn't recognise that there is a drive there. I'm assuming that Ubuntu still boots?**

Ubuntu boots and runs fine, with the exception that if the network connection is wanky (which it is some of the time, probably because the networked computers in the building are all running this script for their internet connection).

[B]It's not really an issue of running the windows boot on a particular partition, as it should see the whole drive and then give you the option of installing on whatever partition. Your Ext3 and swap partitions should just come up as an unrecognised file system.
[/B]

Oh yes I agree, it is strange, let me try to throw in a Live CD for fedora and see what that sees as well. i have used one of these cds to install a Virtual Box windows in my other computer at home with no problems so it really can't be the CD's . 
[B]
Do you have an old hard drive lying around? Can you swap that into your pc and see if windows will recognise that drive and install onto that, then transfer your files/settings from one to the other, then use GRUB to boot into windows on the second disk?[/B]

I hadn't thought of that. I could move my big disk from my computer into that one and try to install on an empty partition there. Transfering should be relatively easy, but .....hmmm I'll at least se what I can do with this idea, it has some promise.


[B]
These issues with windows are the reason I jumped ship in the first place![/B]

Oh yes brother oh yes, like i say it is only these pesky games that aren't ported to Linux yet

**I'll keep thinking and throw it around with one of the guys at my local Pc shop and see what we can work out for you.**

and thanks for your time and effort!

---

### Post by nobodie on 2007-09-21
Ok, just to update you, things are reaching a new height of weirdness.
Ubuntu has started to hang and crash. That's pretty weird in and of itself, but it is also getting worse. Finally dragged the box over to my office to hook it in to the office network (well, actually my university network since I'm teaching at this university in China) and can use the network here for updates fast. 

I am wondering about hardware problems caused by the trip from Thailand to China this summer. in the other box (mine) a HDD popped out of the fastener in the frame and was laying on the floor of the box. So when this update is done I think I'll take this apart and check for loose stuff and check my dates on backups and then begin to approach this again. 

Do you concur?

thanks

---

### Post by Rage10898 on 2007-09-21
Having read your last post, it could very well be a hardware issue, especially if Ubuntu is starting to get flaky too.  After 2+ years of much more Ubuntu than windows, I've yet to come across an issue I haven't caused myself...!

My advice, download a rescue cd from here: [http://www.demonoid.com/files/details/1357136/7271682/](http://www.demonoid.com/files/details/1357136/7271682/) ghost the drive, just in case, and stick a new hard drive in and reinstall.  You could also burn your docs to a dvd or two and keep them for next time windows borks your system!  

This will also work, if the download above is a bit slow: [http://www.torrentspy.com/torrent/1920168/Hiren_s_BootCD_9_2_iso](http://www.torrentspy.com/torrent/1920168/Hiren_s_BootCD_9_2_iso)

I would almost guarantee that that will fix the problems.

Re-install windows and UbuntuStudio and Bob's your uncle, as they say in the classics...

Let me know how you get on.

Regards,

Jason

P.s. What are you lecturing in?  I might need to call upon you if it coincides with my degree.  Cheers!

---

### Post by maybeway36 on 2007-09-21
If your computer is good enough you can try VirtualBox for running your Windows. They have an APT repository on virtualbox.org under downloads.

---

### Post by nobodie on 2007-09-22
Warning, Warning, Cascading series of failures causes comlete system destruction, Warning warning warnnnnnnnnnn.
Damn I hate it when that happens. Yeah, hardware. X11 corrupted, then lost any connection to the screen (no input cable or cable unplugged was the message) either the MB, which is my guess, or the graphics card, but probably the MB. I tried to boot off a live CD and it looks from the busy lights that the HDD is locking as well. soun ds bad. time to pull the HDD and try it in another box to check the data and then get Mr. fixit to destroy it totally before I replace things one by one. 

So, problem solved????? 

thanks for the help from everyone: 

oh: in repoly to other posts: I use Virtual box on my other box and love it, but it can't handle 3d graphics as yet (or the last time I checked it couldn't. 

I lecture in teaching English as a foreign language to Asian language speakers. In this endeavor I spend a lot of time doing practical classroom teaching to prove to Asian teachers that what I do does work, a little time explaining it in seminars and teaching forums and nowhere near enough time publishing and researching . It is an interesting sub-specialty of linguistics (or applied linguistics) which has given me some amazing insight into the structure of English. Which I would love to publish but haven't the time to organize, proof and push on the world.

---

