---
title: "Grub is really slow after Windows virus nuked MBR"
date: 2007-04-12
forum: General Help
---

### Post by aldenhg on 2007-04-12
Hi all - 
I recently had an unfortunate encounter with a virus on the Windows side of my disk that ended up nuking my MBR. Since I dual boot (hda has 3 partitions, 1 is ntfs, 2 is ext2 and 3 is swap) and had a LiveCD on my desk, I just popped it in and ran 'setup (hd0,1)' in the grub console. 
Now it will boot into either OS, but it takes 2-3 minutes for the grub menu to come up when it used to take less then a second. 
I'm not all that well versed in bootloaders, so if there are any config files that would help in diagnosing my problem, please tell me. This isn't that huge a problem, but I would like to have my computer start up in less then 4 minutes.
Thanks in advance.
Alden

---

### Post by bernied on 2007-04-12
> setup (hd0,1) will install the grub MBR on the first part of the second partition of the first drive. Are you sure you did not
```
root (hd0,1)
setup (hd0)
```instead? That would install the grub MBR on the first drive, to point to the second partition of the first drive.

It's really weird to me that grub would take long to load, are you sure the delay is not in the bios, rather than grub?

Does a live-cd boot quickly?

Another test you could try is to reinstall the windows mbr and see how quick windows boots. If that's slow as well, then it's not grub that's the problem.

You would of course have to reinstall the grub mbr, but you already know how to do that.

The only config file is /boot/grub/menu.lst 
There is no log for grub, this would involve disk access that grub just doesn't do.

---

### Post by aldenhg on 2007-04-12
I've tried bot (setup (hd0,1) and your suggestion) and the former faults out and asks me to clrify while the later just takes a long time. I've tested it aginst a boot floppy and a live cd, both of which are snappy and virtually witout delay, putting the blame squarely on GRUB. 
For the sake of clarification, GRUB hangs immidiately after POST, giving me a blinking cursor for a while, then it loads stage 1 for a while, followed by stage 1.5 and then I finally get my menu.list. After making a choice there is no delay at all.
Should I just get rid of GRUB all together and then reinstall it? If so, how would I go about that?

---

### Post by guinra on 2007-04-12
I'm not sure if Grub is probing hardware or if you might have a hard disk problem.  It could simply be a physical / logical geometry mismatch, but while loading if the hard drive light is going and you hear any strange noises from the HD during that time, you might have HD problems.

If you boot off of the Ubuntu Dapper/Edgy CD can you access the HD without problems?

---

### Post by aldenhg on 2007-04-12
The hard drive is fine. I ran DFT on it and it passed with flying colors and I can acess every cylinder of every sector no problem. Every partition is mountable and has been checked thoroughly for errors. The drive itself is running quiet as a mouse (the mamillian type, not the x/y pointing device).
If it is probing hardware is there a way to just tell it what hardware I have so it won't try any more?
Thanks for the quick replies, by the way.

---

### Post by bernied on 2007-04-13
So this really is weird.
To clarify, grub used to work fine, right?
Then, something went wrong with a virus in windows, which hosed your mbr.
Then you reinstalled the grub MBR from 'a live CD'. 
Now grub loads with time enough to make a coffee.
Which live-CD did you reinstall it from?

Have you tried reinstalling grub from the Ubuntu live-CD that you originally installed Ubuntu from? Or from a different live-cd? By reinstall, I mean just do the root and setup commands from a grub console like before.

I think that not all grubs are the same. From the website and the fact that no new version has been released for years, I think that the devs are not up to much, but every distro messes with grub, so maybe different distros have ended up with different versions of grub. So maybe this particular version of grub messes with your particular hardware.

I don't think there is any way of telling grub what hardware to look for, without messing with the source code. It was designed to just work, and it usually does.

And I still suggest that you post your menu.lst file here, just in case there is something weird there.

---

### Post by bernied on 2007-04-13
Actually I think you might need to do more than just the 'root and setup commands'. I think you need to copy all the files in the /boot/grub/ directory from a known good install, and then run those commands in a grub console.

You *could* try reinstalling using apt-get:
```
sudo apt-get remove grub
sudo apt-get install grub
```
But bail out if apt-get wants to remove anything else.
That might reinstate those files.

EDIT: But you might still need to do the 'root and setup commands' after you've done the apt-get reinstall.

---

### Post by aldenhg on 2007-04-13
The live cd I used was Knoppix 5.1.
I just tried reinstalling and re-setuping grub and now it seems like it might be a bit faster, but it could just be that I'm getting used to the delay. I'm starting to wonder if it's not a hardware issue, but the fact that everything else on the system runs at normal speed kind of takes the blame of hardware, unless the actual sectors on the disk are curropt in some - but I've never heard of that happening.
Does anyone want to post their working /boot/grub folder for me to tansplant? Will I have to edit any config files (except for menu.list, of course)?
My menu.lst is attatched.

---

### Post by bernied on 2007-04-13
[These files](http://tech-turtle.co.uk/grubfiles/) are from my kubuntu desktop install.
You don't have to edit anything.

You should maybe take a copy of the whole directory before you change anything:
```
sudo cp -rv /boot/grub /boot/grub.old
```
Then copy the files into /boot/grub/
You will need root access.

---

### Post by aldenhg on 2007-04-14
Thanks for the files, bernied, but it didn't help. 
I wish grub had a log file. :^/

---

### Post by bernied on 2007-04-14
I'm sorry, I'm our of ideas.
Someone must know what this is.
Anyone?

---

### Post by aldenhg on 2007-04-17
Well, I fixed it. Though it doesn't make much sense, the whole thing got better when I put a second drive on the primary IDE channel. POST is faster, GRUB is faster and Ubuntu is just as fast as always. CAn anyone explain this to me? What's the geography of your primary channel, bernied? I'm still using th grub files you posted, so I figur if you've got two drives on your primarry channel it might explain why I'm up to speed again, but it doesn't account for the initial slowdown. C'est la vie. I'm not going to complain as everything is back to normal.
Thanks for all the help, guys!

---

### Post by bernied on 2007-04-17
I have two IDE hard-drives. I think I also have two IDE optical devices (one DVD player, one DVD/RW combo) - I know I have the devices, just not sure whether they are IDE.

I'm almost certain that the two hard-drives are on the same cable because I read that that was a good idea. I don't about channels though.

I had always thought that those grub files were the same for everyone (with the same version of grub), with only the pointer to the root location (grub stages 1.5 and 2) changing between installs. I'm still guessing that your problem was to do with the hardware configuration, not the grub software. Or, as a compromise, the interaction between your particular configuration and grub. So grub took ages working out what to do with you disk setup.

But I'm open to further education. Anyone else know what went on here?

---

### Post by Pox on 2007-04-26
Sorry to revive a post (though it's not THAT old I guess), but I'm having this exact problem - don't think anything hit my windows, but grub is taking 3 minutes to appear.  If anyone has any more ideas that'd be helpful because I'm pretty sure I've tried everything but kicking the box, and nothing's worked so far.

---

### Post by Pox on 2007-04-26
NVM, fixed it.  If anyone was wondering, I had a blank CDR in the drive and GRUB must have been interrogating the lack of a filesystem for 2 minutes. xD

---

