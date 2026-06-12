---
title: "installation halted at 85% please read. very detailed."
date: 2007-04-05
forum: General Help
---

### Post by pixeldotz on 2007-04-05
i'm experiencing a bad time trying to get ubuntu 6.10 to install on my machine :(.

specs. pc is about 4 years old now.

2.20 - cpu
1GB - ram
40GB - boot_hdd
mobo - intel845mgl

we'll start from the beginning....

after installing ubuntu 6.10 (flawlessly with no pains) on my brand new laptop i decided to start using it on my main box next to xp before i made the big switch to operate in ubuntu 24/7.

the LIVECD takes about 20 minutes! to start up to where the progress shows up and then gives me a GNOME DAEMON timeout error or such. check cd for defects was no problem burned at 4x with nero and data verified aswell.

using the alternate cd (verified etc..) worked on my uncles pc since the LIVECD give me the same problems as him when i tried to install on his box. so i decided to use the alternate cd using the GPARTED LIVECD first to partition off my HDD.

I can't partition past 10GB for some reason. I had to do it in increments (even after defragging 4 times) so i finally got it to work by making two separate 4.9 partitions then deleting them and formatting the space as one big partition. GPARTED picked it up fine and all was well. i tried making a 1GB swap but it kept failing with the TRY FREEING LESS SPACE errors message.
so i gave up on that one.

now i put in the alt cd and everything passes and gets picked up, all my hdds get picked up and i manually edit the partition table to use the 10GB/ext3 part i made as root.

ubuntu starts installing and i leave for a few hours and come back later to find my pc is off. i reboot and xp starts normally (ntfs chk that GPARTED schedules)  and my UPS doesn't say anything about a power failure so i figured i did something wrong with the ubuntu install. so i start again and this time i have the partitioner format the 10GB part as ext3 again because it says there are some files there (part of the previous failed install). this time i stay here watching everything install and everythings going great.

suddenly my computer stops at about 86% of the final phase of the install. it doesn't hang but it drops down to a terminal and  something like this starts up...

SENDING KILL SIGNAL
SYSTEM HALTED

then my pc shuts down.

anyone have any idea whats going on? is there a way to access the ext3 part from within windows and if so is there a log file i could look at?

EDIT: i found a freeware app called explore2fs and under xp i can see my ext3 partition fine. what folders would have a log of the install if such a log existed?

---

### Post by pixeldotz on 2007-04-05
anyone?

---

### Post by M$LOL on 2007-04-05
Perhaps your processor is overheating? Maybe that's what's sending the Kill signal.

---

### Post by pixeldotz on 2007-04-05
i wouldn't know where to check but i doubt it's the processor. tried it again a few times this morning and between 85-86% is the kill signal/shut down. it'll start immediately backup up into xp no problems. as a matter of fact i'm encoding some videos right now that's estimate to take about 12-14 hrs and i do this on an almost daily basis, did a 16hr session of encoding prior trying to install ubuntu. i let my pc relax for a few hours before i tried the actual ubuntu install.

i've never had overheating problems and to tell you the truth, my pc is running better than ever now that i've replaced the PSU in it last week.

do you have any other suggestions maybe?

a memtest check shows that my ram is fine which was something that i was concerned about since i have had trouble with this particular brand befor (lifetime warrant replacement though) :)

---

### Post by pixeldotz on 2007-04-06
anyone have any other ideas?

---

### Post by M$LOL on 2007-04-06
You're using the Alternate CD right? IIRC, there are two modes, one is OEM and the other is Text Mode. Have you tried both?

---

### Post by pixeldotz on 2007-04-06
actually i have not.

i only tried the text mode option.

i'll try oem right now.

---

### Post by pixeldotz on 2007-04-06
this time the system halted at 8% in OEM mode.

it gets passed the INSTALLING BASE SYSTEM phase and then halts on the software install phase.

SENDING KILL SIGNAL
SYSTEM IS HALTED

---

### Post by pixeldotz on 2007-04-07
i tried today with the 7.04 beta. the LIVECD worked this time to a point. it was still very slowl but i was able to get the installer working.

this however after getting about 50% through ( telling by the progress bar ) the LIVECD dropped to a terminal. no errors or anything but the screen went black and the pc ejected the cd. the hdd ran for a few seconds before stopping.

the pc didn't shut off this time like prior so i had to do a hard reset.


any one have any clue whats happening? i really want to get ubuntu on my pc so i can move away from windows xp.

---

### Post by erothoff on 2007-04-10
Hi,
  The halting at 85% is a problem that I had before. (And actually am having that same problem again but this time in Fiesty, which is how I found your thead.) It has nothing to do with your processor.  It is a download issue. (Your computer is downloading something during this time. My solution if I remember right, (I will be trying it again tomorrow) is to disconnect the computer from the internet during the install.
Good luck.

---

### Post by pixeldotz on 2007-04-10
any idea whats it's trying to download?

i guess i can use my laptop to see any network activity while it's installing.

i'll try this tonight when i get home.

sidenote: after your install wa ssuccesful, did the installation run fine without any problems?

---

### Post by pixeldotz on 2007-04-10
didn't work :(

i'll give up on the dualboot and try for a single install.

if this doesn't work then i can always restore with my ghosted xp :(

---

### Post by pixeldotz on 2007-04-10
so i formatted my entire hdd and still no go. a little bit more research let me to install 6.06 and these are the results thus far... copy pasted from another post i responded to.

> so i got the LIVECD! of 6.06 to install. a little slow of course but no problems with the install. i'm currently upgrading to 6.10 EDGY using the wiki instructions. it's about 1/2 way done. if this works then i'll be happy.

---

### Post by pixeldotz on 2007-04-11
didn't work :(

now i get this error.
kill: could not kill pid '1956': No such process.

so i'm going to drop in 6.06 till the fiesty final comes out.

---

### Post by stet on 2008-07-17
Hey, I know this thread is old, but I just registered for the forums because this problem is happening to me now, with a Dell 300M (with dell's matching optical drive/bottom plate), 1.2Ghz/640MB RAM. I tried first with the 7.10 Live CD, then the 7.10 alternate CD, and now I'm downloading the 6.06 alternate CD to try.

The Live CD would go to a blank screen then shut down, somewhere in the low-80-percent part of the install process. The alternate CD was the same, except that I could see the messages:
SENDING SIGKILL TO ALL PROCESSES
THE SYSTEM IS HALTED

I also tried it without configuring the network and got the same result.

Oh, and at first I tried to partition it, and then I gave up and was using the whole disk.

Anyone else run resolve this other than with using the 6.06 CD?

---

