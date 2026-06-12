---
title: "Kubuntu/Ubuntu doesn't load after fresh install"
date: 2007-10-02
forum: General Help
---

### Post by PrimoTurbo on 2007-10-02
I have had this EXACT same problem before, it went away by itself after a few installs and partitions.

[http://ubuntuforums.org/showthread.php?t=539073](http://ubuntuforums.org/showthread.php?t=539073)
[http://ubuntuforums.org/showthread.php?t=428954](http://ubuntuforums.org/showthread.php?t=428954)

After I do a fresh install using official shipped CDs of Kubuntu, Ubuntu, or burned CDs including the Alternative CD, (K)ubuntu stops loading. All I see is a small orange bar and it just sits there. I tried installing about 5 times in total (after repartition and fixmbr) and I get the same problem, under recovery console the last line I see is the following:

**drivers/usb/input/hid-core.c: v2.6:USB HID core driver**

I tried unplugging all USB devices and disabling USB under BIOS but then I get.

**udevd-event[1926] : run_program: '/sbin/modprobe' abnormal exit**

I tried doing the check CD for errors and it find no problems.

Pentium 4 1.6Ghz
768 DDR RAM
ATI 9700 Pro 128Mb
Western Digital 250 GB
I replaced my AOpen DVD-RW to an LG one but have the same problem under both DVD drives...

I run Windows XP on a different partition of the same drive, it has no problems and I have done a chkdsk /r many times with no errors.

I have been able to install Ubuntu many times before on the same setup and the problem sometimes happens and other times doesn't. I tried different partition programs like partition magic and gparted, but it doesn't help. Diagnostic tools from Ultimate Boot Disk show no problems with my hardware or setup, everything works. Debian install fine, so does fedora. Is this a Ubuntu specific problem?...

[SIZE="4"]**_[COLOR="Red"]Please I really appreciate any suggestions or help.[/COLOR]_**[/SIZE]

---

### Post by por100pre1 on 2007-10-02
Maybe it is a hardware issue that affects Ubuntu somehow, maybe it is an Ubuntu issue. Try installing Gutsy, be sure to remove all usb devices and other hardware while you do so.

---

### Post by PrimoTurbo on 2007-10-02
No the error didn’t happen in Gutsy, but it’s still beta and there was quite a lot of unrelated problems.

After installing the restricted driver for my video card, the composite manager stopped working and I lost all the cool effects.

After installing all the required updates and rebooting, Gutsy completely broke and only allowed me to reselect the video card driver and restart, however each time I restarted it would force me to do it again and again.

LiveCD had some oddly scaled loading bars, also after install it didn’t add my Windows XP partition to GRUB….

Still very buggy, _**any more ideas about fixing Ubuntu under Feisty**_?....

---

### Post by PrimoTurbo on 2007-10-09
More ideas pls...

---

### Post by Zaph0d on 2007-10-15
Well, the good news is you're not alone.  I, too, am having this exact same issue.  Same presentation too - just kinda comes and goes.  I installed both Ubuntu and Kubuntu several times and it's worked like a champ, but it just decided to stop working with the same behaviour you reported.  Several clean reinstallation attempts to the same and different had drives and partitions have not made a change so far, but I suspect if I try at it hard enough it will eventually install a working copy again, just like you're experiencing.  It's important to note that NOTHING whatsoever changed between my last working install and the first non-working one - same computer, same hardware, same installation options, etc.  Nobody start with the "unplug this" and "reconfigure that" because it has all been tried and more importantly, it all worked as it was for a while. 

Unfourtunately, I don't have a solution to offer as I'm still trying to fix the issue myself.  I'm waiting for the 7.10 release candidate to finish downloading and will give that a try, but am not holding my breath for any difference.  When that fails, I'm going to continue ripping hardware that hasn't already been ripped just on the offhand chance that something i haven't already disconnected has decided to suddenly start acting the fool.  This really only ammounts to half my ram and removing my sata controller and usb2.0 PCI cards altogether - i've already tried disconnecting everything from the cards, but have not yet bothered pulling them altogether (mostly because an OS that isn't going to work with my CORE hardware is of no use or interest to me).  Again, not holding my breath but I will post any seemingly positive results if I get any.

Incidentally, the live CD's of K/Ubuntu boot fine, right to the desktop, with all my current hardware installed, enabled, connected, and working.  It's just when it's booting from HDD that it bites it.  Also, the live Knoppix 5.0 CD and DVD both boot to the desktop fine, but i haven't tried hard installing either yet.  That's plan B.

---

### Post by Zaph0d on 2007-10-15
Well, either I've got some shoe to eat or I just got lucky.  I'm posting this from a working install of kUbuntu 7.10rc.  Booted without a hitch - although I must say that's where the hitches end.  I hope the final 7.10 release is a little more polished.  But hey, it works!  That's progress in my books.

I'm gonna leave this in the "stop pickin' at it before it gets infected" pile for the time being.  Hopefully 7.10final will install alright in a couple days - I'll post an update.

Cheers for now.

---

