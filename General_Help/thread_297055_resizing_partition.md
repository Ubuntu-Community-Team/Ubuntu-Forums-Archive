---
title: "resizing partition"
date: 2006-11-10
forum: General Help
---

### Post by howlingmadhowie on 2006-11-10
hi everybody :)

in installed 6.10 on my new laptop and without thinking about it told it to take the whole harddrive (without making a logical volume). now i'd like to create an encrypted partition (just to find out how it works) and would like some help as to how to resize the current partition.

the way i understand it, i can boot using the live cd and change the size of the ext3 filesystem and then use any partition software (fdisk, cfdisk, whatever is on the live cd) to resize the partition, making sure it isn't smaller than the size i entered for the ext3 filesystem. will this work?

hoping for help :)

howie

---

### Post by ciscosurfer on 2006-11-10
That will work, but it can be tricky and dangerous if you haven't done it before.

My suggestion: download and burn the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), boot with it, and resize your partition that way.

---

### Post by Average Joe on 2006-11-10
> **ciscosurfer said:**
> My suggestion: download and burn the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), boot with it, and resize your partition that way.

Why? The Ubuntu Live/Desktop CD has Gparted on it. You might as well use the Live cd to boot, and run Gparted to resize your partition and to create another one. I have done that many times myself. Works fine.

---

### Post by ciscosurfer on 2006-11-10
It's a matter of preference.  You'll notice I said, "My suggestion" not "It's required you do it this way".

---

### Post by Average Joe on 2006-11-11
> **ciscosurfer said:**
> It's a matter of preference.  You'll notice I said, "My suggestion" not "It's required you do it this way".

I am sorry, I didn't mean to offend you. I was just wondering why you would prefer to download and burn a live CD in order run an application that you already have (assuming you have the Ubuntu Live/Desktop CD).

Anyway, it is always good to know more solutions to solve a problem, everyone can then decide for himself what solution he wants to use. I was not implying either that people are required to use my solution.

---

### Post by ciscosurfer on 2006-11-11
No offense was taken.  Sometimes writing on the forums (or even email or chat) can get confusing and words and thoughts can be misconstrued.

I was in no way offended.  In fact, I enjoy the dialog even if I don't always agree with what is being said (I happen to agree with you though).

The reason I brought up using the live GParted CD was because I got the best results from it -- for some reason (and I really don't have a clue why) the gparted that came with my live CD was acting up -- and ubiquity was acting funny.  So, I decided on using a separate disc.

---

### Post by Average Joe on 2006-11-13
Ok. That sounds like a good reason to use a separate GParted Live CD. I haven't experienced any problems with GParted that comes with the Ubuntu Live CD. But I haven't done too many complaticed things with it either.

Good to know that the GParted Live CD could be useful whenever I get into serious trouble.

---

### Post by smoker on 2006-11-13
hi, i had trouble with the ubuntu gparted before, so tend to not trust it for partition work (probably paranoia on my part), but i have never had any probs with my separate burnt gparted disk, plus it loads in a minute.

i would like to add tho, please ensure that all your essential data is backed up just in case anything does go wrong, rare tho it may be :-)

---

### Post by cotcot on 2006-11-13
I also avoid using Gparted from the ubuntu liveCD. I have seen enough black exclamation marks on yellow triangles. I only rely on either the GParted LiveCD or just simply "parted" in terminal. Parted has a good manual.

---

### Post by tedrogers on 2006-11-16
Hi, 

I have a similar resizing / partitioning related query, because I am trying to do a backup using partimage and I have to resize my exisitng partition to make a new one for the backup to go onto.

When I tried using qtparted from the 'linux resxue CD' to resize the /hda1 partition, the only partition where the 'resize' option wasn't ghosted out was the swap?

It wouldn't let me resize /hda1 at all, I guess because it was mounted or something. So I tried to unmount (or umount) /hda1 in the rescue CD terminal, and it reported that /hda1 wasn't even mounted at all??? :confused: 

Any ideas what's going on here?

Thanks.

---

