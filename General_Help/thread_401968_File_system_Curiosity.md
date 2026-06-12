---
title: "File system Curiosity"
date: 2007-04-05
forum: General Help
---

### Post by FrozenFOXX on 2007-04-05
I've been wondering about the file system lately.  By default Ubuntu uses ext3 as far as I can tell and of course should support something different like XFS or ReiserFS.  My first question is would there be a way to have a fresh Ubuntu installation from the graphical installer using a different filesystem or would I have to build that from the command line and then tell the installer to use those formatted partitions without reformatting?

My second question is why ext3?  I've been reading a bit about it and while to my knowledge, like ext2, ext3 doesn't get file system fragmentation easily it still happens (as from my reading all file systems do eventually).  To my knowledge internal fragmentation and external fragmentation aren't really an issue with any UNIX file system but there are few methods of defragmenting ext3 (shake seems to be popular) whilst some of the other popular file systems out there already have well-defined framentation tools.

My final question is should there be anything done about this?  I mean, I don't know if it's really a problem (I certainly haven't had one but then I don't do any performance benching so I have no basis for it other than gut feeling) but it sounds like something that perhaps should be addressed in some fashion (either FAQ or change in default tools/file system).



Just curious, thank you for sating my curiosity.

---

### Post by ben.s on 2007-04-05
The simple answer is that ext3 is the most widely used, and therefore tested and stable (possibly even mature) open source linux filesystem there is.  When it comes to your filesystem, the most basic building block of your OS -- on which all else (literally) rests -- you want it to be as stable as possible!

What filesystem is "best" is bound to generate a nearly religious argument... and it's really a matter of personal choice.

---

### Post by garlik42 on 2007-04-05
You can select the filesystem you want to use during the install.

You must select manual partitioning of the drive. 

I typically use ext2 for my /boot and reiser for everything else, except for an area that will handle huge files (video dvd images etc) I use xfs.

I have to agree with ben.s about the religious argument comment, it really is a matter of preference. And experience.

---

### Post by az on 2007-04-05
> **FrozenFOXX said:**
> My first question is would there be a way to have a fresh Ubuntu installation from the graphical installer using a different filesystem or would I have to build that from the command line and then tell the installer to use those formatted partitions without reformatting?.

The graphical installer has only a few explicit goals.  One is to properly install the system.  The other is to be as simple as possible.  It's not that you shouln't have options, but that the graphical installer is not the tool for all those options.  The number of clicks that the user must do to install the system are counted and are kept as low as possible.  I think you can install a system in seven clicks?

You can use the alternate cd for that.  That being said, the manual partitioning stage can offer you different filesystems, I think.



> **FrozenFOXX said:**
> 
My second question is why ext3?  I've been reading a bit about it and while to my knowledge, like ext2, ext3 doesn't get file system fragmentation easily it still happens (as from my reading all file systems do eventually).  To my knowledge internal fragmentation and external fragmentation aren't really an issue with any UNIX file system but there are few methods of defragmenting ext3 (shake seems to be popular) whilst some of the other popular file systems out there already have well-defined framentation tools..

Ext3 is rock-solid and has been for years.  It has pretty good performance (certainly for a desktop system) and is extensible.  It's infrastructure, AFAIK, is non-limiting.  Nothing prevents new features from being added to it.  

Just because there are tools doesn't mean you need them.  AFAIK, you will fragment an ext3 filesystem with normal use when it gets full, but likewise, you will defragement it with normal use when you free up some space. 

Again, there is no reason to not have a defragmentation tool - Ext3 has been around for ages and nobody has bothered to write one.  No one is preventing anyone from writing one, you know.

> **FrozenFOXX said:**
> 
My final question is should there be anything done about this?  I mean, I don't know if it's really a problem (I certainly haven't had one but then I don't do any performance benching so I have no basis for it other than gut feeling) but it sounds like something that perhaps should be addressed in some fashion (either FAQ or change in default tools/file system).




If someone wanted to add functionality to ext3 and it was stable and popular, Ubuntu would pick it up and use it - no reason not to.  There is a Common Questions section maintained by the docteam, and i beleive they touch on defragmentation.  If not, someone could add a paragraph.

---

### Post by FrozenFOXX on 2007-04-05
Thanks for the responses, they make for an interesting morning read.  I, too, believe that a debate about file systems is a Bad Thing (but then I'm a vi user so I've had a good share of that already).  I wasn't looking to start a debate about it, was just curious about why this one.

Az, I, too, thought that the ext3 system would defragment the more free it got but so far I haven't found any specific information on that in my searching.  If you happen to know anywhere offhand that lists that would you mind sharing?  If not don't worry about it, I'll just look harder later (lots of other important questions need attention, mine's not one of them).

The bit about the fragmentation tools is interesting.  If the file system only fragments under heavy load (nearly full) then that would be a reason NOT to have a defragmentation tool, wouldn't it?  If that's true that would certainly be a good reason not to have one.




Thank you, Garlik42, for mentioning the extra formatting options with manual partitioning.  Since a recent "accident" I've decided I'm going to have to reinstall from scratch for Fiesty anyway so that'll be a good chance to experiment.  I, too, believe in a ext2 format for a separate /boot partition (just always seems like a good idea).


Again, I appreciate the responses.  So far I'm really enjoying (K)Ubuntu (and I'm in the 64-bit camp even) and I'm glad there's such level-headed support for it (I come from Gentoo...renowned or infamous for its support depending on who you talk to).

---

### Post by garlik42 on 2007-04-06
> **FrozenFOXX said:**
> 
Thank you, Garlik42, for mentioning the extra formatting options with manual partitioning.  Since a recent "accident" I've decided I'm going to have to reinstall from scratch for Fiesty anyway so that'll be a good chance to experiment.  I, too, believe in a ext2 format for a separate /boot partition (just always seems like a good idea).


Again, I appreciate the responses.  So far I'm really enjoying (K)Ubuntu (and I'm in the 64-bit camp even) and I'm glad there's such level-headed support for it (I come from Gentoo...renowned or infamous for its support depending on who you talk to).

Funny how you mention coming from Gentoo, I am still an active gentoo user, but I have changed from using gentoo for everything, to using gentoo for servers, and using ubuntu for desktop stuff. And while I have had a couple of "almost" flames here, it's nothing like the hostility that exists at gentoo. Hopefully gentoo will get better, they have quite a bit of talent.
I also have been experimenting with the 64-bit stuff, but last night I faught with MythTV and was unable to get a picture on the screen, I am going to try a fresh 32 bit install tonight and see if that works better.

---

### Post by FrozenFOXX on 2007-04-07
So far I've been really pleased with the 64-bit support overall, I just wish there was even more of it (looking into seeing if there's anything I can do to help that along...maybe package up a few things or something).  I was going to run 32-bit but for me I think if I don't run 64-bit now then there won't be any motivation for anyone to make it run better (but that's just my opinion, I don't pretend to think everyone should follow it.  The 32-bit version has plenty of advantages of its own).

It's good to hear someone else has experience with Gentoo before Ubuntu.  I really like the IDEAS of Gentoo (no releases, just update.  Customize a system to your exact specificiations to reduce cruft.  A system that builds itself and is adaptable, flexible, and powerful) but in the years since I've started with Gentoo to now I think it's really gone downhill.  At least there's still absolutely fantastic documentation for some things, though, I find myself refering to their docs and how-tos for all kinds of things. :)

Well, I guess my final question is how's ReiserFS support nowadays?  When I used it last the file system crashed and rendered my installation dead.  How?  Dunno, but apparently it had something to do with the stability of ReiserFS support at the time (essentially it thought the disk was overfull and could not run any commands...again, NOBODY I talked to had any idea and I haven't run it since).  Anyway, thought I might try it again if it's gotten any more stable.

If not ReiserFS any other hot file systems anyone would care to recommend?  I don't usually keep up on what's really amazing in the day-to-day sense.

---

