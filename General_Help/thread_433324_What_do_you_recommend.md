---
title: "What do you recommend?"
date: 2007-05-04
forum: General Help
---

### Post by CM Xtasy on 2007-05-04
Hi, I've always wanted to use Linux, and I heard Ubuntu is great.  I installed it a week ago and was confused on some parts so I reinstalled Windows.  Now that I've had time to re-think things, Ive become less confused with linux for some part.  I need Windows for some programs such as MS Office 2007, Photoshop CS3, and Counter-strike 1.6.  What would your suggestion for me be?  I know of Wine but I didnt know how to access stuff at the time which now I think I know how.  With my little knowledge of Linux, should I dual-boot?  Help would be great.

P.S. - Im very experienced with Windows... I dont know if that might help anything.

---

### Post by rsambuca on 2007-05-04
If you need CS3, then you will have to dual boot.  The recent versions of Photoshop can not be run under linux, even with wine.  Gaming for the most part is difficult on linux as well, and as far as MS Office goes, there is an alternative in linux called OpenOffice, which is installed by default.

---

### Post by CM Xtasy on 2007-05-04
> **rsambuca said:**
> If you need CS3, then you will have to dual boot.  The recent versions of Photoshop can not be run under linux, even with wine.  Gaming for the most part is difficult on linux as well, and as far as MS Office goes, there is an alternative in linux called OpenOffice, which is installed by default.

I've used OpenOffice but I prefer MS Office 2007 for major assignments.

Is dual-booting easy or is there a guide?

---

### Post by Judicata on 2007-05-04
Dual booting is easy and there are multiple guides available, but the general rule is just don't reformat your Windows partition on installation (Ubuntu will detect it, and will not format it by default).  The trickiest part is getting the partitions right beforehand.

Have you used OpenOffice under Linux? IMHO it is better than the Windows version, and better the MSOffice. I am a graduate student and have to write a bunch, and prefer OOo over MSOffice. I prefer not to dual boot. You can also run MSOffice through Wine or CrossoverOffice (something like $30-$50). If it doesn't support 2007 now, it will before long.

If you're addicted to PS, then you'll have to dual. (I'm not a big graphics guy, I'd suggest switching to The Gimp, which is what I use - but, like I said, I don't do much).

As for games, check out winehq and click on "appsdb" and search to see which games work there, or check on [http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/), and click on the "Wiki Node" for your game to see how well/if it works.

If you dual, I strongly encourage you to try open source, Linux alternatives and try to progress toward dropping Windows altogether.  Its all about freedom :). 

Good luck!

---

### Post by mannheim on 2007-05-04
After dual-booting for a while, an alternative for PS and Windows-specific appications (not games) is to install VMware (or other virtuatlization software) and run Windows in a virtual machine. That's how I run MS Office. It works very well on a machine with sufficient RAM.

---

### Post by Iokua on 2007-05-04
> **CM Xtasy said:**
> Is dual-booting easy or is there a guide?

If you're dealing with two hard drives, I'd say it's very easy. If you're dealing with one hard drive and multiple partitions, it can be troublesome but I don't think it's beyond your ability if you're an expert Windows user. You mentioned that you had Ubuntu installed, then wiped it out for Windows, so I'm assuming that you're working with one hard drive.

I can't seem to find a guide in any of my bookmarks at the moment, but I can tell you how I've installed Ubuntu when I was in your situation. From a clean hard drive, I first installed XP, then booted into the Ubuntu Live CD, created a new partition on the hard drive, followed the installation steps, rebooted, and all was right with the universe. I had no significant problems. (Although now I'm working with two hard drives, one with Windows and one with Ubuntu)

---

### Post by CM Xtasy on 2007-05-04
> **mannheim said:**
> After dual-booting for a while, an alternative for PS and Windows-specific appications (not games) is to install VMware (or other virtuatlization software) and run Windows in a virtual machine. That's how I run MS Office. It works very well on a machine with sufficient RAM.

I have 2GB of RAM.

and to Iokua - Yes I do have 1 hard drive, but if you can find a good and simple dual-booting guide, that would be brilliant.

---

### Post by Nythain on 2007-05-04
Dual Booting Windows XP and Ubuntu from what i've read:
Install Windows XP First
During Install Create the windows partition (not sure of what size hard drive you are working with, but i wouldnt set the partition to be the WHOLE drive, because then you have to mess  with resizing and all that jazz from within windows and thats annoying, so remember to just leave enough empty space for your ubuntu partitions from the get go)

After that, load up your ubuntu livecd or alternate install cd and start the install.
Once you get to the partition phase you can either tell it to automatically create partitions out of just the free space or you can manaully create them yourself, with at least on large one for / and a swap at about 2x your physical ram size... i personally have a 100meg /boot, a 2gig swap, and the rest is /.
Make sure you install grub in the MBR and it should overwrite windows bootloader and detect windows and add its entry.

If all worked well you should have a grub list at boot with options for windows or ubuntu, and viola...

oh yeah, filesystems, ntfs for windows partition, ext2 or 3 for / and swap for swap

As for games, there are tons of posts in these forums for getting counter strike and other games to work in both wine and cedega... photoshop you will probably want to keep windows for... office is sooooooooo much better than openoffice... gimp doesnt really compare with photoshop either, no matter what ANYONE says... 

wine is great for running most windows apps... but not all... crossover boasts the ability to run some apps wine cant, like photoshop for instance, but it costs monies... cedega is great for games but its buggy as all get out.

hope that helps a bit

---

### Post by wearekosh on 2007-05-05
FYI
here is a cool video on dual booting
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

It worked for me but i did not do it exactly as they did it

I made a full backup of my XP drive and instead of installing XP as they do in the video i pulled the windows cd out before it started the xp install and then dumped my backup onto the drive.

And my reward was a dual boot Ubuntu and (my original) XP

hope this helps  :guitar:

---

### Post by CM Xtasy on 2007-05-05
Do you prefer creating the Ubuntu partition automatically or manually?

---

### Post by wearekosh on 2007-05-05
I manually partitioned half my drive with the XP install cd
(copied my XP onto it and got it working again)
Then put in the Ubuntu cd and partitioned the rest manually too - ( thats the small LILO boot partition and the rest for Ubuntu)
and let Ubuntu install

---

### Post by CM Xtasy on 2007-05-07
> **wearekosh said:**
> I manually partitioned half my drive with the XP install cd
(copied my XP onto it and got it working again)
Then put in the Ubuntu cd and partitioned the rest manually too - ( thats the small LILO boot partition and the rest for Ubuntu)
and let Ubuntu install

No, I'm talking about if I should manually or have it automatically partition my drive for ubuntu.

You guys have been a lot of help, thanks.  Im actually about to do this procedure right now

---

### Post by rsambuca on 2007-05-07
I have always manually partitioned the drive, just so I can make sure it isn't doing something I don't want.  The partitioner is very easy to use, so you shouldn't have any problems.

---

### Post by CM Xtasy on 2007-05-07
> **rsambuca said:**
> I have always manually partitioned the drive, just so I can make sure it isn't doing something I don't want.  The partitioner is very easy to use, so you shouldn't have any problems.

Okay thanks, and how can I tell what my physical RAM is?  Is it the same as my RAM memory?

---

### Post by CM Xtasy on 2007-05-07
Eh, nvm this is all too confusing.  Im at the partitioning options on ubuntu and im stuck on what to put.  I have all the way up to Windows installed so far but idk what to put for the partitions.  I dont have rescue CD (dont know if i really need one).  Can anyone please help me?  I have 60019MB left for all the Ubuntu partitions and a 2048gb RAM.  help please :(

---

### Post by Nythain on 2007-05-07
ok, what part are you at... have you already installed windows and are now stuck at the partition part of installing ubuntu???

---

### Post by CM Xtasy on 2007-05-07
> **Nythain said:**
> ok, what part are you at... have you already installed windows and are now stuck at the partition part of installing ubuntu???

Yes.

---

### Post by Nythain on 2007-05-07
ok, first i would create a SWAP partition... how much physical ram do you have... double that and make a partition that size, filesystem SWAP... then i would just create one big partition ext3 filesystem for /    thats the bare minimum of partitions you need... when creating the partitions, make sure that the big one you created ext3 gets mounted at / or the install wont let you go any further, you NEED /    its whats usually referenced as root (the directory, not the user)

you could also, alternately just click/select the option to let the installer automatically configure partitions using JUST FREE SPACE... not the entire hard drive... very important, the wrong one will delete your windows partition and use that space too... NOT WHAT YOU WANT... (ps, im not yelling, just stressing :))

---

### Post by CM Xtasy on 2007-05-07
i have 2048gb of RAM so I would make it 4096?

and what about /boot?  remember Im trying to dual-boot here

---

### Post by Nythain on 2007-05-07
ok, yes on the size of the swap partition... though you really dont HAVE to make it that big if you dont want to, it is however recommended that you make it at least a little bigger than your actuall physicall amount of ram, so your system can hibernate if you ever want it to...
as for /boot... you dont necessarily have to create a seperate partition for that if you dont want to... some will suggest it for security reasons, but if you dont make one it will just create that directory inside of / anyways... it doesnt really affect dual booting per say, but it is where your grub stuff and boot images are located at... i wouldnt worry about it this go around... if you ever find yourself setting up a linux system in the later future you can choose to create an entire seperate partition for it, but for now, for simplicity, we are just gonna create teh swap and teh rest of the free space for /

---

### Post by rsambuca on 2007-05-07
> **CM Xtasy said:**
> i have 2048gb of RAM so I would make it 4096?

and what about /boot?  remember Im trying to dual-boot here

Yikes, you probably won't even touch the swap as it is with that much ram.  4 Gigs is overkill.

---

### Post by CM Xtasy on 2007-05-07
> **rsambuca said:**
> Yikes, you probably won't even touch the swap as it is with that much ram.  4 Gigs is overkill.

woops D:

well im successfully dual-booting ubuntu and windows xp now. so far no problems even though i havent tried windows yet.

---

### Post by Nythain on 2007-05-07
sweet, glad i could help... hope i helped... hope you enjoy :) any more questions dont be affraid to ask the community, most of us are as helpfull as we can be

---

### Post by CM Xtasy on 2007-05-07
> **Nythain said:**
> sweet, glad i could help... hope i helped... hope you enjoy :) any more questions dont be affraid to ask the community, most of us are as helpfull as we can be

Thanks you helped alot!  now my next goal will probably to install counter-strike 1.6.  again thanks!

---

