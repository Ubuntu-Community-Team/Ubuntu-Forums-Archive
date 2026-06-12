---
title: "Disaster: partition corrupted - need help on partition recovery tools"
date: 2007-06-03
forum: General Help
---

### Post by bren on 2007-06-03
Hi o helpful ones.

Ok i was just enjoying Ubunto on my dual boot Win XP / Feisty laptop when I decided to use gparted Live Cd to increase the size of the FAT32 partition i am using for data (access from both OS's).

Unfortunately Gparted seems to have quit part way through :(

Current situation
--------------------

[Laptop came with OEM recovery disks and not separate XP install disk.]

On booting Gparted Live CD again I have the following partitions

1) old win xp partition
39GB hda1 NTFS.  Gparted now shows that this partition is empty.   When i try to boot win it fails just after start.   Gparted shows disk errors symbol

2) 10GB hda2 Ubuntu 3.53GB used.    Ok and Ubunto boots OK.   Left immediately to try and avoid overwriting anything I shouldnt.

3) 2GB hda3 linux swap partition (<1GB memory on my machine).   Status Ok according Gparted

4) 23GB hda4 with error status.      Was FAT32 with about 21GB of data on there.    I have it all on DVD (except last few weeks which is only a few photos really)

5) 19 GB unallocated

So any suggestions on what I should try?

I can get back to where I was by

a) using OEM recovery to get fresh win xp install
b) adding data from DVD
c) reinstalling Ubunto etc

But hoping for a short cut!

cheers
bren

---

### Post by H.E. Pennypacker on 2007-06-03
Let's see what we can do by running Ubuntu's Live CD, and seeing if you can access Windows' partition by mounting it.  Hopefully, the problem you're having is something GParted is falsely reporting.  Boot from a Ubuntu Live CD, and let us know if you can access the problematic partitions.

Are you getting any specific error messages?  Let us know about them.

Try to access your XP partition by booting straight to it.  If it doesn't boot, you will get error messages.  We'll work from there.  Start by Googling your errors, and if there are no immediate solutions, report them back here, please.

Do you care about your XP partition at all?  If not, let's not worry about it.  

As far as I am concerned, if there is a serious issue here, rescuing hda4 is going to be the most important thing.

---

### Post by bren on 2007-06-03
Hi HE Pennypacker et al,

I booted Ubuntu Live CD and ran Gnome Partition Editor to produce a screenshot (see attached)

To answer your questions

1) Yes i need to retain XP (for now)

2) When I boot XP I don't get any error messages. I get XPs welcome screen and then sudden blank screen for 2 seconds then BIOS startup screen again.

3) mounting hda4 doesnt seem easy since Gpart indicates the type of this partition is "unknown".    But I do have 99.5% of this data on DVD backup if needed.

Are there win or ubuntu partion / boot recovery utilties that I could try? [remember i only have fujitsu siemens oem xp disks]

any more suggestions.

bren

---

### Post by H.E. Pennypacker on 2007-06-04
It looks like those partitions are quite screwed up at this point, but hopefully there's something that can be done.  Another fellow (and a few others) reported that he was having similar problems, and used TestDisk (TestDisk is available via Synaptic) to fix them.  TestDisk is available here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Here is his original thread:

[http://ubuntuforums.org/showthread.php?t=442395&highlight=partition+unknown](http://ubuntuforums.org/showthread.php?t=442395&highlight=partition+unknown)

There is another similar thread, but it is from a Vista user.  It may still be useful (especially post #6:

[http://ubuntuforums.org/showthread.php?t=404160&highlight=unknown+partition+gparted](http://ubuntuforums.org/showthread.php?t=404160&highlight=unknown+partition+gparted)

Here's an fdisk solution:

[http://ubuntuforums.org/showpost.php?p=2499701&postcount=6](http://ubuntuforums.org/showpost.php?p=2499701&postcount=6)

Last, but not least, the GParted forums likely have dealt with this issue before:

[http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

Let us know how things go.

---

### Post by bren on 2007-06-04
wow!   I have it all back!   testdisk rocks!   :p

for others who find same go here first and make a rescue cd from an iso from [this page]("http://www.sysresccd.org/Main_Page")

now i was trying to burn the iso to a cd on a windows machine without any iso burning capability (just ordinary xp burning tool) so I added[ this powertoy]("http://isorecorder.alexfeinman.com/isorecorder.htm") to allow iso burning 

now i could create and boot with the rescue cd
it was not intuitive interface for me as non linux expert but things you have to do are

a) startx (run GUI)
b) run gparted to see state of partitions
c) run testdisk to repair partion table.    In my case end of NTFS partition was after the end of the physical drive which explains why things weren't working very well
d) find it works!
e) boot windows a few times in command prompt mode.....it seems to die but i think it was actually doing chkdsk
f) boot windows again and it comes up in gui mode and does chkdsk and all seems well

Hurray!

bren;);)

---

### Post by H.E. Pennypacker on 2007-06-05
I usually suck at giving people answers, but it looks like I actually helped someone solve a problem this time.  Sure, I spent time doing it, but it's worthwhile. 

I appreciate your reporting back, and letting us know how things went.  Even better, you explained how to solve the problem.  It looks like this was simply a case of a messed up partition table.

PS: Please help out answering questions newbies have, or even questions in General Help.  It helps when people give what they get (in this case, help).

---

