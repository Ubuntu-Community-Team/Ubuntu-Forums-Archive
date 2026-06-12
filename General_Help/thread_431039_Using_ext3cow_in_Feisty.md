---
title: "Using ext3cow in Feisty"
date: 2007-05-02
forum: General Help
---

### Post by SeTsU on 2007-05-02
Hi there!

I was looking forward to make a clean install of my Ubuntu (dist-upgrade from Edgy didn't go too well, messed up some user configs in GNOME) and I was considering to use ext3cow ([http://www.ext3cow.com]("http://www.ext3cow.com")) on some of the partitions (possibly /, but at least the home partition). For those who don't know it, it's a versioning filesystem that allows "time-travel" (i.e. taking snapshots of your filesystem to recover older versions without losing your most recent documents and vice-versa. Think of it as a sort of CVS repository for your whole filesystem).

Disk space won't be a problem, since I have 2 disks making a grand total of 300 GB, most of which aren't really being used anytime soon.

Anyone tried and succeeded with Feisty?

If so, any special hints/tips? If not, what happened wrong?

I was also wondering if it would be worth the hassle to use [this file manager]("http://www.sandeepranade.com/html/ComputerScience/time-travelling-file-manager.html") with it.

Again, I'd appreciate your opinion. :)

Thanks!

---

### Post by crimesaucer on 2007-05-02
I saw that on digg today and didn't know about it until today. It seems interesting.

---

### Post by SeTsU on 2007-05-02
Yes, it does seem interesting. I actually checked this out on Slashdot today and it let me anxious for the whole day (especially after seeing Apple's "time-travel" in Leopard a few months ago).

Well I don't really have much to lose, since I'll be backing up my data anyway (going to re-organize the whole disks), so I guess I'll give it a try this weekend.

I'll drop my results around when I do so. :)

Any feedback from someone who might've tried it first would still be great, though. ;)

---

### Post by frenkel on 2007-05-04
I was also considering using it for my root partition. My home partition is to valuable to test it on (although I have backups). I'm now downloading the ubuntu kernel source, will report back if it works. (Maybe even post the debs for you guys).

---

### Post by saracen on 2007-05-05
has anyone set this up?

---

### Post by nirudha on 2007-05-05
Since it's a kernel patch I assume it won't be possible to distribute it in DEB form. But it would be nice to have a how-to from the more experianced users.

Could anyone tell me the pro's and con's compared to using LVM to get the same effect?

---

### Post by SeTsU on 2007-06-19
Well, I haven't got myself the time to do the change just yet (exams, college projects, and pretty much everything you could throw up at me) but I've recently got the time to try and put it on a Gentoo installation under VMware.

And... surprise, surprise! I didn't manage to get it to work.

I actually managed to create an ext3cow partition and all, thing is, when I booted the VM, fsck would say the partition wasn't a valid ext2/3 partition, so I couldn't boot (couldn't figure out why, though, since the ext3cow partition wasn't the / one). Now that I think of it, I might've just removed it from fstab to get Gentoo to boot.

I'm not really a *NIX expert, so I **may** have screwed up somewhere else, but I'm pretty sure I didn't.

Anyway, as far as anyone is concerned, the installation process isn't trivial (you end up replacing the ext2/3 tools) and it should not be used in a production environment.

I may give it another go somewhere next week, but for now I think [this]("http://ubuntuforums.org/showthread.php?t=474973") is getting interesting.

---

### Post by SeTsU on 2007-06-19
Ok, so I actually tried again today. Couldn't hold it. :P

And yeah, it was my screw up. :P

I managed to get it working on that Gentoo kernel. It was 2.6.20-10, I guess, so as long as you use a 2.6.20-* kernel you shouldn't have much problemas.

Only thing is that you can't remove snapshotted files at the moment. For example you take a snapshot and then delete the file. The snapshotted version stays there, and as far as I know, there's no way to take it back.

If people are interested, I can make a how-to based on my experience someday.

---

