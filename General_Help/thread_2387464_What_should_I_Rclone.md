---
title: "What should I Rclone?"
date: 2018-03-19
forum: General Help
---

### Post by mattzab on 2018-03-19
I like keeping my system backed up, but the internet is full of extremely conflicting advice on *what *to back up.

ie.
> You should NEVER back up directory xyz
You should ONLY back up your home folder
You should NEVER back up your home folder
You should back up your entire system
You should ONLY back up individual folders you specify to save space on your backup drive

Uh, what?

What should I actually back up? I use Google Drive and have unlimited storage, so space is no issue. (I mean, no issue at all. I keep a mirror of the Ubuntu Repository stashed on my Google Drive, along with several other software repos, so my file system is miniscule in comparison)
 
I'd just like to keep a good backup on there. Theoretically I'd like to restore from just above bare-metal, ie. Crash my system, install ubuntu mini (or netinstall) with no desktop or anything else, just get installed and to terminal, wget rclone, config, and sync down my backup. Maybe that's a bad idea- I trust ya'lls judgement. I've heard never to back up mounts or PROC, sometimes skip ETC and DEV, sometimes include them, etc. All kinds of weird advice, and I don't yet know the file system well enough to know what's what, and when advice is good or bad. Please don't let this thread become a big argument, just intelligent and reasonable suggestions please.

I do plan on excluding certain folders for sure. My Download folder is constantly changing, and I'm often downloading large files to it, like ISOs and what not. Anything important there I'd already have backed up manually. Also, I sometimes mount FTPs and my Google Drive account itself, so I'd naturally exclude those. (I'm not sure if Rclone would try to copy my GDrive fuse mount to my GDrive target- that would be a circular recursion situation there)

What do ya'll suggest I white/black list for my backup process?

Thanks!

---

### Post by monkeybrain20122 on 2018-03-19
If you backup for the purpose of restoring your system in case something goes wrong and the OS no longer functions obviously just backing up your $HOME is useless. I know, some people in this forum say they just back up their data and do a reinstall in case. But  that assuming that they only use a vanilla system without any tweak or customization, otherwise it will take a lot more than the 20 minutes to restore things to the way it was, also it doesn't address bad updates. Suppose your system crashes because of a bad updates of some important components (yes, it happens) To do a fresh install and to avoid a repeat of history would mean holding off all updates of said components since the creation of the live iso. but what if I want to restore them to the last good version before the system went busted???

So my strategy is this: I have a separate /home. I use fsarchiver to make an image of it without any user data (music, books, and crap ) and do it only once. I need that for restoration in case. The root partition (system stuffs) is typically small, for most people it is probably around 20g max. It is quick to backup with fsarchiver and can be updated regularly. To restore the system you need / + /home. / is always up to date but /home is just a shell (you may need in addition a uefi partition depending on hardware) So the size of both are small and you can backup and restore quickly. I have had to do this before, it is much much  faster than reinstall + installing all the software even without taking into account the hours I spent on tweaking my system, compiling from source etc.

User data are easy to back up, there are many ways, from using syncing software to just copy and paste. That is a trivial issue really, and I don't know why so many blogs and forum posts talk about it. Backing up system is more challenging and requires a bit more thought.

---

### Post by oldos2er on 2018-03-19
It really depends on your use case, and which data is most important to you. Is the system being used at home?

The best solution for me personally is to backup data in my /home/user folder. I have /home on a separate partition, so keeping it backed up is fairly simple. If I need to reinstall the OS for some reason (which happens infrequently, always from operator error) it takes less time to reinstall it than it would to reinstall the whole thing from a backup. But of course you can do that if you wish.

---

### Post by HermanAB on 2018-03-19
Backup your data.

There is not much point in backing up Linux, since there are thousands of servers out there to download it from again.

---

### Post by monkeybrain20122 on 2018-03-19
> **HermanAB said:**
> Backup your data.

There is not much point in backing up Linux, since there are thousands of servers out there to download it from again.

Sorry that is really horrible advice.

---

### Post by SuperFreak on 2018-03-19
> **monkeybrain20122 said:**
> Sorry that is really horrible advice.

So what do you do when there is a new LTR of Ubuntu and upgrade option from older LTR is not desirable?

---

### Post by monkeybrain20122 on 2018-03-19
> **SuperFreak said:**
> So what do you do when there is a new LTR of Ubuntu and upgrade option from older LTR is not desirable?

Huh?? If I understand that hard to comprehend question, you PLAN your update ahead of time and make all kinds of preparations and tests. You don't plan for your system to crash, that is an accident. Two different matters. 

BTW I never use the "upgrade option" and won't recommend it. To do an OS upgrade just because some popup prompts you out of the blue is nuts. I do a fresh install, or, I make an installation on a separate drive, then tweak and test for at least a month after release date and then use fsarchiver to clone it and then restore it to the internal drive, that way it is a drop in replacement and no nasty surprises.

---

### Post by SuperFreak on 2018-03-19
> **monkeybrain20122 said:**
> Huh??
I assume in the case of moving between Long Term Releases your backup of root and home is pretty well useless. 
I use Timeshift for situations where I use the same release

---

### Post by monkeybrain20122 on 2018-03-19
> **SuperFreak said:**
> I assume in the case of moving between Long Term Releases your backup of root and home is pretty well useless. 
I use Timeshift for situations where I use the same release

See my edit.

---

### Post by SuperFreak on 2018-03-19
Timeshift with the backups stored on a separate HD than the OS seems simpler to me but may not cover all possible situations

---

### Post by mattzab on 2018-03-21
Haha, you guys. No straight answer.

So, I'm using rclone to Google Drive. (that means, not other tools like timeshift, dd, etc)  ***What directories ***should I back up?

Thanks.

---

### Post by mattzab on 2018-04-15
Having had 3 weeks to consider my question, has anyone come up with any ideas?

---

### Post by rbmorse on 2018-04-15
It's pretty clear to me that everyone has their own idea about what constitutes adequate backup, depending upon their individual situations and circumstance. You need to assess your needs and develop a plan that fits your specifics.  

In my case I only need to worry about my user data files, but preserving application settings and options is pretty handy too. I use Backintime to create an automated back up /home/myusername to a dedicated internal hard drive on a regular schedule. This happens automatically and without any intervention on my part once it is set up. Since the backup file store is a local hard drive the backup happens very quickly and without regard to the state/status of the network. I like Backintime because it has performed flawlessly for me over a couple of years and has a fairly intelligent plan for pruning accumulated backup stores and managing disk storage.  There are a number of other packages or front-ends for rsync that do, too.  

If I think about it, I'll make a copy of the latest backup fileset to a flash memory device and store that at my mom's house.  It's sorta offsite storage that doesn't depend upon the network. 

On the system side I could get by with simply reinstalling the O/S and application packages from repository, but as mentioned above that's not viable for everyone.  OTOH, because I come from a Windows and MAC OS background and their scars are burned deep, EVERYTIME I add or remove software or update Ubuntu the first step is to take the machine off line, boot Clonezilla and make an image backup of the ESP and the partitions holding the operating system and /home (they're separate).  This ensures I can put things "back to exactly the way they were before" with minimal fuss if an update or install goes bad or if a Windows update decides to overwrite the entire ESP.  Plus, because the machine has to reboot to load Clonezilla, it ensures a relatively clean operating environment for the upgrade/package management operation. There's room on the flash device that goes to my mom's to hold a copy of the latest partition images, so they get added to the rotation.  These images tend to accumulate and make a good backup store, albeit even the most recent will be one configuration change behind the current machine state.  I keep a paper log of system alterations so even if i can't remember exactly what the last change happened to be, I can easily look it up.  Keeping the paper log takes a little discipline, but I'm surprised at the number of times it has saved my butt when I couldn't remember exactly what I had done to the machine at some point in the past. 

So, that's my idea.  It most certainly won't be appropriate for your circumstance, but go ahead and make you assessment of needs.  You may decide that keeping a safety copy of critical user data on Google drive is all you really need. More likely, however, you'll want to do something a little more ambitious and I'm sure if you have trouble implement a specific function you'll find plenty of help for that here. 

Speaking of Google Drive...at one time, and I don't know if this is still the case, you couldn't simply copy /home/username directory over to Google Drive and be able restore a machine by simply copying the files back onto the machine. Something about privileges and permissions.  I only tried it once and made a real mess. Restoring the clonezilla image backup made things well again in short order, but the situation would have been dicey had I not had that.

---

