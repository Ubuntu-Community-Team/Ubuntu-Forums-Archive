---
title: "Run Live CD"
date: 2008-02-03
forum: General Help
---

### Post by joeynosek on 2008-02-03
[COLOR="Black"]I burned a CD of a Dapper Drake desktop version.  To run it (not install it) on my win xp pro machine. Do I have to change the bios settings to boot from a cd or is there an easier way to do this?  Is it wise to make a backup of my machine as is by creating a recovery point with windows or should I go as far as to clone my hard drive? As a total beginner in Linux, meaning I've _never_ used it before, I only want to roam around and see by making mistakes how this OS works. But I definitely don't want to screw up my win xp setup until I know what I'm doing. Is running the disk I made foolproof in this way?[/COLOR]Can somebody answer all these questions?

---

### Post by jaytek13 on 2008-02-03
There isn't really a way that you could mess up windows just using the live cd. There is a tool on it called gparted, which is a partition editor, and you could mess it up that way, but there wouldn't be any reason to use it just for testing the livecd out. 

Other than that there's no reason to take any type of precaution like backing everything up. But, the livecd probably won't teach you what you want. It has sort of limited functionality as far as actually being able to play around. It's really just to test it out, get a feel for the applications and the environment and whatnot. You can browse the internet, play some games, chat... but that's really about it. 

And you'd have to have the boot from cd option enabled in the bios, yes. It doesn't have to be the first option though, so as long as you already have the option checked there's no reason to go fiddling with the bios.

---

### Post by orange2k on 2008-02-03
You don`t have to be afraid of running the LiveCD...

But you WILL have to make changes in the BIOS to change the boot-device priority.
This procedure is easy and doesnt make any changes to your existing OS - it only enables you to boot from CDROM if its bootable.

---

### Post by joeynosek on 2008-02-03
Thanks very much you guys!  I'll see if the BIOS is set up to have the option to boot from a CD if I want to.  I ultimately want to set up a Linux server (file/print/PDC/web/FTP) so it sounds like I won't be able to learn about that sort of thing by using the live CD.  Would that be true?

---

### Post by jaytek13 on 2008-02-03
Not really. The livecd runs off of the RAM, so it's not persistent. Every time you would restart your computer everything you did on the livecd would be lost. You can play around a little but, but definitely not with getting a server set up.

---

### Post by joeynosek on 2008-02-03
I think that will be OK.  I want to learn how to work with the functions with the goal to learn how to set the server up when I think I've got it.  Right now, I don't have anything! So if I get something too far gone when working within the live cd, I can just shut the computer off, right?

---

### Post by jaytek13 on 2008-02-03
> **joeynosek said:**
> I think that will be OK.  I want to learn how to work with the functions with the goal to learn how to set the server up when I think I've got it.  Right now, I don't have anything! So if I get something too far gone when working within the live cd, I can just shut the computer off, right?

Yes, but I don't believe you would be able to do what you want to do, simply because setting up a server requires downloading and installing quite a few applications that aren't included with the livecd, and I don't think it's possible to install software if you don't have the OS installed.

---

### Post by joeynosek on 2008-02-03
I do have my hard drive partitioned with win xp pro on the C drive and the other as the D with nothing on it but formatted in NTFS.  How would I go about installing Linux on that D drive?  Wouldn't that give me a dual boot option which I could then customize to create my server?

---

### Post by jaytek13 on 2008-02-03
When the livecd loads up there is an option to install it. It would give you several options as far as where it would install itself. It could either resize the windows partition on the C drive and make room for itself, or you could have it take up the entire D drive, or you could specify how much room you would want it to take up on the D drive. It's fairly self explanatory in the install.

---

### Post by joeynosek on 2008-02-03
I will install the cd on my d drive and let it take up the whole partition which is now 10 gigs; but should i take up less?  I also have cd's of gutsy in server and desktop forms.  What is the best version of ubuntu to use for my purposes?

---

