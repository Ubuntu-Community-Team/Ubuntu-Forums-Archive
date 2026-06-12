---
title: "Backup and migration?"
date: 2017-08-24
forum: General Help
---

### Post by Jan_Johansson on 2017-08-24
Hi Guys/girls,

I have 2 small problems, I want to copy my setup from one laptop to another without changing the underlying OS setup - I will try to explain:

I travel back and forth between Denmark and Philippines approx. every 6 months, so instead of bringing my laptop with me everytime, I bought 2 identical laptops(Thinkpad R500) and have one in Denmark and one in the Philippines, both with Xubuntu 14.04 LTS 32bit - Then I just make backup of: thunderbird contacts and folders, firefox bookmarks and new documents to an USB stick and replace them on the other laptop when I'm there - this works like a charm. 
I also do a complete REDO backup(run from bootable usb), just in case. 

Unfortunately that cannot be done with the installed updates and programs, so everytime I'm in philippines/Denmark I have to install changed updates/programs. 

Are there a solution for this or do I have to live with the current setup?

Is there a better solution for the complete task, than the one I'm doing now?

REDO has a problem with disk size, that it can't restore to smaller size HDD, and one of the identical have a 320GB HDD where the other one has 500GB, so I can only restore the backup to the system if were made from or one with bigger size HDD - there is a workaround but I have not got it to work.

------------------------

Second problem, I just bought a new laptop of different model (Thinkpad X300) with window 7. It has different HW and the HDD is only 64GB SSD(being 1.8" its expensive to upgrade to larger GB size similair or bigger than the R500's), I'm thinking of buying an extra 64GB or 128GB SSD and have linux on that one and then swap to the windows HDD when needed(which is 1-2 times a year). The win 7 setup takes up 32GB of the 64GB HDD so running dual boot is not an option and the flash tools don't work in linux not even in wine.

I would like to have Xubuntu 16.04 LTS 64bit(fresh install), but with my software from the above setup, and my thunderbird contacts/folders and firefox bookmarks, so it will be basically identical to the above except for the OS version. 

Do I have to re-install all software in this new version or is there a migration tool that can do this for me - or one that can make a list of whats installed by me? 
Problem is that not all is in Application drawer some is commandline tools, and I can't remember whats installed by me?

Is there any problems between 32/64 bit versions when backing up/restoring thunderbird contacts and folders, firefox bookmarks, firefox sync?  
They are just copied out and zipped, no special SW used. 
- Before answering, remember that one system is 32bit and has to have these things restored from the 64bit one.

I know that if I use the X300 then I have to install and update OS and programs myself.


Like the identical systems above, I like to move my data by just using an usb stick and not the whole laptop, and eventually I will replace one of the R500's with the X300 - which one I'm not sure of yet.

In the philippines the internet connection is so bad that getting merely 1mbit connection is a blessing, therefore I don't use cloudbased options.

JBJ

---

### Post by TheFu on 2017-08-24
FF and TB stuff is agnostic about 32-bit/64-bit.  I've moved from Windows --> Linux --> OSX with those same settings too.  Just binary addons/plugins won't work.  JS ones work fine.

For the other questions, perhaps using something like **fsarchiver** to make an image before you travel is what you need to capture all the OS settings and patches?  Just don't mix 32/64-bit OSes.  I would create the image about a week before my trip, then the night before backup my HOME.

There are lots of tools for these things, so do your homework.  fsarchiver isn't a backup tool, it is a compressed imaging tool.  You'll want/need a self-contained Recovery Linux to restore it.

I started traveling with chromebooks running Linux about 4 yrs ago. They are cheap, light, fast, great battery so I don't mind using them for typical travel things.  Just be certain you verify that the way you want to run Linux is possible with the chromebook you get.  Many will only run with crouton, which isn't the same as running a full install - but crouton does have a full backup/restore method, so any chromebook can be used provided it is the same CPU type (intel vs arm).  The downside of crouton is that the kernel is controlled by google, so no extra kernel drivers can be loaded.  That was an issue for me.

Also, have you looked at other storage options?  USB3 flash devices are pretty fast, just don't expect them to last more than a year.  You could use an external SSD with 128GB and that should last a few years or 10. I have an m.2 version like that. Lots and lots of options for you to consider.

Linux isn't THAT picky about hardware at boot time.  Obviously, RAID controllers and odd network drivers will be an issue, but for a normal desktop, it is pretty plug and play.  I literally pulled a HDD from a Pentium4 (2005-ish) and put it into a Core i7 (2010-ish), booted and all the major things worked.  Only had to reset the udev rules for the wired ethernet so it would use eth0, not eth1.  RAID cards and GPU drivers might fall back to generic versions, but that should be expected.

Obviously, test it all out before your trip.  Whenever I'm traveling overseas, I test by taking my laptop and other gear to the local library.  If I can restore from an external, encrypted, backup using only the tools I have with me and not getting onto the internet until AFTER the restore is complete, then I know I'm good.  The first time, it didn't work. Over the years, I've gotten much better - it basically always works now.  Plus, my laptop doesn't have anything on it during travel besides a base OS installed the day prior.

---

### Post by oldfred on 2017-08-24
I am in similar circumstances. I used to be what Florida residents call a snowbird, or one who only travels South during the snowy season up North. Now I have reversed that and spend a bit more time in FL and less in Illinois.

I used to lug my laptop back & forth, and copied entire Firefox & Thunderbird profiles plus some data to laptop, originally XP, then XP & Linux then only Linux. 
But I am not a fan of laptops, screen too small, keyboard to high, just not ergonomic sitting on desk. So I built another desktop for Florida and cart my 32 & 64GB flash drives with my data. 
I have both systems configured with a larger /mnt/data partition where most of my data is.

I have fast enough Internet speeds that running updates is not a problem. But I also as part of my backup include a list of installed apps and after first time or two, the amount of changed data is relatively small.

Years ago Firefox & Thunderbird was only in XP, then in 32 bit Ubuntu and finally in 64 bit Ubuntu. While application changed from 32 bit to 64 bit, all the data is the same. I have tried to houseclean some older bits & pieces and do delete old emails and bookmarks, but it essentially is the same data for over 10 years.

---

### Post by Bucky Ball on 2017-08-24
I'll chime in with cloning the hard drive in Denmark to another disk (with Clonezilla or fsarchiver or something like them) and taking the cloned drive to wherever. Throw that in the other machine when you get there and nothing else to be done. For all intents and purposes, you'll be using the same machine, current and updated.

(You could also just pull the drive from the original and plop that in the second machine, but bit risky as no backup of the original drive/system.)

---

### Post by TheFu on 2017-08-24
> **Bucky Ball said:**
> I'll chime in with cloning the hard drive in Denmark to another disk (with Clonezilla or fsarchiver or something like them) and taking the cloned drive to wherever. Throw that in the other machine when you get there and nothing else to be done. For all intents and purposes, you'll be using the same machine, current and updated.

(You could also just pull the drive from the original and plop that in the second machine, but bit risky as no backup of the original drive/system.)

Be certain you bring the correct tools/screwdrivers if you intend to swap a drive. ;)  Once had a terrible time finding a null-modem cable and ended up having to build it instead of buy.  That was after a 45 min taxi ride across town to the 2 computer stores in a city of 4M people.  I could have brought the cable with me for about US$5 and a 10 min stop on my way somewhere else.  I have photos!

---

### Post by HermanAB on 2017-08-25
Well, the simplest solution is to buy a fast flash memory thingy, either SD number 6 or USB and install your system on that, then carry it with you.  It is so small, it will fit in your wallet.

Cloning a disk leaves a slight problem with the MAC addresses of the ethernet and WiFi adaptors that are different on the two machines.  I recommend that you figure out how to override those with something like 'ifconfig ether xxxxxxxx'.

---

