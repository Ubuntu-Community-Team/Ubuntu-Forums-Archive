---
title: "disk is full error on Xubuntu 16"
date: 2023-02-14
forum: General Help
---

### Post by StrobeWylan on 2023-02-14
Hello Friends.

I just got a used Lenovo  ThinkCentre with Windows 10. I decided to try doing a dual boot, which I never tried before. I figured it may come in handy to have windows if if need it. I installed Xubuntu 14.* to start and used Grsync to add things from a previous desktop with X14 on it that I wanted to have. Then I upgraded to Xubuntu 16.* and planned to keep upgrading until I caught up with the rest of the universe. Everything was working fine (I was a bit surprised) but after a few days I started getting 'not enough space on disk' errors. I used Gparted to see what I had and see that there are two ext4 partitions. The one that is 9.77 Gib is indeed almost full. The other has 207 Gib available . I'm not sure why the install created 2 of them and is using the smaller one for storage. 

Is it possible to use Gparted to merge the two partitions (everything is backed up on an external hard drive)? Or perhaps you may have another idea. I'm not a super geek but have some intermediate skills.

Thanks in advance.

---

### Post by guiverc on 2023-02-14
Xubuntu is a *desktop* system and is thus *year.month* in format, as Ubuntu has *reserved* for the *year* format products (eg. Ubuntu Core 16) for *snap* only systems, where Xfce isn't available as a *snap* package so won't run on 16; it only ran on 16.04 & 16.10

Xubuntu 16.04 LTS was released in 2016-April (*thus the 16.04*), with 3 years of support, ie. read [https://xubuntu.org/news/xubuntu-16-04-release/](https://xubuntu.org/news/xubuntu-16-04-release/) thus reaching its EOL in 2019-April.

> The Xubuntu team is pleased to announce the immediate release of Xubuntu  16.04. Xubuntu 16.04 is an LTS (Long-Term Support) release and will be  supported for 3 years.

The oldest currently supported Xubuntu is Xubuntu 20.04 LTS, and given you're so far behind, I'd just re-install a *supported* system and ensure you have allocated a larger partition. 

Ubuntu 17.10 Desktop and later releases have recommended a **minimum** disk allocation of 25GB, and whilst that's a different desktop to Xubuntu - it's a reasonable guide. Your disk size is too small in my opinion, unless you're going to *apply* upgrades very often, never let upgrades accumulate etc*. *Your Xubuntu is so old it's still using *deprecated* GTK2 which is *smaller *than the more modern GTK3 so expect it to grow (*ability to handle HiDef screens etc gets added thus libraries/toolkits grow in size*).

FYI:   A default install of Xubuntu creates only a single partition (*plus an ESP on recent releases*), it doesn't split /home and / unless it was told to; though your install was so long ago maybe it's changed.  I suspect your two partitions are due to options selected at install time (*though it's been too long since I installed a release that old of Xubuntu*).

Due to your system being so *ancient*, I'd start again with a *supported *release of Xubuntu.  Also if it says you're using 16 (*which wasn't supported; 16.04 & 16.10 only were supported*), you may have other issues too.  You have your data backed up, I'd suggest restoring that post-re-install.

(You can non-destructively re-install to allow you to very quickly re-install a *supported* system and not lose data, but given your small your / partition is, I'd not recommend that but starting again given how long your system has been unsupported).

---

### Post by grahammechanical on 2023-02-14
GParted will not let us merge partitions. It will let us shrink a partition to create unallocated space and then expand a partition into the unallocated space. In this way one partition becomes smaller and another partition becomes larger. You will find it difficult to do that because of the layout of the partitions. This is what I suggest.

We use GParted from a live session. 

1) Shrink sda7 from the left to create about 25 -30 GB of unallocated space between sda7 and sda6. 
2) Shutdown the live session and see if you can load Xubuntu.
3) Load the live session and GParted
4) Move sda6 to the right into the unallocated space. This will put the unallocated space between sda6 and sda5.
5) Expand sda5 to the right into the unallocated space.

Now the OS should have 34 - 39 GB of space.

By the way, you will need to do this even if you decide to install a newer version of Xubuntu. If you decide to shrink the Windows partition then remember to use Windows tools to defrag Windows and shrink the Windows partition. 

If you do that with your present install of Xubuntu you should be able to continue online upgrading until you get to the version you want. Multiple online upgrades is an educational experience.

Regards

---

### Post by StrobeWylan on 2023-02-14
I'm probably going to do a clean install then. Should I use Gparted to wipe out the present mess? I still want to retain the Windows 10 partitions. Should I create one Ext4 partition on the remaining disk space? Or what?

I wrote this post without seeing  grahammechanical's post. I may try that first. Thanks

---

### Post by StrobeWylan on 2023-02-15
I tried to do what grahammechanical said but Gparted kept freezing up when I tried to resize/move anything. Messed with it for over an hour and decided to do a clean install of X20 as guiverc suggested. I was able to delete all the non-windoz partitions and make the area a single Ext4. Then I did the install and it is working fine today. 

Since it is a related issue I want to bring up another problem on this thread. The box I'm replacing has some software that I cannot replace and do use on some occasions. A few days ago I decided to start doing a series of OS updates to gradually bring it up to date. I clicked on the button to update from X14 to X16 and it started to work. I went out of the room for a minute and came back to a blue screen (not the BSOD thankfully). It was a blank standard desktop without the picture I had on it before.  Nothing that I did changed anything. There was no panel or anything. After letting it alone for a long time I shut it down by pressing the power button. When I start it up it loads Firefox (it had been set to load on startup). In fact I have been using this box to put my entries in this thread. If I minimize Firefox I cannot get it back. I can't get a terminal with any keys. Right clicking on desktop does nothing.  I can use Firefox to access Email like before but cannot open Thunderbird (or anything else for that matter). I use the power button as the only way to shut down.

Ideas?

---

