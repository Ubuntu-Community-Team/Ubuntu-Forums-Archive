---
title: "Big Problems"
date: 2007-05-10
forum: General Help
---

### Post by ihoodz on 2007-05-10
I couldn't find help on most of my issues so I have called the computers manufactuer (dell) and to no success I am left to come here.  I should have came here first.


Alright the situation.

(partitions)
ubuntu partition (fiesty fawn) - 10 gigs (problems here)
"Switch partition" - small (none)
Windows - 15 gigs  (problems here)
Data Partition - 50 gigs (none)

I installed windows on a 15 gig partition, then made the 50 gig for my data and put my data on it.  Later I used the left of my hard drive to install Ubuntu, after a few attemps with the live cd I used the text based cd (which took me 2 times to burn, one copy went corrupt).  I installed ubuntu with no problems, even played a few games of connect four.  I restarted to boot into windows xp for a few things.  Bam first problem (see #1)  (see #2) So seeing the corrupt file I decide, lets reinstall windows on this partition, so I reinstalled on the partition... BAM new problem (see #3). So now we see my problems, I am almost on the edge of banging my head against a hard surface untill I blackout.  I need help to solve these problems

_**Problems**_
1- I had a corrupt version of windows. hal.dll was corrupt  -  How to get rid of it on my boot menu now?

2- Now I don't have a choice to boot into Ubuntu, even though the system recognizes that it has some sort of data on it.  -  Anyway for me to boot back into Ubuntu?   -   How do I get my system to tell that there is Windows and Ubuntu?

3- I can now boot into 2 versions of Windows on that same partition
   Windows xp Home (Working)
   Windows xp Home (Corrupt Dll)  -  How do I get rid of this.


I need some general help here if someone could.  I am currently patching up this version of Windows (the only one that will work) with some updates and reinstalling stuff like certain Media Players.  Any help would make me a happy person.

---

### Post by turbojugend_gr on 2007-05-10
M8 you really messed up there.

First of all where is the latter xp installation on the partition table? You give no info about that.

Now to actually solve the problem... Since you have no data on the ubntu partition tha you care off, since that is a brand new installation, I duggest reinstalling ubuntu.

On the windows issues I 'll be waiting for the answer on the question above.

**EDIT** -> Oh reinstalling Grub using the ubuntu cd will bring ubntu choices back to you.

Ask for specific help when you read this, as I don;'t know you level of knowledge at the moment.

---

### Post by ihoodz on 2007-05-10
I reinstalled the 2nd windows on the same partition of the first windows partition.  I placed my xp cd in (got it when I got the laptop) and went to repair, then it "reinstalled" windows.

---

### Post by turbojugend_gr on 2007-05-10
Hmm i am not familiar with windows xp repair function, but from what I understand it should repair the excisting installation of windows xp not install a new one... Are you sure there are two xp installations at the moment?

---

### Post by turbojugend_gr on 2007-05-10
Pardon my consecutive posts but ideas keep floating here and I can't edit the prevous one cause you mght read it before I am done with it.

The thing is : For you to be sure of the excistance of 2 installations check your harddrive, and plz tell me if you see a renamed old wndows folder or sth like that, that could suggest two installations, I can't imagine how it would manage to keep two installaitons on the same partition else.

---

### Post by ihoodz on 2007-05-10
Lets put it this way.  It was a 15gig partition just for windows.... It still has a full open space of 13gigs, the windows folder on the working file is 1gig without adding in the program files or anything else, which would add another gig.

I'm not even sure that the "Corrupt" windows is even existent anymore, but it appears on my startup none the less.

---

### Post by jerrylamos on 2007-05-10
Best (maybe only) good case is if Windows is the first partition on the first hard drive.  Ubuntu can be anywhere but doesn't like the hard drive to be moved after install.

Best install Windows first, then when it is running, install Ubuntu in some other partition using manual partition to get it in the right place.  I prefer using Gparted to create the partitions before the install, only using the manual partitioner built in to Ubuntu's install to edit the mount point to / and format ext3 and make a swap formated as swap.

Of course first run Ubuntu CD Live and do a few things like internet, etc. to make sure Ubuntu is going to work on your configuration.  If Gparted isn't on System, Administration then use Applications, Add/Remove to install Gparted (yes, on CD Live).

Grub will grab the master boot position and should give you the option of booting Ubuntu or Windows.  It will default to booting Ubuntu but that can be changed by editing /boot/grub/menu.lst (where l is a lower case L).

be VERY cautious about resizing an installed Windows partition, avoid resizing if at all possible.  I've done it but it is very tricky.

Cheers, Jerry

---

### Post by turbojugend_gr on 2007-05-10
@ihoodz: Since that's the case you have to rn the ubuntu CD and reinstall Grub, are you familiar with that? if not say so I ll give you some directions

---

### Post by ihoodz on 2007-05-10
Hm, I already have windows installed and running again.  Problem is, my Ubuntu partition still has Ubuntu on it, so you are saying for me to reinstall it over the 10gig partition again?  I can't run the live cd here, this laptop is a "little" outdated.  256RAM and 1.5 processor.

---

### Post by turbojugend_gr on 2007-05-10
> **ihoodz said:**
> Hm, I already have windows installed and running again.  Problem is, my Ubuntu partition still has Ubuntu on it, so you are saying for me to reinstall it over the 10gig partition again?  I can't run the live cd here, this laptop is a "little" outdated.  256RAM and 1.5 processor.

You dont have to reinstall ubuntu neither to have the LiveCD. What the other user said (pardon my lazyness here :P) is not at all necessary.

---

### Post by ihoodz on 2007-05-10
> **turbojugend_gr said:**
> You dont have to reinstall ubuntu neither to have the LiveCD. What the other user said (pardon my lazyness here :P) is not at all necessary.

I'm still a little worried about it saying I have 2 windows OS's.  What is the diagnostic on that?

Thanks so far this is helping a lot.

---

### Post by turbojugend_gr on 2007-05-10
Actually that shouldn't worry you. No matter what, reinstalling Grub won't touch any data on your machine. 

But if you are too curious to let that go, try a search for sytem32.dll if there is only one there I imagine that the old version of xp is actually the same with the new one, only the corrupted files still exist.

that is of course if you have no issues with the new xp installation.

---

### Post by ihoodz on 2007-05-10
> **turbojugend_gr said:**
> Actually that shouldn't worry you. No matter what, reinstalling Grub won't touch any data on your machine. 

But if you are too curious to let that go, try a search for sytem32.dll if there is only one there I imagine that the old version of xp is actually the same with the new one, only the corrupted files still exist.

that is of course if you have no issues with the new xp installation.

Alright I just done a quick seach fro my sys32 and I found only one.  Hmm, this now makes me a happy person.  I just now have to reinstall some programs for windows again, then install grub tommarow, I have been through so many dell reps on this issue that my head is hurting.  Thanks a lot, now I see why people like the Linux community over the Microsoft community.

---

### Post by turbojugend_gr on 2007-05-10
I have a pay per minute phone number if you are just used to people exploiting you over this :D

:)

---

### Post by ihoodz on 2007-05-10
> **turbojugend_gr said:**
> I have a pay per minute phone number if you are just used to people exploiting you over this :D

:)
lol, to be honest I got my Dell warenty for free, had a friend who worked there plug one in for me.

---

