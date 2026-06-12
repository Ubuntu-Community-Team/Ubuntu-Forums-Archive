---
title: "Gparted.. good or bad"
date: 2008-03-19
forum: General Help
---

### Post by coninsan on 2008-03-19
Hi

First of all i would like to say thank you to everyone and all that have helped to get my linux up on its feet.

the main thing is that i am standing at a turntable, i am about to resize my main partition where my OS is located, and i am planning to do it with Gparted live cd.

at this point i do not have space on my main partition for a full backup of my system, remastersys symply just halts in the middel of the process, but i am thinking, is it needed, when i used gparted on my sekondary partition it resized it and all my data on it stayed put without a glitch.

So should i take the time to backup my files on a external drive and make room for a backup with remastersys and then resize, or should i trust Gparted and jump on out into it?

---

### Post by Shazaam on 2008-03-19
ALWAYS back up your data. I learned this the hard way (trashed install). You could use an app a million times without any problems, but I would bet that the time it does fail is the time you need it the most. Murphy's Law, of course. :lolflag:

---

### Post by Herman on 2008-03-19
I agree, it doesn't matter how good the hard disc partitioning program you are using is, it is always recommended to back up your data first.

GParted is the best in my opinion. Normally CDs and CD/DVD drives, hard drives and hard drive partitioning programs are reliable, but all it takes is a microscopic grain of dirt on the lense of your optical drive or a scratch on your CD, and you could end up with a corrupted partition table, (rare I know, but possible).
If that happened, you could use TestDisk to fix your partition table, but even better, you can avoid the whole situation in the first pace by taking the time out to back up your data.

Besides, your hard drive can go south any time, and you may thank yourself some day for having made that recent backup. It should be a habit to make regular backups.
If you have too much data and you can't make backups, is it best to mentally condition yourself to consider the data as already lost or not even belonging to you at all. 

An external hard drive can be worth its weight in gold.
... or maybe many times it's weight in gold.

Regards, Herman :)

---

### Post by coninsan on 2008-03-20
Thansk for the good answers :-D

Herman, the matter of the fact is that i trust my internal drive more than my external, sure there is a bigger possibility that my internal drive would get scrambled, but, i have experianced the opposit.

I got my first exteral drive of the internet via pixmania, all the way from france, and it did only survive 3 months before the drive began to smoke and the internal mechanics was toasted, sort of the same happened to the next 5 external drives i had, thats why i do not trust my external drives.
after all an external drive is only a normal drive that has been added some chips so it can work, who  can with surtainty say that those few chips are sufficiant to make it run probberly, or maybe its just a tikking timebomb waiting to go off. :lolflag:

---

### Post by mcduck on 2008-03-20
> **coninsan said:**
> Thansk for the good answers :-D

Herman, the matter of the fact is that i trust my internal drive more than my external, sure there is a bigger possibility that my internal drive would get scrambled, but, i have experianced the opposit.

I got my first exteral drive of the internet via pixmania, all the way from france, and it did only survive 3 months before the drive began to smoke and the internal mechanics was toasted, sort of the same happened to the next 5 external drives i had, thats why i do not trust my external drives.
after all an external drive is only a normal drive that has been added some chips so it can work, who  can with surtainty say that those few chips are sufficiant to make it run probberly, or maybe its just a tikking timebomb waiting to go off. :lolflag:

External drives, when properly handled, are just as reliable as internal drives. the ATA-USB controller chip doesn't make them any more or less reliable than the drive itself.

Anyway, it's a known fact that _every_ hard drive breaks, maybe today, maybe after 10 years. But as long as you have _any_ files you consider valuable to yourself you should _always_ have a backup of them on some external media. If not on external disk, then on CD's or DVD's.

Why not keep backups on internal drive? Because if your power source or motherboard breaks it might easily take all your hard drives with it. This makes backups on internal drives rather pointless..

And why you should always have those backups? Because when you start noticing theres something wrong with your system it's usually already too late, your files are already gone or corrupted. While you may sometimes get a warning before your hardware completely fails, it can also happen suddenly with no warning.

When people loose their data because of disk failures and such I don't feel sorry for them any more, loosing data for such reasons is not bad luck, it's just own stupidity because they didn't make backups.

---

### Post by Herman on 2008-03-21
> Thansk for the good answers :grin:

Herman, the matter of the fact is that i trust my internal drive more than my external, sure there is a bigger possibility that my internal drive would get scrambled, but, i have experianced the opposit.

I got my first external drive of the internet via pixmania, all the way from france, and it did only survive 3 months before the drive began to smoke and the internal mechanics was toasted, sort of the same happened to the next 5 external drives i had, thats why i do not trust my external drives.
after all an external drive is only a normal drive that has been added some chips so it can work, who can with surtainty say that those few chips are sufficiant to make it run probberly, or maybe its just a tikking timebomb waiting to go off. :lolflag:Sure.

Well, the important thing is you have your data stored in at least two different devices, if your internal hard drive fails or your computer blows up, you will still have most of your data in your external hard drive. If your external hard drive fails, you still have your data inside your PC and you just go buy a new external hard drive.
I don't know how much people's data can be worth, Usually it doesn't seem to be worth much until people think they have lost it, and then suddenly it becomes as valuable as irreplaceable works of art, and really it can be. It is because of the way our human minds work that we don't think it's valuable when everything's okay.
I have recovered data from old backups that was worthless when the backup was made. It turned out to be valuable for proving certain work was done after the paperwork had been accidentally destroyed and a company I worked for had some trouble collecting money from another company that the work was done for. My employer was sure glad I still had the information. The value of the information turned out to be many, many times the price of a computer, let alone an external hard disk.

My wife and I use external hard disc drives, we have one each and they are both quite old and there are no problems with ours yet.
If something went wrong with the electronic chip part I would just take the case apart by removing the retaining screws and slide the hard drive our and plug it in to an IDE cable or a new external hard drive case and keep on using the hard drive.
The hard drive case with the electronic chip and USB/IDE adapter only cost me about $20, so I'd just throw that part away.
My wife is pretty rough with her external hard drive, she carries it to her office and home again in a bag and she doesn't take any particular care about how she handles it. Often the hard drive inside gets shaken off the IDE connector and I have to open the case and re-attach it for her. Hers is still working fine even with that kind of treatment.

One thing neither of us do is expect our external hard drives to run an operating system. When they're just used as data disks, which is all they are designed for, they only spin for a while when we're reading and writing to them, and they don't build up excessive heat.
I am always worried about people installing operating systems in external hard disk drives, USB flash memory drive4s are okay, but external hard disk drives, (in my opinion anyway), shouldn't have an operating system running in them. I don't think most of them have a cooling fan in their cases, at least none that I have seen.
Excessive heat buildup would probably be the number one killer for hard drives, in or out of a PC case.

Thanks mcduck for your useful post,
> Why not keep backups on internal drive? Because if your power source or motherboard breaks it might easily take all your hard drives with it. This makes backups on internal drives rather pointless.. I agree!
In fact I have an old PC I used for looking at when I first began learning about PC hardware. It was given to me for free from a friend because it was completely fried, and thus of no practical use at all. (Except to learn what the different PC parts look like). The power supply had failed, and over-volted all the rest of the parts in that PC, (it was a cheap and nasty brand that isn't made anymore).
Power supplies are about the most important part of a PC, well, all the parts of a PC are important, but the power supply is the part that most people don't think about as much, so they have a cheap one instead of the best one. The power supply can fry the rest of your computer if it's a cheap one. An expensive one should last longer and if it ever does fail, should fail on the safe side and switch itself off to protect the rest of your computer parts.
I'll bet 99.9% of computer users wouldn't even know what brand of power supply they have, and they probably have the cheapest available, so the risk that mcduck has pointed out is real. Thanks for reminding me, mcduck. 

Regards, Herman :)

---

