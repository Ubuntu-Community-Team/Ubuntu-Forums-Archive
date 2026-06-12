---
title: "Need to &quot;Repair&quot; 7.10 installation. Can't start."
date: 2008-02-19
forum: General Help
---

### Post by Dangerous2505 on 2008-02-19
Hi everyone,

First a little info before getting to the question.

I have installed Ubuntu 7.10 on my AMD Athlon XP 2500 desktop system,
(1.5 GB ram, nVideo G-force 6200, with 2 internal HD's), to dual boot.  I have
W-XP installed on the first HD, and Ubunto installed on the second.
All was working OK, (still got issues with sound and local network, but that's
for another thread), and had installed several programs I wanted to use.

When I first installed, I set up a small (20GB) ext3 partitions as "/", and a 4GB
swap partition. The rest of the drive was set up as a Fat32 partition to use for
moving and storing things between the two OS's. After playing around with
things for a day or two, I found that I could access and move things directly to
and from the "NTFS" directories on my other drive, so I decided to get rid of the
"Fat32 partition and use the entire second drive for "ext3 and swap.

Now the problem;

First, I tried to use gparted to delete the fat32 and resize the ext3 partitions,
but it wouldn't let me move the swap to the end to make room to enlarge
the ext3.  OK, no sweet.  I'll just backup everything and then do a clean install
and change the partitions that way.  I made the backup using tar
as per the instructions in a "How-To" thread here. (Don't have the link to
thread right now.)  Anyway, with a backup made, I booted from the live CD and
installed again setting the drive up the way I wanted it, rebooted
and let it install the upgrades.  So far so good. After another reboot, I 
restored everything from the .tzg backup, logged out and bank in.  At this point
everything was like it should be, all the stuff I had was there and working.
Then I restarted and booted to XP just to check that I hadn't messed that up.
Worked just fine.  Then, restarted and chose Ubuntu from the boot list.
It got to the splash screen with the progress bar on it and froze.  Now I 
can't start Ubuntu.

What I want to know, is can I use the live CD to repair Ubuntu without
reformating and losing everything that I have installed?

Any help would be appreciated.  If you need any more info, then tell me what
you need and where to find it and I'll try to get it for you.

Thanks in advance for any help you can give.

Dangerous Dan

---

### Post by GuDoN on 2008-02-20
I would like to double up on this guy's post, I have had a few glitches and couldn't find any repair stuff, neither from the boot cd.


how can one repair sensitive files, that have gone wrong?

not taking over the post, doubling the query :)

---

