---
title: "32 bit on 64 bit machine"
date: 2014-07-27
forum: General Help
---

### Post by bearboy518 on 2014-07-27
Hello I was wondering if someone could tell me if I should be running 64 bit instead of 32 bit Ubuntu, I have installed since 12.04 I am now running 14.04 since it came out, but since I did not want to install completely over again I upgraded per instructions, but I notice in the system information it says 32 bit. I know windows runs in 64 bit mode and I read on here that you are supposed to be using 64 bit if your processor supports it, but I was never given a choice when I initially installed it about a year ago.  Does it matter? I mean my system appears to run fine sometime a little slow but I don't know if that is normal or not.  Here are my specs.  Any help would be greatly appreciated.  Thank you!

Ubuntu 14.04 LTS
Memory  7.9 GiB
Processor Intel Core i7-2600K CPU @ 3.40Ghz x 8
Graphics GeForce GT 430/PCIe/SSE2
OS type 32-bit
Disk 740 GB

---

### Post by grahammechanical on 2014-07-27
A 32 bit OS will run on both 32 bit and 64 bit CPUs because the 64 bit CPU architecture is backwards compatible with the architecture of the 32 bit CPUs. But a 64 bit OS will not run on a 32 bit CPU. The CPU 32 bit architecture is not compatible with the 64 bit OS computer code. That is a fact.

In the past the Ubuntu web site recommended downloading the 32 bit Ubuntu ISO because even if the new user did not know anything about CPU architecture at least they would get a version of Ubuntu that worked on their computer. But truthfully, if we have a 64 bit CPU we should be running a 64 bit OS. That is true of Linux. Windows is a different matter. With Windows there is a minimum RAM consideration.

Right now the Ubuntu web site for downloading Ubuntu 14.04.1 is putting the 64 bit version first on the list and as regards the 32 bit version it says: "for machines with less than 2 GB RAM." Which I find it hard to believe as I am running Ubuntu Utopic Unicorn (14.10 development) on an Intel core 2 Duo 2.4 GHz with only 1 GB RAM and I am not experiencing any issues. In fact I am noticing that Ubuntu is making better use of RAM than 12.04 ever did. Perhaps the person who wrote that sentence is running a machine with the amount of memory that you have in your machine.

To tell you the truth, I cannot understand how it is with the hardware you have that you are running 32 bit Ubuntu.

Regards.

---

### Post by Bashing-om on 2014-07-27
bearboy518; Hello !

If it were me on that system:
> 
Memory 7.9 GiB
Processor Intel Core i7-2600K CPU @ 3.40Ghz x 8

I would be running with 64 bits !

For you to do so from 32 bits would require a fresh install of the 64 bit version. ( there is no optionals, it is either a 32 bit install or a 64 bit install, depending on the instalationl medium )

[INDENT][INDENT]if ya got it
[INDENT][INDENT][INDENT]flaunt it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bearboy518 on 2014-07-27
If I reinstall a 64 bit version is it going to make a big difference in the way my system preforms? I don't remember it even giving me a choice when I installed it, but I have so much stuff installed on here that I don't want to lose.  Is there a way to see a list of all the packages I have installed since installing the system or just have to kinda make a mental note and try to figure out what I have installed?  Sorry to ask so many questions.

---

### Post by QIII on 2014-07-27
Hello!

Will it make a difference that you will notice -- assuming you are just doing normal stuff?  Sometimes.  Sometimes not.  If you are doing heavy calculations (into which basket I would put gaming, scientific applications, video and image processing, etc) then it will.

The big thing, however, is that the industry has pretty much gone 64 bit now.  When things went from 8 to 16 bit and from 16 bit to 32 bit, there were hold outs who steadfastly maintained that there was not reason to switch.  They soon got left out in the cold with old software that was no longer being updated.

As for saving what you have installed -- at least from the Ubuntu repos -- you can capture that with 

```
dpkg --get-selections > somefilenameyouwillremember
```

This will generate a list in your /home.

When you reinstall, you can installl those packages again with 

```
dpkg --set-selections && sudo apt-get dselect-upgrade
```

Anything you have installed from outside the repos you will have to make note of and reinstall from that source.

When you do reinstall, though, make sure that you have first backed up your /home in case you obliterate it.

If you have a separate /home, you can just choose "Something Else" when the installer gets to the part about creating partitions and choose not to formate your /home.  But still back it up anyway beforehand because bad things certainly can happen.

---

### Post by linux_dream on 2014-07-27
My experience with 32 bits vs 64 bits is that some programs will run faster with the 64 bits system. For example with the free chess engine Critter I got a 30% speed increase passing from 32 to 64 bits and for Stockfish chess engine, a boost of 25%.

---

### Post by bearboy518 on 2014-07-28
> **QIII said:**
> 
When you do reinstall, though, make sure that you have first backed up your /home in case you obliterate it.


Thanks for your reply. I think I will reinstall and see if my computer runs any faster. with the /home directory, does this mean I should back up the entire /home directory just the way it is and just copy it back when I'm done? Just copy it exactly and then copy it back when I reinstall?  Thanks for your help.

---

### Post by bearboy518 on 2014-07-28
> **QIII said:**
> 
When you reinstall, you can installl those packages again with 

```
dpkg --set-selections && sudo apt-get dselect-upgrade
```


Sorry.  Also, when I use this to reinstall the packages, how will I specify the file to use like somefilename like you indicated? or do I have to do them one by one, or is this just to give me a general idea of what I had installed?

thanks again.

---

### Post by Bashing-om on 2014-07-28
bearboy518; Hey;

This is but one general approach to (re-)installing packages that the package manager is aware of:
```

##From old install##
dpkg --get-selections > ~/my-packages
##From New install##
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```
See:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
for a working example.

Of course you will copy the file named here as 'my-packages' off to a safe place, and in the new install copy that file back - to say your home directory as the Present Working Directory. That file is but a text file and as such is editable to make any changes in the file to accommodate the package manager in installing - or not installing - what you want.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by slooksterpsv on 2014-07-28
With that system it should support PAE which may allow you to use the full extent of your  RAM - 8GB. With 32-bit systems generally you can only use 3.25-3.75GB of RAM (depending on Windows, system, etc.) because 4GB is in the 64-bit range. 

What everyone else has stated is true, if you're running high performance apps like gaming, scientific, etc. 64-bit will be a lot better, but that's all dependent on what you use.

Personally I highly recommend using the 64-bit version of Ubuntu. You may not notice the differences until you're running a bunch of stuff. In a 32-bit some apps may not be able to take advantage of the PAE and require memory addressing in the lower 4GB of RAM (0-3.99GB); some apps won't care and will use it wherever (0-7.9GB); some apps may not have a 32-bit version - very rare, but some don't now-a-days.

If you give us some information on what kinds of things you want to run, we can give you some suggestions or even specifics of what you may want to run. I stand by 64-bit and have been running 64-bit since I got my first 64-bit CPU - AMD Phenom 9550.

---

### Post by bearboy518 on 2014-07-29
> **Bashing-om said:**
> 
```

##From old install##
dpkg --get-selections > ~/my-packages
##From New install##
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```
See:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
for a working example.


Thanks for your reply.  I did reinstall and noticed a big difference in speed (especially when going from text back to graphical) but I need to get the right video driver in It's way off and I don't want to do anything until my packages are installed.  I read the link you mentioned and Both ways I am getting errors that look like this:

dpkg: warning: package not in database at line 1118: xserver-xorg-video-geode
dpkg: warning: package not in database at line 1120: xserver-xorg-video-intel-lts-raring
dpkg: warning: package not in database at line 1126: xserver-xorg-video-openchrome-lts-raring
dpkg: warning: package not in database at line 1138: xserver-xorg-video-vmware-lts-raring
dpkg: warning: package not in database at line 1152: zlib1g:i386
dpkg: warning: found unknown packages; this might mean the available database
is outdated, and needs to be updated through a frontend method

The command does not seem to be doing anything at all.  Just pages of this.  Does database just need to be updated?  Thanks for your reply and help.  It is truly appreciated.  My research on the dpkg command has not yielded any information on updating a package database, or I am just dumb.

---

### Post by Bashing-om on 2014-07-29
bearboy518; Hey,

Like advised, those "dpkg: warning:" - graphics driver related -items are a result of non repository package files, as well, things you do not want in the new install (raring).
Edit the resultant "my-packages" file , or what ever name you chose for the text file - with you favorite text editor and remove those entries.

dpkg can not and does not cope with anything that is not a part of the ubuntu software management system directly.

In the new install, install the appropriate graphics driver.

[INDENT][INDENT]a means to an end
[/INDENT][/INDENT]

---

