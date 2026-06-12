---
title: "Changed 14.04 uuid and now can't do anything - won't boot"
date: 2014-10-02
forum: General Help
---

### Post by crazybear on 2014-10-02
After literally weeks of struggling to get my Ubuntu 12.04 upgraded to 14.04 and then able to boot - and then install a new VGA driver...and starting to get it somewhere near what I wanted, I cloned it to make sure I had a copy. I'm used to changing the UUID of the clones - and also changed the uuid of the 'original 14.04' as it had the same uuid as the 12.04. Now, to my HORROR, neither will boot, neither will do anything...the disk or program just say 'no such device as <uuid>. How do I correct this? I can't even begin to imagine going through the months of work again......Thanks in advance! I guess one should never change the UUID?!...and then one can never have an old and new Ubuntu disk in the same machine....learning the HARD way! Ah, I should significantly add that the newest Linux bootrepair disk fails - it gives commands to put into terminal that give errors - so it goes nowhere and only removes grub entirely [I imagine a bug with bootrepair on 14.04, but far from sure...I tried it over and over and over. These were recloned - so still have the grub, but wrong uuid - I do NOT dare to use the bootrepair disk on them...for then they'll have both the wrong uuid and NO grub!....

---

### Post by crazybear on 2014-10-02
I just tried to go in an change the uuid in the fstab on my disk, but I do NOT know how to get permission from a Live CD to do this...I had put in the new number, but then was informed I didn't have permission....and failed. You old hands at Linux probably forgot how hard it is to learn all this stuff - and I have no friends at hand who know Linux - so must find answer and 'friends' on the internet for this. Also, I read that I should also change the uuid in /boot/grub.cfg - but there are always WARNINGS on this and most say it should be done only by running sudo update-grub [should I ever get that far and live that long....]....sorry if I sound exhausted, but the change from 12.04 to a working 14.04 now has taken me a few months and so MANY hours...and I just ****ed it all up again. Thanks in advance. One other thing I see is use of gksudo - but when I try this I'm told I must install some program - which when I apt-get install <gksu> it says program not found and issues other errors...so I'm dead in the water at the moment.... I fundementally don't understand where I 'am' in a live CD and how to 'get' into my disk other than in read only mode - so I can make some changes. I'd also like confirmation that the changes I mention above are the needed ones. Thanks.

---

### Post by Bashing-om on 2014-10-02
crazybear; Hello;

We break it, we fix it, that is the way we learn. If you are going to break your system, then YES dual boot 'buntus !

To the situation at hand:
Let's find out why the "real" system has problems booting by confirming that all UUIDs match to what the system has mapped.
Boot up the liveDVD and have a looksee at what is:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

OK, now, once the partitioning is know from the outputs of the above commands -> 
we mount the appropriate partitions(s) and look at the related files. ( /etc/fstab , /boot/grub/grub.cfg) IF there is an discrepancy in "grub/cfg" then we go looking into the config files located in "/etc/grub.d".
A problem in /etc/fstab -> edit to make sure the UUIDs and the mountpoints match with 'blkid and 'fdisk'.

[INDENT][INDENT]a process in learning
[/INDENT][/INDENT]

---

### Post by crazybear on 2014-10-02
> **Bashing-om said:**
> crazybear; Hello;

We break it, we fix it, that is the way we learn. If you are going to break your system, then YES dual boot 'buntus !

To the situation at hand:
Let's find out why the "real" system has problems booting by confirming that all UUIDs match to what the system has mapped.
Boot up the liveDVD and have a looksee at what is:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

OK, now, once the partitioning is know from the outputs of the above commands -> 
we mount the appropriate partitions(s) and look at the related files. ( /etc/fstab , /boot/grub/grub.cfg) IF there is an discrepancy in "grub/cfg" then we go looking into the config files located in "/etc/grub.d".
A problem in /etc/fstab -> edit to make sure the UUIDs and the mountpoints match with 'blkid and 'fdisk'.[INDENT][INDENT]a process in learning
[/INDENT]
[/INDENT]


Wow Cowboy!....I follow you only so far and you assume I can understand other parts [which I can not!]. I have already tried a live CD and was 100% successful getting the new uuids. Done....but I can NOT find a way to get the permissions to make any changes on my disk from a live CD. You say mount the appropriate partitions. I tried and I got some error message, so likely don't understand the proper wording. I've seen some that only confuse me...such as sudo(?) mount /media/____something___[which they do NOT define]/dev/sd# mnt

Sorry, but with a live CD I can only look in my disk...not change anything, so far. Thanks for the 'suggestion'...but I don't get it fully...it me - not you. I tried the gksudo approach and above told that that failed miserably...as the live CD doesn't have nor will it download the needed program. I tried mounting and failed. I tried all I know and your 'idea' seems missing the needed syntax you assume I know......

...I also didn't mention [yet...now I am] that the clone never booted like the original did [don't have any idea why, but suspect grub problem which bootrepair fails to fix with 14.04]. Original worked after cloning until I messed it up by changing its uuid too.

---

### Post by Bashing-om on 2014-10-02
crazybear; Hey !

We are going to work through all this - together ! ALL of us.

So, for starters show us:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
From the liveDVD terminal.

And Then I show you how to access the installed system and as well how one manipulates files.

I try and teach, what others have taught me ->
[INDENT][INDENT][INDENT]passing it along
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2014-10-02
Basically you have two things busted.
fstab and grub.

I assume you have mounted the installed partition from the files program(nautilus)
If so, try this:
```
sudo -i
```
this will move you into the root user, and allow you to edit the fstab on the installed partition.

next run
```
gedit /the path to the install partitions fstab file
```
or simply type nautilus in the root terminal and navigate to the file from there, then doubleclick to open in gedit.
then edit the file and save and close gedit.
Then, if did this through nautilus, close that window too.
then, with the root terminal still open, type
```
 exit
```
this will end the root session.


The next part is fixing grub
simplest way is with boot repair, which should work
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Use Option #2, you can run this from the livecd.

Follow the directions and hopefully it'll fix grub without errors.
It'll also show a link to paste.com with a number, copy that in case of problems. That link is a web page of what boot repair did on the system, and can be of great help if something went wrong.

I'm not sure if any of my seemingly convoluted advice will help, but I hope it does.
Good luck.

Post back if something went wrong.

---

### Post by crazybear on 2014-10-03
> **Bashing-om said:**
> crazybear; Hey !

We are going to work through all this - together ! ALL of us.

So, for starters show us:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
From the liveDVD terminal.

And Then I show you how to access the installed system and as well how one manipulates files.

I try and teach, what others have taught me ->[INDENT][INDENT][INDENT]passing it along
[/INDENT]
[/INDENT]
[/INDENT]


Thanks. I was able to get the full list of uuids - for the ext4 [my Ubuntu partition] and the swap partition. Please don't ask me to cut and paste - as it is on another machine and there is no easy way to do that here. [and those are LOOOOONG numbers!]

---

### Post by crazybear on 2014-10-03
> **deadflowr said:**
> Basically you have two things busted.
fstab and grub.

I assume you have mounted the installed partition from the files program(nautilus)
If so, try this:
```
sudo -i
```
this will move you into the root user, and allow you to edit the fstab on the installed partition.

next run
```
gedit /the path to the install partitions fstab file
```
or simply type nautilus in the root terminal and navigate to the file from there, then doubleclick to open in gedit.
then edit the file and save and close gedit.
Then, if did this through nautilus, close that window too.
then, with the root terminal still open, type
```
 exit
```
this will end the root session.


The next part is fixing grub
simplest way is with boot repair, which should work
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Use Option #2, you can run this from the livecd.

Follow the directions and hopefully it'll fix grub without errors.
It'll also show a link to paste.com with a number, copy that in case of problems. That link is a web page of what boot repair did on the system, and can be of great help if something went wrong.

I'm not sure if any of my seemingly convoluted advice will help, but I hope it does.
Good luck.

Post back if something went wrong.


Thanks, the sudo -i gives me a root prompt, BUT, try as I might I was not yet able to navigate to the files - whatever I tried in the file system in Unity [which I never use - I use classic desktop...but can manage with difficulty] I get read only. I need to be able to edit the file[s] and permission to run [maybe?!] update-grub. I simply don't know how to....[what the syntax is]. The partition I need is /dev/sda2 , but I don't want to put all of my attempts that failed. I know this is basic, but not knowing is not knowing...thanks..what do I do next? puting gedit /dev/sda2 didn't work...there must be something to add.

EDIT: aha! I added media/ and I eventually got to the fstab in my disk and changed the uuids....now how do I change the other file - by editing or by runing [how and where?] update-grub? I see on the internet warnings about attempting to edit that grub file...and don't need to damage things more!

NOTE: I tried before I changed the uuid's to get the clone's grub reinstalled with the bootrepair disk [which always worked fine on any 12.04 disk...but failed every tiime with a 14.04 disk and I can't find reference to that problem on the internet. I dare not try it again - it leaves the disk with NO grub at all - it only gives error messages and unmet dependencies that can't be repaired.

I tried option 2, and it seemed to re-install grub properly...now to test the disk and change the uuids on the other [original]....will report back....but have others noted that the boot repair disk seems to need updating for 14.04? Thanks...lets see if this worked...

---

### Post by crazybear on 2014-10-03
Amazing! It worked!...on both disks!....only thing it did was deleter the grub customizer program....so will have to find out how to re-install. It also defaults to no unhide - so one can't choose any options...but it works and I hope I'll be able to figure out these smaller problems...Thanks much both of you! typing in some of those very long instructions into a terminal when one can't cut/paste is not easy work! I'm back in business with the 14.04 and have a backup clone - just in case.... again many thanks. I learned a lot...hope I can remember. I took notes on paper and hope I don't loose it.

---

### Post by Bashing-om on 2014-10-03
crazybear; Great;

As you are now booting, may we consider this issue at an end ?
If so, please make this thread solved: top of post -> thread tools.

Any other issues, open as many threads as needed ! _ 1 problem one thread ... like dead men in a box.

Remember:
[INDENT][INDENT]we are all at some point on the learning curve
[/INDENT][/INDENT]

---

