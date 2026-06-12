---
title: "Dual hdd's &amp; Partitioning"
date: 2007-01-18
forum: General Help
---

### Post by randiroo76073 on 2007-01-18
I'm acquiring 2 lrg hdd's[500gb, 750gb] & since I like multibooting, I have a question about /root & /home. Would it be good, performance wise, to put all my / on 1 hdd & my /home on the other, or just a null.  I just don't want a perfomance decrease.
TIAFAI

---

### Post by tommcd on 2007-01-18
There is no performance decrease by having /root and /home on the same disk. Since you have such huge hard drives I would set up the 1st as:
/root 15GB
/swap 2x RAM
/home what is left
If you want to dual boot with win XP, set up the ubuntu drive as master (if IDE) and winXP dive as slave like this (see the replies from "lha"):
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)
[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)
If you want the 2nd hard drive as storage for ubuntu see this:
[https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28hard%29%7C%28drive%29](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28hard%29%7C%28drive%29)

---

### Post by randiroo76073 on 2007-01-18
Thanks for reply Tommcd, I'm presently multibooted with Ubuntu Dapper, Edgy, Feisty, K & X ubuntu, Fedora, Freespire, Kanotix, Sidux, PC Linux, Slackware, Mephis, Mandriva, PC BSD, Arch, Berry, all with separate /root , /home partitions, DSL, Puppy & 98se.  Swap partition of 2gb[same as ram, swap very seldom used] Now you can see why I need larger hdd's, LOL!  Friend is upgrading to the new 1tb drives and selling me  his [less than 1yr old] drives at a deep discount[he can afford it].

---

### Post by indytim on 2007-01-18
So Randiroo, what distro / ops are you NOT booting too? :D   Impressive list that kinda makes my head swirl thinking of how you keep track of things between ops.

IndyTim

---

### Post by randiroo76073 on 2007-01-18
LOL! indytim, it gets confusing to me somtimes, I'll open a terminal and try to do something, end up getting msg: "command not found" then I'll just sit there trying to remember what the hell I'm supposed to type in.  It makes it doubly hard cause I just switched over from windoz 6 mos ago.  Ya, I know, I'm crazy!

---

### Post by tommcd on 2007-01-19
Randiroo,
now I fully understand why you started this thread! Could you please post your /etc/fstab? I have been interested in booting more than one distro (along with windows for gaming). I have been wondering about the virtues of seprate /home partitions for each distro, or just one big /data partiton for my files, and just have a /root partition for each distro.

---

### Post by randiroo76073 on 2007-01-19
This is my backup fstab, it changes with addition/deletion of distros.  Best advise is to backup your original 1st so you always have something to fall back on.  I always use a copy to fool with & when I'm happy replace original.  Keep your live cd handy to boot/repair from cause mistakes happen :)

# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>     <options>                          <dump>  <pass>
proc            /proc           proc      defaults                              0       0
/dev/hda1       /mnt/98me                 vfat       defaults,user,rw           0       0
/dev/hda5       /mnt/pc-linux-1r          ext3       defaults,user,rw           0       0
/dev/hda6       /mnt/pc-linux-2h          ext3       defaults,user,rw           0       0
/dev/hda7       /mnt/mephis-1r            ext3       defaults,user,rw           0       0
/dev/hda8       /mnt/mephis-2h            ext3       defaults,user,rw           0       0
/dev/hda9       /mnt/kubuntu-1r           ext3       defaults,user,rw           0       0
/dev/hda10      /mnt/kubuntu-2h           ext3       defaults,user,rw           0       0
/dev/hda11      /mnt/kanotix-1r           ext3       defaults,user,rw           0       0
/dev/hda12      /mnt/kanotix-2h           ext3       defaults,user,rw           0       0
/dev/hda15      /mnt/freespire            reiserfs   defaults,user,rw           0       0
/dev/hda16      /                         ext3       defaults,errors=remount-ro 0       1
/dev/hda17      /home                     ext3       defaults                   0       2
/dev/hda18      none                      swap       sw                         0       0
/dev/hdb2       /mnt/berry                ext3       defaults,user,rw           0       0
/dev/hdb3       /mnt/fedora-1r            ext3       defaults,user,rw           0       0
/dev/hdb5       /mnt/fedora-2h            ext3       defaults,user,rw           0       0

/dev/hdc        /media/cdrom0             udf,iso9660 user,exec,rw,noauto       0       0
/dev/hdd        /media/cdrom1             udf,iso9660 user,exec,rw,noauto       0       0
/dev/fd0        /media/floppy             auto rw,noauto,user,sync              0       0


Here are 2 readme's that I used[lost links so am enclosing txt]

PS:  I used the /mnt folder cause I didn't want them generally available, you can use /media if you want on desktop or simlink from /mnt

---

### Post by CowzRule on 2007-01-19
Do you use 1 swap partition for all you DE's?

I can only imagine what your grub menu looks like :-D

---

### Post by anaconda on 2007-01-19
> **tommcd said:**
> Since you have such huge hard drives I would set up the 1st as:
/root 15GB
/swap 2x RAM
/home what is left

With as large a disk than yours there is no point in making only 15GB /root partition. Because 15GB is quite small and you might easily run out of space.. (almost all programs you install and apt-cache etc. will go to /root)
I would make it atleast 40GB if I had enough room in my disk...

---

### Post by randiroo76073 on 2007-01-19
CowzRule, Yes, 1 swap partition is all you need, if you have plenty of ram I would make it same size as ram, otherwise 1 1/2 - 2 times is general rule.

LOL! Anaconda, so I found out, due to size of current hdd I made /root=5gb, /home=10gb & ran out of space fast.  I'm going to have to think out my partitions more carefully this time as I have to leave room for expansion too.  One of the nice things with a linux partitioner is that you can leave space between your partitions :)

---

### Post by tommcd on 2007-01-20
> **anaconda said:**
> With as large a disk than yours there is no point in making only 15GB /root partition. Because 15GB is quite small and you might easily run out of space.. (almost all programs you install and apt-cache etc. will go to /root)
I would make it atleast 40GB if I had enough room in my disk...

Well, I suppose it depends on how much software you install. My /root partition is 12GB. df -h shows I have used about 3.8 GB so far. Of that used space 1.5 GB is DOOM3. So unless I start installing a bunch of games I will likely never fill my 12 GB root partition. However, it is always better to have more than not enough, so if you got a huge drive then go for it. 40 GB sounds like a bit of overkill to me though. My windows partition is 40 GB, and with FEAR, the Extraction Point expansion pack, Half-Life2, and Call of Duty2, it is still only about 60% full.
On ubuntu many games can easily run from your home folder. I run Nexuiz and Alien Arena from my home folder and they work just fine.

---

### Post by randiroo76073 on 2007-01-20
Tommcd, I agree, /root = 40gb is quite large.  I am thinking that /root should be in the 10-15gb range, mainly because some of the distros are DVD installs.  I think /home, except for Ubuntu[40gb], should be 20gb.  Most users won't run into this problem cause they're not crazy like me, LOL!  Here's a little tip, if you plan on multibooting, have a backup copy of fstab & menu.lst, do all changes on them and when your satisfied copy them to appropriate destination.  Can't tell you how many times I rewrote menu.lst to get it right, some of distros are real fussy about their boot entries being just so.  Here's some references that I used:
[http://ubuntu-tutorials.com](http://ubuntu-tutorials.com)
[http://www.ubuntugeek.com](http://www.ubuntugeek.com)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.debianhelp.co.uk/tools.htm](http://www.debianhelp.co.uk/tools.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
HTH

---

### Post by tommcd on 2007-01-21
Randiroo,
Thanks for the info. I am familiar with the sites you linked to, and I always have a current super grub disk handy. I also have backed up fstab and menu.lst (I learned to be totally anal about computers from my experience using windows).
So, if I understand your fstab correctly, then:
/mnt/distro-1r ext3 ... is the root for each distro
/mnt/distro-2h ext3 ... is the home for each distro
...is that correct?
And I suppose your personal data is on 
/dev/hda17 /home ext3 defaults 0 2
Or do you have data on each of the /home partitions for each distro?
And when you reinstall a distro, do you just run <sudo update-grub> or do you just edit grub by hand?

---

### Post by randiroo76073 on 2007-01-21
LOL!  I hear the windoz anal part.  Ya, r=root, h=home, I try to be logical setting things up but it still gets a little wacky :)  Mostly personal data is on /dev/hda17, with other h's only getting what they need to function[bare miniumum].  The one thing that didn't show on my fstab is my USB drive, it's auto mount ala Ubuntu[most of other distros automnt it too], it's strictly to hold backups and an image of Ubuntu[ms anal retentive]  I edit by hand cause I found that auto doesn't seem to get it right all the time & I keep a copy[ms strikes again] of each distro add[named xxdistro menu.lst, xxdistro fstab updt].  I think I personally keep the cd/dvd mfgs in business cause before any major changes I burn a image of whatever distro I'm working on, mainly I use dvd-rw for incrementals, must be close to arse-deep by now.  Hope you have as much fun multibooting as I do, it's a learning experience.

PS:  Nice thing about linux is, short of a hdd crash, you can always recover to a working state fairly quickly :D

---

