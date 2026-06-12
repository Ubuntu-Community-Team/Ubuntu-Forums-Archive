---
title: "Ubuntu, Windows XP, GAG... boot problems"
date: 2007-02-11
forum: General Help
---

### Post by charish2k1 on 2007-02-11
I decided to get Ubuntu after watching countless videos of it combined with Beryl. So, here's the deal:

My IDE harddrive of 250GB has been partitioned.
My partition with Windows on it (the primary partition I suppose you could say) is about 179GB according to Partition Magic. The other partition is extended and contains my ext2 partition for Ubuntu set as the / (root). I have another partition (about 500MB) as my swap (1GB of RAM if that matters). Now, I went through the whole installation up until GRUB where for an hour I struggled to get it to install, but no matter where it went, it came up with an error.

After getting fed up of GRUB's refusal to install, I tried LiLo and got the same thing. I continued the installation without a boot loader. Immediately, I looked for something that might be able to replace GRUB and LiLo and I stumbled upon GAG. So I installed GAG and added my Windows OS and Ubuntu to the list; however, whenever I try to select my Ubuntu in GAG's boot menu, it comes with the message, "Sector boot invalid or not found." Now, I'm at a standstill.

Unfortunately, this is my first real exposure to as well as working with anything Linux-based. So sorry if the problem seems to be a bit vague. I've tried searching all over the web for anything remotely similar and tried all the suggestions that I could (which is how I stumbled on GAG), but cannot boot GAG. Any help would be *greatly* appreciated and hopefully as soon as possible. And in advance, thank you to whomever helps. :-)

---

### Post by louieb on 2007-02-11
Herman is regular contributor to this forum.  Check out his website, the Dual Boot link  in my signature.

---

### Post by charish2k1 on 2007-02-11
> GAG will boot Windows, but not Ubuntu. GAG will boot Ubuntu if either Lilo or GRUB is installed to the first sector of the Ubuntu partition or a /boot partition. Read my GAG page first. You'll find illustrated instructions on that page about what to choose in this step of the installation to set Ubuntu up for booting with GAG Boot Manager. This should be planned well beforehand though, it is not something you can decide in the middle of an install. You can also do it afterwards.

Alright, I think that's about the only solution that I can see that'll work for me. My only remaining question (hopefully) is how big does the /boot partition need to be? Or does it not really matter? Once again the set up for my computer as of right now...

Primary: NTFS, 179GB with Windows XP Pro SP2
Logical: Ext2 60GB Ubuntu (root)
Logical: Swap-space 500MB (swap)

---

### Post by confused57 on 2007-02-11
If you created & formatted your Ubuntu partitions using Partition Magic, that may be part of your problem...you really need to format your root partition as ext3, using the live cd partitioner during installation.

Don't worry about a separate /boot partition, if you want, you can use the live cd to install grub to the root partition:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

For example, if "find /boot/grub/stage1" shows root (hd0,1), then you would do "setup (hd0,1)", without the quotes, then type "quit" to exit grub as explained in the above link.

GAG should then be able to boot Ubuntu,  if it doesn't, then you may need to reinstall Ubuntu, using the installer cd to format your partitions.

If you want an excellent partitioning tool for Linux, look into the gparted live cd(30mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by charish2k1 on 2007-02-11
Yeah, I think Partition Magic is what screwed me, considering that's what I made my partitions from... so should I just wipe those partitions, remerge them with the physical and then through the Ubuntu installation do all the partitioning from there?

And also I can't exactly use that that thread, confused57, seeing as I can't boot into Ubuntu to go to the desktop and open the terminal >.>; I'm using the alternate install CD which only gives me the option of installing in CLI, text, or OEM.

---

### Post by confused57 on 2007-02-11
> **charish2k1 said:**
> Yeah, I think Partition Magic is what screwed me, considering that's what I made my partitions from... so should I just wipe those partitions, remerge them with the physical and then through the Ubuntu installation do all the partitioning from there?

And also I can't exactly use that that thread, confused57, seeing as I can't boot into Ubuntu to go to the desktop and open the terminal >.>; I'm using the alternate install CD which only gives me the option of installing in CLI, text, or OEM.

Here's a link with excellent screenshots for installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I think the easiest way would be to reinstall with the alternate cd, keeping the same partitions you have now, but selecting to format your root partition as ext3, using the alternate installer.
You shouldn't need to use Partition Magic to delete & remerge(would be a lot of unnecessary work).

Check out the link I gave you, make sure to select manual partitioning, format root as ext3, set the mountpoint as /, & setup your swap partition(formatted as swap & mounted as swap)...the alternate cd will do the rest...there's no guarantee this will all work, but it's worth trying.

Also, you might want to check out the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It can boot Windows or Linux, repair the mbr of both, great boot utility to have in your arsenal.

---

### Post by charish2k1 on 2007-02-11
I finally got it to work, lol; I just changed the partition where root was going to on to a ext3 instead of ext2... and I've already started messing around with it, getting media and stuff onto there. Now, just a few tie-up questions out of curiosity: 

1) Is there any sort of standard way to install new programs kind of like how Windows has its InstallShield or is it all done through the Terminal?
2) Are there any real good P2P programs for Ubuntu?
3) GAIM... is there a version for Ubuntu or must I grab another version that's for Fedora or live without it all together?
4) I have all my music on 1 hard drive... so I assume that I can make it a FAT32 so it can be read and written to by both Windows and Ubuntu? (it's an NTFS right now)
5) For WINE, do I have to get it off the Net or does Ubuntu have some sort of apt-get or other command to install it?
6) For those that have it, how difficult was it to install Beryl w/ Ubuntu and are there any little bugs during the installation that I should keep an eye out for?

EDIT: Also, GRUB works properly, making GAG obsolete alas. =D

---

### Post by K.Mandla on 2007-02-11
Just as a side note: I don't know if this will be helpful at all, or if it will just be a tacky self-aggrandizing link to a blog.

[http://kmandla.wordpress.com/2007/01/19/howto-install-gag-on-a-dual-boot-windows-ubuntu-box/](http://kmandla.wordpress.com/2007/01/19/howto-install-gag-on-a-dual-boot-windows-ubuntu-box/)

GAG needs Grub to be installed to a unique partition before it will work. For what I've seen, GAG passes the boot sequence to Grub, but can't boot without Grub. So perhaps GAG will still work for you if you want to give it a try. I like it; it has been worth trying, in my experience.

Anyways, sorry for the interruption. :rolleyes:

---

### Post by charish2k1 on 2007-02-11
Alright, I got another problem... I had Ubuntu running and after restarting it twice today (once to change my username and such from oem) and then a second time before switching back to Windows to do some gaming, I can't load into my Ubuntu; after selecting Ubuntu from the GRUB boot menu, it gets to the "Starting up..." screen and just hangs there. I get no error messages whatsoever so my apologies for not giving any exact problem >< I left it alone for 5 minutes before restarting into Windows and coming here. Does anyone know a possible fix to this?

EDIT: Sorry for not mentioning this earlier, but there was also a ton of upgrade packages that I had to download and such. So on the GRUB boot loader menu I got Ubuntu 6.10.11 and 6.10.10 each with their own recovery modes.

---

### Post by confused57 on 2007-02-11
> **charish2k1 said:**
> Alright, I got another problem... I had Ubuntu running and after restarting it twice today (once to change my username and such from oem) and then a second time before switching back to Windows to do some gaming, I can't load into my Ubuntu; after selecting Ubuntu from the GRUB boot menu, it gets to the "Starting up..." screen and just hangs there. I get no error messages whatsoever so my apologies for not giving any exact problem >< I left it alone for 5 minutes before restarting into Windows and coming here. Does anyone know a possible fix to this?

EDIT: Sorry for not mentioning this earlier, but there was also a ton of upgrade packages that I had to download and such. So on the GRUB boot loader menu I got Ubuntu 6.10.11 and 6.10.10 each with their own recovery modes.

Did you try pressing "arrow down" to boot the older kernel entry?  Your system may boot with the original older kernel that was installed.

---

### Post by charish2k1 on 2007-02-11
Yes, I've tried booting from the older kernel, I still get the same result. I was thinking of deleting it but I thought I'd leave it there just in case.

---

### Post by confused57 on 2007-02-12
> **charish2k1 said:**
> Yes, I've tried booting from the older kernel, I still get the same result. I was thinking of deleting it but I thought I'd leave it there just in case.

I don't know what your problem may be, but possibly something with one of the kernel updates...I've seen other people have problems with the new update, but it's usually been because of having nvidia modules that need updated.
You can reinstall grub with the alternate cd(don't know if it'll help):
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

I would recommend that you make a Super Grub Disk, that I gave you a link for in an earlier reply.  Having a linux live cd, possibly Knoppix or Ubuntu, would be a good idea to have when you may need to repair your system...you can even use Linux to recover data from Windows, in case of a crash.

You could try reinstalling Ubuntu, but there is no guarantee that it won't happen again...what I'd suggest is if you installed Edgy, try installing Dapper 6.06.1 instead(Dapper will be supported for longer than Edgy).

If you're interested in Beryl, you might want to look into Sabayon Linux, which is based on Gentoo.  This would require learning a little about Portage, the update manager used, instead of Synaptic(apt-get) package manager used by Ubuntu...they have a pretty good forum & you might want to check out the "Other OS Talk" in this forum(down near the bottom of the homepage).  Just something you might want to look into to see if you might be interested.

Added:  Here's someone who had a similar problem and reinstalling grub DID repair their Edgy installation:
[http://www.ubuntuforums.org/showthread.php?t=357965](http://www.ubuntuforums.org/showthread.php?t=357965)

---

