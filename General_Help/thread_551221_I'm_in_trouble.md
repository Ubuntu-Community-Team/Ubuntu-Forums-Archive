---
title: "I'm in trouble"
date: 2007-09-14
forum: General Help
---

### Post by TheDon0369 on 2007-09-14
Hello everybody i have been reading on these forums for some time now but have never needed to become a member until now.  Here is my situation,  I had setup a dual boot xp and ubuntu install.  All was well until i accidentally installed backtrack 2 over my ubuntu install.  Now i cannot boot into backtrack or reach the grub boot screen to access ubuntu or my xp install.  Is my ubuntu install unrecoverable?  If it is, how can i get my computer to boot back into xp so i can format my ubuntu partition.  Right now it goes straight to backtrack and gives me errors and i can't boot the os.  Any help is greatly appreciated and i would like to thank everybody else here for being so helpful in general.

-Don

---

### Post by peabody on 2007-09-14
To get back into XP, you might be able to boot off of the XP CD and use the fixmbr and fixboot commands.  This will of course scrubb grub, or whatever else is there.

I don't know what backtrack is but it sounds like some kind of windows backup, imaging software?  If you installed it "over" the ubuntu partition as you say, more than likely your ubuntu install is toast, but that depends on what backtrack does.

---

### Post by rivalarrival on 2007-09-14
If your xp installation isn't hosed, you can get to it by booting from the XP installation disk, going to a recovery console, and doing "fixmbr" and "fixboot" - that should rewrite your master boot record and recreate ntldr (the thing that lets you choose which windows operating system you want to boot)

Doing this will allow you to boot to windows only. If you wanted to try to boot to ubuntu, you'll have to fix grub instead:
[http://ubuntuforums.org/showthread.php?t=210820](http://ubuntuforums.org/showthread.php?t=210820)

---

### Post by tgalati4 on 2007-09-14
Boot the Ubuntu Live CD and explore around.  Mount your drives and do some looking to see what's still intact.

---

### Post by init1 on 2007-09-14
> **peabody said:**
> To get back into XP, you might be able to boot off of the XP CD and use the fixmbr and fixboot commands.  This will of course scrubb grub, or whatever else is there.

I don't know what backtrack is but it sounds like some kind of windows backup, imaging software?  If you installed it "over" the ubuntu partition as you say, more than likely your ubuntu install is toast, but that depends on what backtrack does.
backtrack is a distro

You probably did destroy Ubuntu. But you will be able to boot Windows if you either fix the mbr, or reinstall grub and configure it for your needs.

---

### Post by Overbyte on 2007-09-14
> **peabody said:**
> I don't know what backtrack is but it sounds like some kind of windows backup, imaging software?

It's a linux distro.

[http://en.wikipedia.org/wiki/BackTrack](http://en.wikipedia.org/wiki/BackTrack)

Better do what tgalati4 says since you just installed over the OS, hopefully the data in the home directory is intact. Burn all critical data to CDs or to another hard drive (if you have one, the LiveCD has all the tools you need), then install xp, backtrack, and ubuntu to 3 separate partitions. A separate fat32 partition to store data is nice if you have the extra space because all OSs can read that partition. Hopefully, again :) the all-knowing GRand Unified Bootloader will recognize all 3 and when you reboot, you get a menu...nice and easy to go.

Darn how I still wish Ubuntu had the looks of openSUSE's boot menu :)

---

### Post by tgalati4 on 2007-09-15
I have a distro whore machine that uses the Fedora 7 boot loader (I think it's just a fancy GRUB) that has 4 distros + Windows.  So, if you really like SUSE, load it as the last distro and it's loader should pick up your previously-installed distros.  I'm not sure what loader openSUSE uses, but you are right, it's neat-looking.

I don't boot often, so I don't really care what the boot-loader looks like.  Although with some tweaks you can make GRUB fancy.

---

### Post by TheDon0369 on 2007-09-16
Yeah my Ubuntu got terminated.  I loaded the live cd, formated my ubuntu install and started all over.  Xp remained untouched.  Thanks for all the help.

Has anyone here got ubuntu and backtrack2 to work together?  It seems that backtrack 2 doesn't like the grub boot and ubuntu didn't like lilo.  I gave up trying to install backtrack and am just going to run it from the live cd.  Anyways, thanks for the help.

---

