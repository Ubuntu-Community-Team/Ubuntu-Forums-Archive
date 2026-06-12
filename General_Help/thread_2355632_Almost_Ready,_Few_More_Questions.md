---
title: "Almost Ready, Few More Questions"
date: 2017-03-14
forum: General Help
---

### Post by jischinger on 2017-03-14
I was able to format a flash drive and I think I'm pretty much ready to boot off of it, but I have a few questions before I follow through.

Currently I have a DELL 530 Intel Duo vista 32 computer

The HD is 300gigs partitioned.
On C there is 288G total with 170G free.
On the D sits the Vista OS Recovery roughly 10G

The Flash Drive currently is 7Gs with roughly 5G free.

Now if I were to install Ubuntu OS on the HD do I have enough room to install and leave Vista there if I need to drop into Windows later? IOW do I have enough room to house both Ubuntu and Vista on this drive untill I clean and move the files?

OR 
Could I install Ubuntu completely on this or another flash drive or external drive ?

------
I have a few more questions, but I'll stop here foe now.


thanks

---

### Post by gdesilva on 2017-03-14
Check [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) for the minimum requirements. However, what one needs to keep in mind is how much user data one is intending to keep in Vista vs in Ubuntu. If you are going to save all your videos in Ubuntu then obviously you would need to allow more space for Ubuntu.

---

### Post by HereInOz on 2017-03-14
If you intend to dual boot, then you need to have Windows installed first, resize its partition to make room for the Ubuntu install (use gParted on a CD), and then make sure that you select the correct installation option when asked what you want to do with the hard disk.  Get that wrong and you will wipe your Windows install.

---

### Post by Bucky Ball on 2017-03-14
> **HereInOz said:**
> If you intend to dual boot, then you need to have Windows installed first, resize its partition to make room for the Ubuntu install (use gParted on a CD) ...

Do not ever use Gparted to resize or do anything else with a Windows OS partition. You will almost definitely kill the boot and may break other things. Definitely no. Use Windows own Disk Management.

Rule of thumb: Windows OS partition? Resize with Windows tools. Linux OS partition: use Gparted or another Linux tool. Never the twain shall meet on that one. :)

The first part is right though and the description of shrinking the Win partition to make room for Ubuntu: install Win first. You will save umpteen headaches. The main thing to be aware of is whether you are installing in UEFI or legacy mode. However you install Win, that is the mode you MUST install Ubuntu in. 

Best to know exactly what you are aiming for before launching into an install. You have a blank disk. What do you want it to look like after? Pencil and paper, please. Draw a 'mud map' of how you are going to partition the drive. 

One way is to have Win on, say, 50Gb partition, Ubuntu on 25Gb and use the rest of the drive for a large /data partition (NTFS filesystem) which stores your personal data. This can then be accessed by either OS. Keep in mind that Ubuntu has no problem accessing Win partition but Win can't access Ubuntu's partition (they are EXT* filesystem). 

/Win = 40-50Gb (you will see how much room it is taking up when installed and before you shrink, but leave 'headroom', i.e. you may want to install more programs in Win later and you will need 10-20Gb headroom at all times or the OS will come to a crashing halt, so be generous with your headroom rather than skimpy)
/Ubuntu = 20-25Gb (and generally less)
/data = the rest of the drive but for
/swap = 2Gb at the end of the drive; /swap is like a Win pagefile but they go on a small partition in Linux world (as the pagefile can also in Win world? Don't quote me. :))

Hope that helps.

PS: It may be helpful to you to know that in Linux, drives are known as sda, sdb etc., the partitions on them as sda1, sdb5, etc. For instance. sdb1 would be the first partition on the second drive. Drives are drives and partitions are partitions. There is no drive 'C:/' or drive 'E:/' or whatever. Win calls them drives and they are actually partitions! Very confusing. That syntax is not used at all.

PPS: When you install Ubuntu after Win, you will need to choose 'Something Else' at the partitioning section to partition manually. No drama. Just ask if you get stuck, but in the meantime, [check here for full explanation]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation") (down the page a bit there is a full explanation with pics). You will see your freshly installed and resized Win partition in there (it will be NTFS filesystem and probably sda1). Just don't touch it or anything else that Win created during the install and you'll be fine.

Create your partitions in the free space you created by shrinking the Win partition with the disk management tool following the guide I link to above. :)

Good luck and any issue/questions, post away.

---

### Post by jischinger on 2017-03-15
well I think I get it  - I was watching a video on the install and it seemed the guy went with wiping windows out - I don't want to do that just yet or if I have to.

I have a USB external drive with a capacity of 900G (1T) with roughly 600G of free space -  it is not partitioned - 300Gs has a full image backup of C and a bunch of folders from a manual backup.

Question is: Can I use that external drive to install Ubuntu as is or even create a partition on that external using Ubuntu without losing the 300G worth of backups?
Then set the BIOS to boot off this Drive?

-thanks

ps. if this seems like it would be too complex for me to do - I looked at the page you linked -  I could move the manual files to another external and dump the windows  backup - reformat the external and just install Ubuntu on fresh on this external. ???

I want to figure this out before I go through all the effort though. Ideally if I can keep the backup and manual files AND install Ubuntu directly to the external without a hitch that would be the simplest thing to do. Then I could leave the old CDrive as is and zip all the lose files as legacy later.

I hope I am making sense

---

### Post by Bucky Ball on 2017-03-15
> **jischinger said:**
> Question is: Can I use that external drive to install Ubuntu as is

Yes.

 > **jischinger said:**
> or even create a partition on that external using Ubuntu without losing the 300G worth of backups?

Yes. You need to create a partition to install Ubuntu onto in free space (using 'Something Else' during the install) regardless of how you go about this.

> **jischinger said:**
> Then set the BIOS to boot off this Drive?

Yes, but you will need to install the grub to sdb (probably the external drive but check in gparted). The other option is to install grub to sda (probably the internal drive) and that will pick up all installs, Windows included, and add them to your choices at boot. You have the option of where you would like to install grub during 'Something Else'. This option, though, would rely on you having the external Ubuntu install plugged in when you boot your machine (or grub will complain that you have an install missing). 

Issues I can see: Where you install grub depends a lot on what you intend to do with the drive. Do you want this external drive to be able to boot on other machines or just this one? Expecting it to boot on other machines will be problematic because of the UEFI and legacy mode conflict mentioned earlier. There are ways around this, but I know nothing about them. 

Incidentally, install grub to sda or sdb, NOT sda1 or sdb1 or any partition. Install directly to the MBR of the disk, not into a partition on the disk, if you follow me. :)

---

### Post by jischinger on 2017-03-15
k, I didn't understand the whole grub thing - I will have to find a video about how this works or how I install it.
 
As far as having Ubuntu work on another machine, not important right now -  only if this one dies, but I think if I keep files I create on a separate drive - backed up -  it won't really matter if the unfortunate happens.
 
.....

now, let me just take one step back...


Right now I have an external drive with 1T and 300Gs used (random pics, docs, vids, a full image back-up; which is unimportant, and no OS) and 600G free space (give or take a few).


-------So to be clear - Can I just install Ubuntu as is without doing anything  -or-  do I have to put in a partition on thsi drive for fear that Ubuntu will want to format during install, thus wiping out the random files?------

---

### Post by Bucky Ball on 2017-03-15
[LIST=1]
[*]Boot from the Ubuntu install disk or USB, whichever you create.
[*]Choose 'Something Else'
[*]You will see your Win partition(s) there on the drive. Don't touch them at all. You are only interested in the free space.
[*]For a basic install, you will need two partitions: / and /swap. You use the installer to create the partitions in free space.
[*]The / partition is where the OS and settings go; /swap goes at the end of the drive and is about 2Gb
[*]You will see a bar along the bottom of the partitioning setup which asks where you want grub. No special procedure. Just choose sda (should be set to go there by default). 
[/LIST]

The mountpoints / and /swap are there by default. You don't need to create them, you only need to select them. The link to the 'something else' install gives instructions. The root partition should have the mountpoint /, be ext4 filesystem and the system will 'automagically' detect that is where to install the OS. Same with /swap. Make a 2Gb 'swapspace' partition.
 
As I mention, there are various ways of going about this. As you have a 300Gb partition already for Win I presume you have a lot of personal data on there as well as the operating system. I would personally back that personal data up, delete it from that partition and shrink the Win partition to 50Gb (see what size it is now and give it 10-15Gb more than that). You should defragment the partition a number of times prior to shrinking.

You will then be left with a heap more free space. Make the / partition for Ubuntu 20-25Gb, create a /data partition (NTFS filesystem) which leaves 2Gb for your /swap at the end of the drive (in other words, make /data as big as possible). Install Ubuntu.

Drop your backed up personal data onto the new /data partition. Now, you can create symlinks inside the /home partition in the / of Ubuntu which link to folders on the /data partition. 

Hope that makes some sense.

PS: If you have valuables backed up, no harm having a practice and just DON'T hit the button to install. You can get to 'Something Else' and have a look around, but NOTHING will actually be created until you give the go ahead. So just don't give the go ahead until you're confident and good and ready. :)

PPS:>  -------So to be clear - Can I just install Ubuntu as is without doing anything -or- do I have to put in a partition on thsi drive for fear that Ubuntu will want to format during install, thus wiping out the random files?------ 

To be clear: Ubuntu will not format anything you haven't told it to. Just make sure you use 'Something Else' and not one of the auto install methods, side-by-side or 'use whole disk' (which would naturally obliterate everything on there already). 

'Something Else' is for manual partitioning. Ubuntu can't and won't automatically obliterate everything on your disk using this method, but you can. :) Like I said, just don't touch anything that's already on the drive. The Win partitions will be NTFS and you will clearly see that in Something Else partitioning.

---

