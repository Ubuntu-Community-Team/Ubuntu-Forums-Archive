---
title: "Dual Boot, should I uninstall Wubi first?"
date: 2014-04-27
forum: General Help
---

### Post by Budchekov on 2014-04-27
I'm about to dual boot Xubuntu 14.04 LTS with EX-P,  could leaving the Wubi install cause booting confusion, is it better to get rid of it first ?

Advice appreciated.

---

### Post by Bashing-om on 2014-04-27
Budchekov; Hi !

May I suggest this:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
as the better option ?

[INDENT][INDENT]do it well
[INDENT][INDENT][INDENT]or don't do it at all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Budchekov on 2014-04-27
Thanks 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1111508") 				 				 					 						 	[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") , I've explored that option, way above my pay scale.

The only reason I'm even thinking of keeping the Wubi install is if I forgot to backup somethng, it's there.

It's the booting issue I'm concerned about.

---

### Post by Bashing-om on 2014-04-28
Budchekov; Morning,

Look, I have no experience with WUBI so my perspective is different than yours. I am aware that WUBI does have it's limitations and is no longer supported due to incompatibilities with UEFI.
All I can do is relate what I would do.
Save whatever files I have in the WUBI install;
From within Windows, delete that WUBI file.

Now to install Xubuntu as a true dual boot you have a couple of options.
a) Take the easy way out - for those less experienced - and let 'buntu's install wizard take care of all details and accept the default set up. That option is "install along side".
b) Set the system up like you want it. That option is "something else".
1) defrag Windows 2 times;
2) In Windows maybe remove an unneeded partition ( recovery - you have made a copy to DVD of that partition, yes ?), or shrink a present partition and set aside 50 or so gigs for xubuntu to install to and then run Windows check disk utility; Reboot Windows a couple of times to make sure Windows is still happy.
3) IN the xubuntu install choose the "something else" option and set up partitions manually for xubuntu - minimum a '/' and 'swap' partitions -> setting up a /home partition is also a good thing.

Now the booting situation; Windows will not talk to 'buntu, but 'buntu  can will and does talk Windows; as only one operating system can control the booting process (single hard drive install with both operating systems installed to same hard disk) that leaves the only option as 'buntu to be that controlling operating system. When you install xubunt, grub (GRand Unified Bootloader) will install and chainload Windows to it's boot menu .

There is a lot of anxiety on your part to make this happen, I assure you it is easier DONE than said. Decide what you want to do, make a plan on paper, back up all your files - Murphy's Law always applies - any error could wipe out Windows ! - and just do it.

I stress that the install wizard is smart, real smart. The default setting will be just fine for just starting out. Once you have some experience under your belt and know what you want of your system; you can then back up and re-install. It does depend on how much space you think Windows requires to continue to function efficiently. Window's too needs a bit of elbow room and operating overhead. A small hard drive and a large Windows "might" be a problem - not expected - .

[INDENT]A piece of cake
[INDENT][INDENT][INDENT]thousands and thousands have done it
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Budchekov on 2014-04-28
Hmm.....
You're kinda missing the point, that's exactly what I'm going to do and have done several  times, this is the first with Wubi installed, it was a simple yes or no question regarding a possible booting conflict.
Thanks anyway, :) obviously without any specific info to the contary it's logical to remove Wubi first.

---

