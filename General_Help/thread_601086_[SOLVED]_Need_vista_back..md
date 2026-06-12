---
title: "[SOLVED] Need vista back."
date: 2007-11-02
forum: General Help
---

### Post by stitcher06 on 2007-11-02
I recently installed ubuntu and it ( rather, I) wiped out vista completely.  I've tried using the recovery discs for vista, but it won't load.  I've been given quite a few suggestions most pointing at the fact that I will need to have a re-formatted hard drive to use the vista recovery cd's.  I've tried gparted, but can't figure out how to format the hard drive completely removing ubuntu to start over.  I've also gotten the suggestion of fdisk, but am unsure how to use.  Help!!!!  I just want to get vista back up if possible and try again, but need the windows side of things for special software.

---

### Post by Pumalite on 2007-11-02
Use Super Grub and see if there is any Vista left:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by American_Outcast on 2007-11-02
> **stitcher06 said:**
> I recently installed ubuntu and it ( rather, I) wiped out vista completely.  I've tried using the recovery discs for vista, but it won't load.  I've been given quite a few suggestions most pointing at the fact that I will need to have a re-formatted hard drive to use the vista recovery cd's.  I've tried gparted, but can't figure out how to format the hard drive completely removing ubuntu to start over.  I've also gotten the suggestion of fdisk, but am unsure how to use.  Help!!!!  I just want to get vista back up if possible and try again, but need the windows side of things for special software.


Use the Ubuntu Livecd to delete the partitions. You won't be able to do anything with mounted partitions, they need to be unmounted. You can also make a new ntfs or fat32 with the livecd's gparted if Vista still doesn't  recognize anything on the drive.

---

### Post by jrharvey on 2007-11-02
> **American_Outcast said:**
> Use the Ubuntu Livecd to delete the partitions. You won't be able to do anything with mounted partitions, they need to be unmounted. You can also make a new ntfs or fat32 with the livecd's gparted if Vista still doesn't  recognize anything on the drive.

I agree, if you use the live cd to format the previous ext3 format to ntfs then your recovery should recognize this. This will only work if you even have a recovery option left., It is a possibility you may have wiped it off the hard disk when intalling ubuntu. Hopefully this is not the case. While doing this you may also want to make another partition (ext 3) for ubuntu and dont forget a 1G swap partition if you want to dual boot.

---

### Post by stitcher06 on 2007-11-02
I'm pretty sure there's nothing left of vista from what others have suggested I do and report to them.  The install of ubuntu completely wiped out that partition and started over through my errors installing.  Nothing has been lost on this computer as it's a spare.  I just want to scrub everything and start over if possible.  What's the easiest way to do this and be able to  re-install vista from the recovery cd's?  I have put in the cd I assume is called the "live cd".  It is the cd I installed ubuntu from.  When rebooted with the cd in the drive, it still boots into the ubuntu operating system.   I am at a loss as to how to use gparted from the live cd.  Help!!  Thanks.

---

### Post by American_Outcast on 2007-11-02
> **stitcher06 said:**
> I'm pretty sure there's nothing left of vista from what others have suggested I do and report to them.  The install of ubuntu completely wiped out that partition and started over through my errors installing.  Nothing has been lost on this computer as it's a spare.  I just want to scrub everything and start over if possible.  What's the easiest way to do this and be able to  re-install vista from the recovery cd's?  I have put in the cd I assume is called the "live cd".  It is the cd I installed ubuntu from.  When rebooted with the cd in the drive, it still boots into the ubuntu operating system.   I am at a loss as to how to use gparted from the live cd.  Help!!  Thanks.


With the Livecd Just go to System>Administration>Partition Editor. Unmount the partitions and then delete them. Create an ntfs partition.

Edit: When the cd loads you get a list of what you want to boot from the Livecd. Choose the install/livecd option on the top of the list.

---

### Post by Pumalite on 2007-11-02
Delete all partitions and then make one large partition of your whole hard drive formatted ntfs; install Vista. Then use Vista partitioner to allocate space for Ubuntu. Then install Ubuntu.

---

### Post by stitcher06 on 2007-11-02
> **American_Outcast said:**
> With the Livecd Just go to System>Administration>Partition Editor. Unmount the partitions and then delete them. Create an ntfs partition.

Edit: When the cd loads you get a list of what you want to boot from the Livecd. Choose the install/livecd option on the top of the list.

Maybe I'm not using what you call the "live cd."  I am inserting the same cd I installed ubuntu from.  It doesn't give me any choices when restarted.  The system simply restarts the ubuntu operating system and then shows my that a cd is in the drive.  When I go to system-administration-gnome partition editor it doesn't allow me to do anything.  Most of the menu selections aren't active.  When I selected the largest partition and tried to unmount, it said it couldn't since other things were mounted with it and stated I should do this manually.  I'm just looking to start over.  Thank God I am not worried about losing information because this is a backup computer.  Any suggestions?  Thanks.

---

### Post by American_Outcast on 2007-11-02
> **stitcher06 said:**
> Maybe I'm not using what you call the "live cd."  I am inserting the same cd I installed ubuntu from.  It doesn't give me any choices when restarted.  The system simply restarts the ubuntu operating system and then shows my that a cd is in the drive.  When I go to system-administration-gnome partition editor it doesn't allow me to do anything.  Most of the menu selections aren't active.  When I selected the largest partition and tried to unmount, it said it couldn't since other things were mounted with it and stated I should do this manually.  I'm just looking to start over.  Thank God I am not worried about losing information because this is a backup computer.  Any suggestions?  Thanks.

What is your boot setup in your bios? Does it boot from the CD drive first or the hard drive? If it is from the hard drive first change the order so it boots from the cd drive first instead and the hard drive second.

Edit: The install cd is the livecd.

---

### Post by mysticrider92 on 2007-11-02
Your BIOS is probably set to boot from the hard drive before CD drive. Watch the POST screen carefully (if you have a Dell, HP, Compaq, etc you might need to hit TAB then PauseBreak), and look for a key code that says "boot selection menu" (F11 on my MSI mobo, could be different).

If there is no option for this, you will need to select it in the BIOS. Follow the same steps, except look for a key to enter "setup". From there, you will be able to modify the boot sequence. Tell the computer to load from the cd drive first, then the hard drive. 

After setting it up or getting to the boot selection menu, choose boot from cd. The Ubuntu boot menu will show up, press enter on the first option. Now you can follow all of the steps everyone else has posted.

---

### Post by jrharvey on 2007-11-02
You have to unmount the drives before you can edit them. The last guy said to delete all the partitions but DO NOT delete your recovery partition (that is if you still have one). To unmount a drive just go to "places" then "computer" and on the left you will see your mounted drives. Right click on them and select unmount. Then go back to Gparted and contitnue to format the drives. Is your windows recovery disk on a cd or is it inside your hard drive?

---

### Post by Pumalite on 2007-11-02
To do what I suggested in post # 7 you need Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> Maybe I'm not using what you call the "live cd."  I am inserting the same cd I installed ubuntu from.  It doesn't give me any choices when restarted.  The system simply restarts the ubuntu operating system and then shows my that a cd is in the drive.  When I go to system-administration-gnome partition editor it doesn't allow me to do anything.  Most of the menu selections aren't active.  When I selected the largest partition and tried to unmount, it said it couldn't since other things were mounted with it and stated I should do this manually.  I'm just looking to start over.  Thank God I am not worried about losing information because this is a backup computer.  Any suggestions?  Thanks.

you are using the live cd because you cannot acces gparted after you install ubuntu

---

### Post by mysticrider92 on 2007-11-02
> **jrharvey said:**
> you are using the live cd because you cannot acces gparted after you install ubuntu

No, a Ubuntu install can load Gparted (it is installed by default), but Gparted cannot be used on mounted disks (e.g. your Ubuntu / drive). 

I am not trying to step on your toes, just pointing that out so he doesn't mess something up. ;)

---

### Post by American_Outcast on 2007-11-02
> **mysticrider92 said:**
> No, a Ubuntu install can load Gparted (it is installed by default), but Gparted cannot be used on mounted disks (e.g. your Ubuntu / drive). 

I am not trying to step on your toes, just pointing that out so he doesn't mess something up. ;)

In 7.10 it is now called partition editor rather then gparted, etc, (even though it is gparted.)

---

### Post by jrharvey on 2007-11-02
> **mysticrider92 said:**
> No, a Ubuntu install can load Gparted (it is installed by default), but Gparted cannot be used on mounted disks (e.g. your Ubuntu / drive). 

I am not trying to step on your toes, just pointing that out so he doesn't mess something up. ;)

You are not stepping on my toes by any means. That is weird though. I did not know that you could access Gparted from a hard disk install. I dont think it installs by default though. Is it something you have to add?

---

### Post by mysticrider92 on 2007-11-02
> **American_Outcast said:**
> In 7.10 it is now called partition editor rather then gparted, etc, (even though it is gparted.)

Same difference, either way, you can not use it on a mounted hard drive. :)

jrharvey: I am not using Ubuntu right now (Arch Linux FTW!!), but I am fairly certain it is on there by default.

---

### Post by American_Outcast on 2007-11-02
> **mysticrider92 said:**
> Same difference, either way, you can not use it on a mounted hard drive. :)

Yes.

---

### Post by lyndaj70 on 2007-11-02
You are on the Live CD. GParted isn't on the standard install....

If you have a FAT32 partition, that will be your restore partition.  If you go to places --> computer, it will probably show up under Restore or some other name.  They are a few GB in size but I haven't seen any over 10GB.  Any partition larger than that would be your ext2 partition.

You may have 3 partitions on it:  The restore partition, the swap partition, and your linux partition.
Swap will be about 1GB in size, so it should be your smallest partition.  the Restore partition should be in the middle sizewize.  Delete the smallest and largest partitions and make one big ntfs partition, make it bootable, save and reboot with your restore disk in the drive....  That should get you going. 

If there are only 2 partitions on it... delete them both cause your recovery partition is toast.  

Good luck!

---

### Post by Pumalite on 2007-11-02
That's why Gparted Live CD has to be used. It does not mount the drives on boot.

---

### Post by stitcher06 on 2007-11-02
Yup, I'm that new at this.  It was booting from the hard disc versus the cd drive.  Got that fixed now.  I'll try all your suggestions.  Probably will disappear for awhile.  Thank you all for your help!!!  I look forward to learning linux, but have got to get vista back on since this computer is really meant to be a windows backup system for our main computer for a business.  Thanks again!!!!  Let you know how I make out.

---

### Post by jrharvey on 2007-11-02
Is it possible to unmount the the file system while running Ubuntu from the hard disk??? Haha either way I am getting off topic. It just makes it so difficult now that most computer companies do not give you a CD version of windows. All this recovery on the hard disk stuff makes me hate windows even more. Im sure they do it to protect themselves from software theft but geese it is frustrating.

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> Yup, I'm that new at this.  It was booting from the hard disc versus the cd drive.  Got that fixed now.  I'll try all your suggestions.  Probably will disappear for awhile.  Thank you all for your help!!!  I look forward to learning linux, but have got to get vista back on since this computer is really meant to be a windows backup system for our main computer for a business.  Thanks again!!!!  Let you know how I make out.

Good luck :)

---

### Post by thx11381974 on 2007-11-02
Download a cracked copy of Vista off bittorrent, That should install no problem.Plus you won't have to worry about calling M$ to beg them to reactivate it.

---

### Post by American_Outcast on 2007-11-02
> **jrharvey said:**
> Is it possible to unmount the the file system while running Ubuntu from the hard disk??? Haha either way I am getting off topic. It just makes it so difficult now that most computer companies do not give you a CD version of windows. All this recovery on the hard disk stuff makes me hate windows even more. Im sure they do it to protect themselves from software theft but geese it is frustrating.

No you won't be able to unmount the file systems when you are running Ubuntu from the hard drive. It is using them and won't let you. 

You can always call the company to request the cd's. I have done that three times, twice with my Compaq's and once with someones HP. They sent my the disks through FedEX over night each time free of charge.

---

### Post by jrharvey on 2007-11-02
> **thx11381974 said:**
> Download a cracked copy of Vista off bittorrent, That should install no problem.Plus you won't have to worry about calling M$ to beg them to reactivate it.

You better edit this off before someone kicks you off the forum.

---

### Post by Pumalite on 2007-11-02
That's why is so nice to have Gparted Live CD.

---

### Post by jrharvey on 2007-11-02
> **American_Outcast said:**
> No you won't be able to unmount the file systems when you are running Ubuntu from the hard drive. It is using them and won't let you. 

You can always call the company to request the cd's. I have done that three times, twice with my Compaq's and once with someones HP. They sent my the disks through FedEX over night each time.

I might try that some day. Does it cost anything???

---

### Post by stitcher06 on 2007-11-02
> **thx11381974 said:**
> Download a cracked copy of Vista off bittorrent, That should install no problem.Plus you won't have to worry about calling M$ to beg them to reactivate it.

I wondered if that would be the case.  I will have to call them to re-activate my copy of vista even if all this works?  How do I go about the download off bittorrent you mentioned?  Thanks.

---

### Post by mysticrider92 on 2007-11-02
> **jrharvey said:**
> You better edit this off before someone kicks you off the forum.

It was probably a joke, but I have seen people banned on other forums for comments like that...

stitcher06: if you do not know how to bittorrent a copy of Windows, don't even try to learn, and do not try it. Even if you have the original disks, it is very illegal. Your Windows should be able to activate easily (most likely without a call), but without an original disk, you can get into serious trouble (Bill Gates has better lawyers than any of us..).

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> I wondered if that would be the case.  I will have to call them to re-activate my copy of vista even if all this works?  How do I go about the download off bittorrent you mentioned?  Thanks.

Do not mind this guy, he doesnt know what he is talking about.. Your copy of Vista is LEGAL and you should be able to activiate it without any problems. You will not have to call microsoft as long as you have an internet connection.

---

### Post by stitcher06 on 2007-11-02
Seeing all the quick responses to the cracked copy idea lets me know I won't try that option.  Thanks again for your help everyone.  One last question.  Will I be able to do anything before I beg microsoft to reactivate my copy of vista if it works?  Thanks.

---

### Post by Pumalite on 2007-11-02
You can get an OEM Vista in EBay for ten bucks and use the serial # stamped in your machine.

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> Seeing all the quick responses to the cracked copy idea lets me know I won't try that option.  Thanks again for your help everyone.  One last question.  Will I be able to do anything before I beg microsoft to reactivate my copy of vista if it works?  Thanks.

Hahaha, you will not have to beg. I have activated my LEGAL copy of vista 3 times. There is no begging involved. It should work just fine by clicking the button ACTIVATE. Now I am not trying to sound like an old geyser by saying "dont steal" i am just saying why would you steal when you have the real thing.

You never answered my question though.... Do you have a vista recovery CD????

---

### Post by mysticrider92 on 2007-11-02
> **stitcher06 said:**
> Seeing all the quick responses to the cracked copy idea lets me know I won't try that option.  Thanks again for your help everyone.  One last question.  Will I be able to do anything before I beg microsoft to reactivate my copy of vista if it works?  Thanks.

They will give you 30 days of full use before you need to activate it. As a note, while activation is an annoyance, I have reinstalled Windows many times on the same computer without having to call Microsoft. It will usually take at least 5 reinstalls before you would need to call them.

---

### Post by jrharvey on 2007-11-02
> **mysticrider92 said:**
> They will give you 30 days of full use before you need to activate it. As a note, while activation is an annoyance, I have reinstalled Windows many times on the same computer without having to call Microsoft. It will usually take at least 5 reinstalls before you would need to call them.

When I was using XP i would get a virus once a month and have to reformat and reinstall. I must have activated 20 times and had no problem. Thank god for linux

---

### Post by stitcher06 on 2007-11-02
> **jrharvey said:**
> Hahaha, you will not have to beg. I have activated my LEGAL copy of vista 3 times. There is no begging involved. It should work just fine by clicking the button ACTIVATE. Now I am not trying to sound like an old geyser by saying "dont steal" i am just saying why would you steal when you have the real thing.

You never answered my question though.... Do you have a vista recovery CD????

Sorry, I'm trying to keep up here jotting down notes.  I do have the recovery CD's that I burned originally with the new computer.  There are 2 cd's for recovery and 1 for applications and drivers.

---

### Post by Pumalite on 2007-11-02
The problem is for the laptops that are sold without a disc. Especially when you just wiped off your hard drive.

---

### Post by American_Outcast on 2007-11-02
> **stitcher06 said:**
> Sorry, I'm trying to keep up here jotting down notes.  I do have the recovery CD's that I burned originally with the new computer.  There are 2 cd's for recovery and 1 for applications and drivers.


Install Vista first and then set up partitions later for Ubuntu. Chances are if that is a bundled version of Vista from your computer manufacturer, like my DvD's from Compaq, two install and one driver disk, it will wipe the whole hard drive, create the recovery partition and then install Vista. You can resize the partition later and then create the ext3 partition, swap partition and install Ubuntu again if you choose to.

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> Sorry, I'm trying to keep up here jotting down notes.  I do have the recovery CD's that I burned originally with the new computer.  There are 2 cd's for recovery and 1 for applications and drivers.
Ok that helps out alot. In that case I would follow pumalite's directions on page one. Just wipe it clean and make a ntfs partition. An easy way to install ubuntu (dual boot with vista) is with the WUBI alpha. It worked great on my girlfreinds laptop and my roomates computer. It is a great program if you are mainly a windows user. IT IS SAFE TOO. It will not hurt your windows drive.

If you are planning on using Ubuntu alot then go with a seperate partition. It is the best way to install ubuntu but I didnt know how much you used it.

---

### Post by stitcher06 on 2007-11-02
> **American_Outcast said:**
> Install Vista first and then set up partitions later for Ubuntu. Chances are if that is a bundled version of Vista from your computer manufacturer, like my DvD's from Compaq, two install and one driver disk, it will wipe the whole hard drive, create the recovery partition and then install Vista. You can resize the partition later and then create the ext3 partition, swap partition and install Ubuntu again if you choose to.

I will definetely choose to install ubuntu again, but need to get back to vista if possible.  I've learned a ton the last few days.  I even configured my broadcom wireless card.  I'm so proud.  You linux bunch are awesome and the os works like I wish windows did.  The first thing I'll be asking about is how to correctly get ubuntu back on as a dual boot with windows.  Thanks again for everyone's help.  I'll be back!!!

---

### Post by jrharvey on 2007-11-02
> **stitcher06 said:**
> I will definetely choose to install ubuntu again, but need to get back to vista if possible.  I've learned a ton the last few days.  I even configured my broadcom wireless card.  I'm so proud.  You linux bunch are awesome and the os works like I wish windows did.  The first thing I'll be asking about is how to correctly get ubuntu back on as a dual boot with windows.  Thanks again for everyone's help.  I'll be back!!!

This is why I sugguested WUBI. It is a super simple way to dual boot. The only problem is that your computer doesnt suspend or hybernate and the max size is 30G. Other than that it works like a charm. 

Wubi Alpha    [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

Yes it is ALPHA but I havnt had any problems.

---

### Post by jake16424 on 2007-11-03
> **stitcher06 said:**
> I recently installed ubuntu and it ( rather, I) wiped out vista completely.  I've tried using the recovery discs for vista, but it won't load.  I've been given quite a few suggestions most pointing at the fact that I will need to have a re-formatted hard drive to use the vista recovery cd's.  I've tried gparted, but can't figure out how to format the hard drive completely removing ubuntu to start over.  I've also gotten the suggestion of fdisk, but am unsure how to use.  Help!!!!  I just want to get vista back up if possible and try again, but need the windows side of things for special software.

well whatever you do DONT GO BACK TO VISTA, 

go to XP if anything, vista has BUILT IN key loggers wich send your email and personal information to companies to see what you search for on the internet, and what your intrested in, therefore able to morph marketing for the majority..

plain and  simply, microsuck is trying to take everything over, like AT&T did with teh pay phones..

and, i use windows XP cause its more supported NOT because i like it..

---

### Post by thx11381974 on 2007-11-03
If he has a license for vista,  who cares? 
I'm running a cracked copy of MCE2005 which I have a license for. It's just easer to crack it than to beg for reactivation. 
Visa I understand is prone to deactivating just to screw with ya. Cracking it just makes it run like it should!

---

### Post by stitcher06 on 2007-11-03
Just wanted to let everybody know that vista is back up and running again (unfortunately).  I wish we didn't need it at all, but we do for some special windows software.  Thanks for all you help.  You've got me hooked on linux!!!!  The first thing I'll be doing is getting ubuntu installed back on the system correctly this time.  Thanks again!!!!!!:)

---

### Post by Maestro23 on 2007-11-03
> **stitcher06 said:**
> Just wanted to let everybody know that vista is back up and running again (unfortunately).  I wish we didn't need it at all, but we do for some special windows software.  Thanks for all you help.  You've got me hooked on linux!!!!  The first thing I'll be doing is getting ubuntu installed back on the system correctly this time.  Thanks again!!!!!!:)

Mark this SOLVED using Thread Tools.  And when you get ready to come back to Ubuntu... We'll be here. :guitar:

---

