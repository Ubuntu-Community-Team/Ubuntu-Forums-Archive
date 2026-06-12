---
title: "Computer crashes"
date: 2008-04-06
forum: General Help
---

### Post by 828688 on 2008-04-06
I have Ubuntu and I don't have any other OS installed in my computer. I had left my computer (which is a laptop) on and closed while being out and some "brilliant" cleaning employee of mine left it covered while I was out. When I returned the computer was very hot and I uncovered it as I logged back in on it to resume my work. Then right after a couple of minutes of working fine (and still being hot) the hard drive started ticking and ticking, so the computer froze and eventually crashed. I turned it off by pushing the power button and I tried turning it back on.

It started running fsck automatucally and it took many times (turning off and on with the power button) until it reached 100%. Then I could run Ubuntu just fine and log back in the OS and everything just fine (it was being slow while loading). But then after a couple of minutes the hard drive started ticking again. I tuned it off with the power button again and turned it back on. 

After turning it back on several times, sometimes it showed things like:

"drive not ready for command"
"GRUB loading, please wait"
"GRUB loading, please wait
Error 10"
"GRUB loading, please wait
Error 18"

And sometimes not even that, it would show the blinking _ cursor or a blank screen.

Then I waited several hours and I tried again. I turned it back on and it loaded Ubuntu just fine and I could log back in again and everything just fine. Then after a few minutes it froze again while I could hear the ticking sound in the hard drive again. I tried turning it off with the power button and back on and it kept on showing errors like those I just showed and the hard drive still ticking...

Could it be that the hard drive is damaged and I'll need to dispose of my hard drive and buy a new one and reinstall everything in the new one?

Please help :(:confused:](*,)

---

### Post by BaffledMollusc on 2008-04-06
It does sound like a hard disk problem.

I think the first thing you should do is get any important data off the drive. If you manage boot into Ubuntu you could back up the data onto DVD or a flash drive. If you can't get into Ubuntu, you may have some luck booting the laptop with the live CD (i.e. the one you used to install Ubuntu). Depending on what part of the disk has errors you may be able to copy files from the hard drive while running off the Live CD.

Once you have backed up any data you can start trying to fix the hard drive. If there are errors on the disk itself you may be able to use the fsck command to fix them. If the problem is with the mechanical parts of the drive itself, I'm guessing you're out of luck.

---

### Post by 828688 on 2008-04-06
With the little time the laptop allows me to work just fine, I managed to open a terminal and I typed fsck and something like this appeared:

user@computer:~$ fsck
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/.static/dev/hda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may
cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted
user@computer:~$ 

Maybe I don't know how to run fsck? I'm kind of new at this. If I seem not to know how, could you please give me the instructions?
I also tried opening the Ubuntu kernel in recovery mode and it started showing many tasks being done and finishing with "done." then several lines and numbers appeared as if it was checking something saying something like "I/O hda" (i don't remember the rest) along with many numbers.
Then all of a sudden all this scroll disappeared and it displayed a blank screen while I still was able to hear the hard drive ticking. I turned it off and waited for it to cool down.

Seems like when the laptop starts warming up the hard drive ticks because after a few minutes of working fine it crashes again.

Does it sound to you more like a hard drive problem? Could it be fixed with fsck?

---

### Post by ghost_ryder35 on 2008-04-06
boot the comp with a live cd and run fsck, that way the drive is not mounted.

---

### Post by 828688 on 2008-04-07
I don't have the live CD with me, but I was able to run fsck by opening up a terminal during the little time it lets me work in there and I typed sudo control /forcefsck or something like that and when I restarted it after many tries yesterday, it failed, but today morning it ran fsck and reached 100% successfully in a very fast way. 

Nevertheless, the problem still remains. After a few minutes of working just fine, it again crashes while the hard drive makes a sound of ticking. (tick, tick, tick) Then I have to turn it off because it doesn't work at all. (edit) The screen looks frozen.

Now, after these details probably it could sound more to you that it is a hard drive problem and I need to dispose of the hard drive and buy a new one? :mad::confused::(](*,)

---

