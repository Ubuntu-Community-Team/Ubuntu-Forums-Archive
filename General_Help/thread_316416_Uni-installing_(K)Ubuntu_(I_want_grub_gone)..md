---
title: "Uni-installing (K)Ubuntu (I want grub gone)."
date: 2006-12-10
forum: General Help
---

### Post by o0o_sainted_o0o on 2006-12-10
Hey all, 

I installed Kubuntu and am having to many problems and conflicts (E.G. grub errors). Anyways, I would like to uni-install kubuntu along with everything it's related to (such as grub) right off my system. See, I am running on low disk space on C: (Windows), when I attempt to use partition magic to allocate un-allocated space, I end up with a non-hard drive booting machine - it sends my system wacko in addition to screwing with my bios settings. 

Anyways, how do I wipe Kubuntu and grub off the partitions without recieving grub messages and ending up with a non-hard drive booting machine? All I want is a system with Windows XP, just how it was before installing Kubuntu.

---

### Post by igknighted on 2006-12-10
You need to use the windows CD to restore the windows bootloader, I've never done it, but if you search the forums you will find detailed instructions.  I'm not sure it can be done without the Windows disc, so you will need that.

---

### Post by o0o_sainted_o0o on 2006-12-10
Well, that's going to be a problem because I never received any XP disk - the XP OS is integrated into my system recovery disks.

---

### Post by bigken on 2006-12-10
you could download the windows xp boot floppies and go into recovery console once your in the console just type fixmbr enter then fixboot enter then type exit 

you might be able to enter the recovery console hitting F8 just after the bios screen :-k


or borrow a windows xp cd

---

### Post by o0o_sainted_o0o on 2006-12-10
Ok then,

So once I run fixboot, I then should be ok to completely format the linux paritions without having any grub problems?

Thanks in advanced.

---

### Post by max.diems on 2006-12-10
HDDs are cheap these days, and if a Linux install is taking so much disk space, you should probably get a new disk even if you do get rid of Linux.

---

### Post by bigken on 2006-12-10
its fixmbr 1st then fixboot yep you can do what you like with your linux parttions 

this is how i would do it download and burn gparted boot from gparted cd delete your linux parttions 

the run the windows fix

---

### Post by o0o_sainted_o0o on 2006-12-10
Ok, I did what you said and I couldn't access fixmbr. I downloaded the program to create the bootable floppy disks, then booted with the floppy's, which eventually got to a black screen with the following prompt C:/>

I then typed in fixmbr, and nothing.

All I got each time I typed it was:

C:/>
C:/> 
C:/>

I should note that I don't have any recovery sector, recovery partition or console.

Anyways, because I deleted the linux partitions, I had nowhere to go except to a big fat grub error screen. Therefore, I reinstalled Kubuntu via the bootable CD and am now back to square one?

So tell me, is there anyway, manually, without the Windows XP CD, to get the boot ladder back to MS default?

---

### Post by o0o_sainted_o0o on 2006-12-10
I'd like to add that this is pissing me off now. No disrespect to you guys and I appreciate all the help, but to be honest I'ma shoot some pengiuns.

---

### Post by ryan00davis on 2006-12-11
just a thought, but if you have any friends who do have windows disks, than you can barrow theirs.  

also, if you have a dell, they like to disguise their windows disks and make them purple or something like that.

once you do have the disk, you want to boot into recovery mode, select which operating system, probably only have 1 choice (linux shouldnt show up), then run fixmbr and fixboot

the other option, if you cant get that to work and/or cant get your hands on an xp disk, i believe lilo will run by itself, so you could put lilo on the mbr, delete the linux partition, and lilo will still be there until you can get the windows stuff working.  note that you wont be able to edit lilo once you delete linux.  im not completely sure that lilo will run without linux on there, but i believe thats how it worked back when i did use it, someone correct me if im wrong

hope that helps
ryan

---

### Post by bigken on 2006-12-11
did you try F8 when booting into windows ?

also take a look [here]("http://support.microsoft.com/kb/314058")

---

