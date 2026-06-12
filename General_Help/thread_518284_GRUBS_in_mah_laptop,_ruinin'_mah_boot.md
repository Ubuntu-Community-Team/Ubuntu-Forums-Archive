---
title: "GRUBS in mah laptop, ruinin' mah boot"
date: 2007-08-05
forum: General Help
---

### Post by nacho_newbs on 2007-08-05
Ok I am posting this in General only because there is no Forum for "CLASSIC NEWB F***UPS"

Get this:  I am having trouble getting the LiveCD to work on this old machine I am toying with.  I try the CD on my laptop and sure enough, it works fine and I can open unbuntu.  Then I get this great idea to install ubuntu (7.04) via my laptop onto the hard disk I plan on using for the old machine.  I have an external USB enclosure, so I put it in and Ubuntu can see it just fine.  So I set the installation to use the entire external disk for the main ext3 partition AND the swap partition.  Confident that there are no traces being left on my laptop I proceed.

WELL, since then I have found out that there is a tiny little advanced tab on the last screen of the installation setup wherein you can choose the location of GRUB, the default being of course the primary IDE drive.  So what I ended up with was an incomplete installation on the intended disk (which does not have a bootloader) and a partially installed (I think GRUB 1 and mebbe 1.5) GRUB that bravely tries to boot my laptop and gets unavoidably confused.

For the time being, I can boot through a SystemRescue CD and get into windows, but I'd like to get rid of that little GRUBBY monster.  Problem is, I can't even see it!  According to the diskpart the main partition begins after the first 30KB (which as far as I can tell are now claimed by GRUB).  

How the hell do I even try to get rid of this?  I'm not a complete newb, but here I am clueless.  Any ideas are greatly appreciated.

---

### Post by tgalati4 on 2007-08-05
GRUB is not a bug.  We normally reserve the term "bug" for a specific use as in: "I'm using Linux because it's working toward fixing Bug #1."

The GRand Unified Boot Loader is simply a tool to manage several boot configurations.  Yours happens to be screwed up.  A little reading on the subject (or searching these forums) will turn up a wealth of information on how to repair a GRUB installation so it works the way you expect it to.

Start with

>man grub

and 

>man grub-install

so that the repair procedures will make sense to you.

So you tried installing Feisty from a laptop onto an external USB drive, then took the drive out and installed it in a desktop machine?  And the desktop machine did not boot.  Sounds like you need to tell GRUB where your boot partition is located.

If this is an IDE drive in the first IDE channel and in the Master cable position, then hit "Esc" when in the GRUB menu and type:

root (HD0,0)

boot

And see what happens.

---

