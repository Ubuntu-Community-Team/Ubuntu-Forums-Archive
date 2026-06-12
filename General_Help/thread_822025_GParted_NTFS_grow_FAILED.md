---
title: "GParted NTFS grow FAILED"
date: 2008-06-07
forum: General Help
---

### Post by Ian505 on 2008-06-07
GOALS OF THIS THREAD: Get windows to boot!
What I can do... 
... access the NTFS partition from Ubuntu Live CD.
... run recovery console from original windows XP cd.

What I can't do...
...get windows XP to boot! (Blinking _)
... figure out what all of these sqmdata##.sqm files are for in the root of my NTFS partition.

-------------------------------

I had Ubuntu 7.10 installed on my computer in a separate partition, and decided to remove it and revert entirely to Windows for a time as I don't have the time ATM to work with my WiFi card. 

I copied all the data that I needed from my Ubuntu partition to my windows partition. Then I had gparted shrink the ext3 partition and grow the ntfs partition, as not all of my pictures would fit on the NTFS partition. That went fine

I deleted the ext3 partition, and the swap partition, and grew the ntfs partition. Everything (including the read only test) went fine until at the end it ran the ntfs check on it, which failed. Some of the information it provided was that the drive was "Busy" and any modifications would "not be recognized by linux." I exited Ubuntu (8.04 disk) and tried to boot. I got a Error 22 from GRUB, which didn't bother me. I pulled out my old Super GRUB disk and told it to repair the MBR with the default windows boot loader. Rebooted, and got a blinking white _ that didn't go away. I tried to boot it from the disk, 2nd partition (which confused me as I didn't know that I had but one... and it was listed under a 2nd drive...and I only have one...) no luck. I activated the 1st partition, which was NTFS, with the same result. I tried the phantom second one, no luck. Chkdsk from an original windows xp cd didn't do anything. 

What's wrong! I really don't want to have to reinstall windows or lose my several years worth of photos!

Please help!

-Ian

**PHANTOM DISK FOUND!-** Turns out it was a SD flash card.... I feel soo stupid... Still wont boot though. :-(

---

### Post by Ian505 on 2008-06-08
Update!
I have run both **FIXMBR** and **FIXBOOT** from the windows recovery CD, as well as run chkdsk 3 times now. So instead of just a blinking cursor, I get...

Error loading operating system(insert blinking _ here!)

Big help... burning the latest version of Super Grub Disk to see if I can't install GRUB over the XP bootloader and see if that solves anything.

The strange thing is I can access the drive from the recovery CD and Ubuntu... it's just not booting!

I have found similar problems, and I am considering switching forums with this problem as at first I thought that this was a GParted issue (as it happened directly after my NTFS partition resize) but mabye it's not?

Oh one more thing, when I run the partition information utility from the recovery console, it shows that there is the main partition with about 4MB of free space. :confused: I don't remember leaving any free space!

***If you have ANY idea of what is going on please post! I have been working on this for 4 hours now!:(***

Thanks,
Ian

---

### Post by adrian15 on 2008-06-10
> **Ian505 said:**
> I thought that this was a GParted issue (as it happened directly after my NTFS partition resize) but mabye it's not?


Hi Ian, I do not know what to advice you.

Please take a look at the links present at the resources section at the [Windows refuses to boot (Super Grub Disk Wiki Page)](http://www.supergrubdisk.org/wiki/WindowsRefusesToBoot)

In order to try to boot your Windows try always the: **Boot & Tools -> Boot Partition** option so that you can see your actual Windows.

I suppose that Windows was the first partition ** before and after ** the ntfs grow. Isn't it?

adrian15

---

### Post by adrian15 on 2008-06-10
> **Ian505 said:**
> I tried to boot it from the disk, 2nd partition (which confused me as I didn't know that I had but one... and it was listed under a 2nd drive...and I only have one...) no luck.

Please check: [Grub Hard Disk Order](http://www.supergrubdisk.org/wiki/GrubHardDiskOrder) to get an idea.

adrian15

---

### Post by Ian505 on 2008-06-12
Thank you so much for replying... I was afraid nobody would.

The 2nd disk turned out to be a connected USB Compact Flash drive from my old camera. (I disconnected it.) THAT mystery is solved.

I tried the Boot Partition option, but only got the blinking _.

The windows partition was the 2nd partition before the grow and the only partition after it... that is until this mysterious 40GB of free space appeared.:confused:

Does anybody know of a NTFS partition recovery tool that doesn't cost $80!?

-Ian

---

### Post by Ian505 on 2008-06-12
Found a project called TestDisk which was on the ["Ultimate Boot CD"]("http://www.ultimatebootcd.com/") (version 4.1.1, latest) and ran that. I ran a "deep analysis" of the disk and it came up with 3 partitions:

1. NTFS - started at 0 - Current Status: Deleted
2. NTFS - started at ### - Current Status: Deleted
3. Linux SWAP - Started at ### - current status: logical

I wanted to have the first one the primary boot, which was basically the expanded 2nd one. And I didn't want the SWAP at all. So I deleted the SWAP, left the 2nd NTFS, and changed the first one to primary boot. No luck... not even "Error Booting Operating System" this time. Just the blinking _.

I am wondering... since the SWAP semi-survived... is there some sort of rhyme or reason to how you are supposed to handle SWAP logical/extended partitions?

-Ian

---

### Post by adrian15 on 2008-06-13
> **Ian505 said:**
> Found a project called TestDisk which was on the ["Ultimate Boot CD"]("http://www.ultimatebootcd.com/") (version 4.1.1, latest) and ran that. I ran a "deep analysis" of the disk and it came up with 3 partitions:

1. NTFS - started at 0 - Current Status: Deleted
2. NTFS - started at ### - Current Status: Deleted
3. Linux SWAP - Started at ### - current status: logical

I wanted to have the first one the primary boot, which was basically the expanded 2nd one. And I didn't want the SWAP at all. So I deleted the SWAP, left the 2nd NTFS, and changed the first one to primary boot. No luck... not even "Error Booting Operating System" this time. Just the blinking _.


If I were you I would try to try these tools such as recover from a live cd to try to recover files from your deleted ntfs partition. I do not think you are going to recover something usable from your ntfs mess.

Remember do never interrupt a resize operation.

> **Ian505 said:**
> 
I am wondering... since the SWAP semi-survived... is there some sort of rhyme or reason to how you are supposed to handle SWAP logical/extended partitions?
-Ian

The SWAP partition is not useful. You can delete it if you want to.

adrian15

---

### Post by Ian505 on 2008-06-25
If I wanted to just take my files off and start from scratch, I would have. However, I don't want to because I would lose several hundred dollars worth of software associated with that copy of windows.

I know I know... I should have backed it up. But please don't lecture me. I have learned my lesson. If you want to post, please just post with info about how to save my butt.

Thanks,
Ian

---

### Post by breadbin on 2008-06-25
can you boot with the xp cd and install it again but choose not to change the filesystem? That will write the mbr back hopefully and maybe let you boot back into xp and from there  you can try and repair the drive. once you are in xp you can add a new drive and mirror the contents of the old hard disk to the new one if thats what you wnat. i don't know if it'll work i'm only giving out suggestions that you might not have thought of before. hope it works out for you

---

### Post by Ian505 on 2008-07-06
> **breadbin said:**
> can you boot with the xp cd and install it again but choose not to change the filesystem? That will write the mbr back hopefully and maybe let you boot back into xp and from there  you can try and repair the drive. once you are in xp you can add a new drive and mirror the contents of the old hard disk to the new one if thats what you wnat. i don't know if it'll work i'm only giving out suggestions that you might not have thought of before. hope it works out for you

Yes, but I don't have a spare drive to install Windows on again and installing windows on the damaged hard drive will require a reformat (I think) and that will mean bye bye data. So thanks for the suggestion, but I don't think that will work.

Hopefully this week I can get someone to look at it, I am planning to call on Monday.

-Ian

---

### Post by caljohnsmith on 2008-07-06
Ian, you should try to use the "repair Windows" option from your Windows CD. That will not erase the Windows partition, but it will instead copy over all the original Windows system files from your Windows CD. Of course that assumes your Windows partition is not so messed up that the Windows CD can't even recognize it as a valid Windows partition.

---

### Post by Ian505 on 2008-07-06
Fortunately, my system is not that messed up and that IS an option... but I am pretty sure that I will lose all of the software that is associated with that copy of windows by doing so... which is NOT what I want to happen as I have a LOT of software on that copy.

---

### Post by caljohnsmith on 2008-07-06
> **Ian505 said:**
> Fortunately, my system is not that messed up and that IS an option... but I am pretty sure that I will lose all of the software that is associated with that copy of windows by doing so... which is NOT what I want to happen as I have a LOT of software on that copy.
Actually, that is the whole point of doing a Windows repair rather than a complete reinstall--it only tries to repair all the windows system stuff while not messing with any of your installed programs. I know it can work, because that's exactly how I saved my Windows partition recently after my Windows completely crashed from a failed update.

---

### Post by Ian505 on 2008-07-06
Okay... I am willing to try it- but first could you point me to a decent free (as in price, though as in -dom would be great) drive imaging software? The current one that I use ([PartImage]("http://www.partimage.org/Main_Page")) only copies partitions and I really just want a bit for bit image that I can put onto an external drive- but I want it in a file such as .img not mimicing the entire drive to another. 

Sorry if I am a bit confusing... it's late here and I am almost ready to turn in. I would like to be able to set it to backup overnight though...

-Ian

---

### Post by imolafem on 2008-07-06
Installing Windows will not require a format if you choose to Repair Windows -- its an option kind of like where you see the Recovery Console.  That will find where Windows is installed and install it over it.  Things might not work quite right until you install the service packs and hotfixes again.... and they might never work quite right until you do some tweaks -- or it could all work perfectly.  Your mileage will vary with Windows Repair =)

---

