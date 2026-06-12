---
title: "Re-partitioning trouble"
date: 2007-05-14
forum: General Help
---

### Post by Tucci on 2007-05-14
I'm a very new Ubuntu user who just installed on a laptop with XP. When installing Ubuntu, I tried to partition so I could dual boot between XP and Ubuntu. That seemed to work fine... but

1: I haven't been able to successfully enter XP (which isn't really a problem, see below).
2: I have a 120 gig hard drive and I guess Ubuntu is only assigned 30-some gigs of that. I don't have enough room to move all of my stuff from my old computer (an aaaaaaancient iMac) to Ubuntu.
3: I don't really care about keeping XP anymore, so I'd just as soon delete it entirely so all 120 gigs goes to Ubuntu.
4: I'm pretty sure I burned gparted to a livedisk, and so I should be able to restart using that and then changing the partitioning will be easy.
    4a: I'm hazy on, what, exactly, a livedisk is. I was under the impression that it's an .iso file, which means it can be booted from directly rather than loading the operating system. So, if I downloaded the .iso file and burned it to a disk normally, I should be able to boot from it, right? (or is burning an .iso file different somehow?) In any case, I can't seem to boot from the CD.
     4b: To clarify, I'm a long-time Mac user, and to boot from a CD on a Mac, you hold down the C key. Searching indicated to me that I would either not need to hold down any key and it will give me an option on starting, or that I need to hold down the 'del' key. Not doing anything doesn't work, and holding down the 'del' key makes a really loud beeping noise like my laptop's about to self-destruct.

Can someone help? What's the easiest way to just delete a partition or two entirely?

---

### Post by GS2 on 2007-05-14
I use Knoppix live cd with gparted - never had any problems with re-partitioning.

you need to make a "CD Image" from the .iso - not a data cd (you probably know this but everyone has done it)

The cd will boot after restart if your BIOS settings are set to boot from cd first - or your bios has a hot key (my toshiba laptop uses the "C" key for cdrom booting

---

### Post by Tucci on 2007-05-14
Thanks, that answers my question, I think. I did burn a data cd - how do I make a CD image instead? I guess I thought the .iso format meant it was a CDImage... (Wikipedia seems to imply that I'll need a special program, so I'll go find one now and try that)

---

### Post by GS2 on 2007-05-14
You have ubuntu already - you can install gnomebaker (from Synaptic - not sure which repository might be in the multi-verse or universe - do a search for it) 

Gnomebaker is very easy to use. Ubuntu also has a 'built in' burning package - on my Ubuntu box comes up automatically when you put a blank cd in.

On Kubuntu at the moment, if I right click over the .iso file, it shows an option to use the burning suite installed - Ubuntu should have something similar :)

---

### Post by Tucci on 2007-05-14
I tried using Graveman, which looked like it was going to work, but then gave an extremely unhelpful error message ("Operation Failed"), apparently at the Fifo stage, whatever that is.

---

### Post by Tucci on 2007-05-14
Weird... I tried Gnomebaker, and it too appeared to work but then said it failed. But after ejecting and re-inserting that disk, the burn appears to have took (the disk is called gparted), so I'm going to try it now.

(putting a blank CD prompts a choice of either a data cd or audio cd, btw)

---

### Post by GS2 on 2007-05-14
Did you check the md5sum of the .iso to ensure it is not corrupted ?

example:
.iso name = image.iso
location = /home/user/

```
cd /home/user
md5sum image.iso
```

This should give you a series of letters and numbers, check these against the md5 given on the download page (or a link somewhere on the download page) for the md5 of your  .iso download - if they match the file is not corrupted - if it does not match the file is corrupted - download it again.

Never used that package, so not much help there - check the documentation for it. If not included in one of the menus will be installed in 
/usr/share/doc/nameofpackage.

To find it more efficiently open terminal type:
```
sudo updatedb
locate nameofpackage
```
This will show the path to all matches
May be worth 'piping' the command:
```
locate nameofpackage | more
```
press return to scroll down through the list press CTRL+C (that is cnrtl and C together) to cancel the search.
Or install gnomebaker :)

---

### Post by GS2 on 2007-05-14
Just seen the post - glad it worked :)

---

### Post by Tucci on 2007-05-14
Aargh! It definitely did something, but on rebooting it took me straight into a command line interface, so I'm re-downloading the iso image, hoping that was maybe corrupted.

The kind of CD I use shouldn't matter, right? I'm using a cheap Memorex CD-R...

---

### Post by Tucci on 2007-05-14
Okay, I'm pretty sure I burned a CDimage correctly, but it still won't boot from the disk...

---

### Post by GS2 on 2007-05-15
Step 1 check Bios boot sequence (cd has to be first).

Step 2 burn image again but at the slowest speed possible (higher speed increases the chances of errors)

cd should not matter - I use cheap ones too. Ensure they are being 'fixated' - Gnomebaker should be do this automatically. When Gnomebaker is burning expand the window so you can see the textual output (the little arrow bottom left of the window when burning I think it is labelled "Details") check for any errors

---

### Post by Tucci on 2007-05-15
Thanks, I'll try a lower speed next time I have problems (I do remember Gnomebaker "fixating", which is I think where the error message came up)... I actually decided to just backup the handful of files I wanted to keep, and am reinstalling Ubuntu entirely, deleting the XP partition and all that.

Thanks guys!

---

