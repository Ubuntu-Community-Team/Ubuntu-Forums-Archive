---
title: "Duel Boot Shared partition."
date: 2008-05-12
forum: General Help
---

### Post by Mistron on 2008-05-12
eHey,

I want to install a Dual Boot system with a shared partition of Windows XP and Ubuntu. This laptop already has a fresh installation of Windows XP done with recovery disk. I want to create a shared partition so I can share files between Windows and Ubuntu. I have found some guides on how to do this, so this is not the real problem. Everything looks easily doable. Only when starting with repartitioning the Hard Disk I see there is a hidden partition at the front of the hard-disk, and I have no clue where it's for. From what I have read it may be a recovery partition.

 This is around how I want the partitions to be laid out:
Part. One: Windows XP OS.     Size: ~10GB
Part. Two: Ubuntu OS.         Size: ~10GB
Part. Three: Ubuntu Swap.     Size: 1024MB (Best is 2x memory. memory= 1024MB)
Part. Four: Shared.           Size: All the rest. (total disk is 80GB)

Only now I don't know what to do with that first hidden partition that might be a recovery. But I am unsure what it really is and/or it save to delete. I don't ask a real question here I notice but I would still be happy with your help.

 Greetings Mistron.

p.s. I also have another minor question, since I am still looking around at which distro to choose. Is it easily possible to overwrite this current Linux partition with another Distro? This may come in handy, though I will still install Ubuntu first since it may take me weeks before even making a minor decision and I can always use the Recovery disk I have here.

---

### Post by michaelaly on 2008-05-12
It's likely the hidden partition is some sort of recovery partition possibly with hardware testing utilities and/or a disk image(windows). Check with the manufacturer of your comptuer to be sure. The utilities can be helpful in case of a hardware problem, but they're not entirely necessary. 
And it is usually very easy to overwrite one distro with another. You can even set up an extra partition to try out other distros and run a tripple boot, that way there's no need to delete your current Linux install to try another distro. 
best of luck,

---

### Post by Mistron on 2008-05-12
Okay thanks. =) 
Just some other last questions now.
Would it be safe to delete that partition if already have recovery disks en a disk with utility's and drivers? (Even have 3xdifferent versions of recovery disk, EN, FR & NL) That they will work all the time even when I have it deleted. 
And I think I can't really contact the manufacturer and get any help, this is a Laptop I got from the neighbors to try and repair and if it succeeded I could have it. And it also is already outside of the warranty. Though I will Google some more and maybe find it out.

And okay, thats great. That way I can safely experiment with different distro's without going to the trouble of removing/recovering every time I try out a different one.

Thanks again. ^^

[I]Edit: I have an Asus A6000 Series entertainment notebook.
Asus A6Q00VA[/I]

---

### Post by Mistron on 2008-05-12
I decided to take the shot and delete the partition. The Recovery disk should be fine.
Only one problem, in Qparted if I delete the first partition (which is probably recovery) how will that reflect to windows. 
I noticed that the first partition is called /dev/hda1 and the second /dev/hda2. Will windows still boot if I simply delete the first partition? And how will that go with the names, shouldn't windows than have hda1. And how will the rest be named?

Thanks already. =)

Edit: Nevermind, I just decided to go full Linux, donno where I will using windows for. It's a laptop so it isn't suited for gaming anyway. and most things have a linux alternative and if not I better start learning how to make it. =p

---

### Post by michaelaly on 2008-05-13
Guess you figured it out. hda1 is the first partition on the first drive, hda2 is the second partition on the first drive(hdb1 would be the first partition on the second physical drive, if you had one). 
Should you need to reestablish a windows install for some reason let the Grub bootloader load windows, it will auto-detect all the installed OS's and make an entry for you.

---

