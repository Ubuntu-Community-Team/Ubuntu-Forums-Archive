---
title: "What size SSD for Ubuntu?"
date: 2014-01-03
forum: General Help
---

### Post by PsychedelicWonders on 2014-01-03
I plan on having Ubuntu on it's own dedicated SSD drive, I'm just wondering if 120g will be enough?  How many gig is the OS itself & I'm just wondering what kind of other programs I'd want to put on here.  I like iTunes (I don't care what anyone says about it, it has the best visualizer I've ever seen in my life), Firefox, GPA Privacy assistant, truecrypt Filezilla, photoshop, dream weaver and maybe a handful of other ones.  I realize I'd still be using Photoshop/Weaver in windows, which I'm fine with.

I know Windows 7 is around 30g I think? But with all of the other programs, a couple games & some bloatware that I need to clean up, I'm all the way up to like 170g for my Windows 7 OS drive.

I plan on also upgrading my Windows 7 to a new SSD, but I'm going with the 240 for that.

I don't know how much I plan on using Ubuntu, I'd like to use it as much as possible and use it full time, but it's hard to get away from windows with certain programs like Photoshop CS4 and a few others I like to use, so even when I ran Ubuntu before (and that was maybe 4-5 years ago?) I would always have to jump to windows to do something and then once Win7 came out it was actually pretty nice to use so I migrated back over to it 100% of the time.

But I'd really like to get back to Ubuntu and get some more security between myself & that scary internet.

What version of Ubuntu should I get?  I just read that there is one that is expiring or something this month?  So wait for the newest version?

Also a big thing for me, will my Microsoft wireless keyboard & mouse work in Ubuntu?

I also want to starting using Ubuntu OS for mobile once it's fully ready, hopefully this year.  I currently have an iphone but will probably switch to the newest Samsung Galaxy once it's fully operational, so I am wondering if it's even worth it to buy a new SSD for Ubuntu at this point if Mobile OS will be ready soon?

---

### Post by king.of.random on 2014-01-03
Okay first thins first. Photoshop, itunes etc will not work in Ububtu. Wine is an option (it's a kind of compatibility layer) but you still won't be able to run the latest windows software. You could visualise windows within linux if you have a spare license but then if you're dual booting there would be little point. My suggestion would be is to run your windows programs in windows and discover the alternatives to i-tunes and photoshop in Ubuntu. For instance you have Rhythmbox which looks and feels similar to i-tunes. Amarok (my favourite) is a different beast but once you get your eye in is really powerful and if you have an ipod both will hook up. For photo shop we have Gimp and Darktable; both very powerful editors. Darktable for instance can handle RAW files. On the subject of RAW Ufraw is another option. I guess what I'm trying to say is have a dig in the repositories and see what is available.

On the subject of disk space linux/Ubuntu takes up much less room on your hdd than windows. I tend to have a 20G / partition, 4G /swap and /home as big as I need to cater for my files. You could even share your windows documents folder in Linux; although this isn't recommended to a newbie for security reasons.

13.10 is the latest release but is a short term release. 14.04 will be the next long term release and should be available in April. My recommendation would be 13.10.

I hope this personal view helps.

---

### Post by papibe on 2014-01-03
Hi PsychedelicWonders.

The OS would be around 15Gb. With some games and a couple of years of use, mine is around 20Gb (12.04). I'd recommend a root partition of 25Gb. Match your RAM for the size of the swap partition.

I'd recommend installing 12.04 and then upgrading to 14.04 later on April.

Almost all keyboards and mice will work on Ubuntu. Some special keys may not work, but most standard extras like media keys usually work ok.

Hope it helps.
Regards.

---

### Post by PsychedelicWonders on 2014-01-04
Yes I realize all of the programs I am used to using, for the most part aren't avaialble in Ubuntu unless through Wine - but I'd rather just use the normal programs in windows if I needed/had to use certain ones.  And like I said iTunes has the most amazing psychedelic visualizer EVER!

I am not opposed to learning exploring their twins within Ubuntu, but I've spent years learning some programs like Photoshop, so it would be hard and very confusing to jump in and try to learn Ubuntu and every other program from scratch.

So Ubuntu OS is 15g, does this include all of the programs you've suggested such as Gimp, Darktable, Rythmbox etc?  Or would all of these extra programs be in addition to the 15g?  I'm just trying to see what a total Ubuntu setup would take up.

I should state that I have all of my media/photos/documents on a separate media HDD, so as long as I can install & use truecrypt within ubuntu to access my media HDD that is encrypted with truecrypt, I will be fine.  Is this possible?  Truecrypt works on Ubuntu right?

With the Ubuntu distro labeling, so 13.10 means that version came out in October 2013 where as the new upcoming release of 14.04 will be April 2014 correct?

This 14.04 is supposed to be the new upgraded version that supports mobile & goes from your phone to a dock on your main computer & allows desktop mode? - This is truly what I'm looking & waiting for & if it only takes up 15-20g of space then I may just wait until it's out and get a good phone to load this up on & use the phone as the SSD I originally was thinking of.

Why do one of you guys say to 13.10 & the other 12.04?

Honestly I'm in no rush & may just wait for the 14.04 distro and just upgrade my Windows to an SSD, if 14.04 is in fact the new mobile OS.

---

### Post by coldraven on 2014-01-04
Why not just install 12.04 and put Windows in a Virtual Machine? That way you could use Ubuntu for all internet stuff and only let Windows do updates.
VirtualBox is free and easy to setup and use. [https://www.virtualbox.org/](https://www.virtualbox.org/)
Do as papibe suggests, root partition 25Gb, swap partition the same size as your memory and the rest for /home.

The version for phones is called Ubuntu Touch. I'm not sure when it is going to be a finished product but it is not the same as the 14.04 desktop version.
[https://en.wikipedia.org/wiki/Ubuntu_Touch](https://en.wikipedia.org/wiki/Ubuntu_Touch)

---

### Post by 3rdalbum on 2014-01-04
> **PsychedelicWonders said:**
> So Ubuntu OS is 15g, does this include all of the programs you've suggested such as Gimp, Darktable, Rythmbox etc?  Or would all of these extra programs be in addition to the 15g?  I'm just trying to see what a total Ubuntu setup would take up.

No, the base Ubuntu install is 3-4 gigs, including Rhythmbox, Firefox, Libreoffice, Totem Movie Player, and a few other small utilities. The extra programs mentioned might bring the size of the system up to 15 gigs if you installed them. Probably less than that, though. Twenty gigabytes should be more than enough.

> I should state that I have all of my media/photos/documents on a separate media HDD, so as long as I can install & use truecrypt within ubuntu to access my media HDD that is encrypted with truecrypt, I will be fine.  Is this possible?  Truecrypt works on Ubuntu right?

Although I've never used it, it appears that Truecrypt is available.

> With the Ubuntu distro labeling, so 13.10 means that version came out in October 2013 where as the new upcoming release of 14.04 will be April 2014 correct?

This 14.04 is supposed to be the new upgraded version that supports mobile & goes from your phone to a dock on your main computer & allows desktop mode? - This is truly what I'm looking & waiting for & if it only takes up 15-20g of space then I may just wait until it's out and get a good phone to load this up on & use the phone as the SSD I originally was thinking of.

14.04 will be out in April 2014, correct, but there are no phones capable of docking. Not even the first Ubuntu phones are likely to be dockable. Also, you forget that a phone CPU will be very slow to run the kinds of programs you want to run. Probably run out of RAM, too. Use your computer instead, you'll be much happier. 14.04 isn't "the phone version", it's just another version of Ubuntu that just happens to have certain Android phones as a supported platform.

> Why do one of you guys say to 13.10 & the other 12.04?

Some people advocate Long Term Support versions (like 12.04 and 14.04), whereas others advocate using the latest version of Ubuntu at all times (13.10). There are advantages and disadvantages to each approach. LTS releases can be used for up to five years before upgrading, and they are very predictable. Non-LTS releases are only supported for 9 months and if you upgrade you might find that the older bugs have been fixed and newer ones introduced. However, running the newest version gives you support for new hardware, newer software, and generally more features.

---

### Post by Bucky Ball on 2014-01-04
*Thread moved to **General Help**.*

I have never used a partition larger than 15Gb for Ubuntu, and now Xubuntu, but I keep my personal data on a separate partition. Run the OS on the SSD and keep your data elsewhere. That seems to be rule of thumb. If you're doing this, you should get Win and Ubuntu on a 64Gb SSD without issue.

---

