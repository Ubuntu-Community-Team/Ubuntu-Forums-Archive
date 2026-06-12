---
title: "What could affect XP on a separate hard drive?"
date: 2008-02-22
forum: General Help
---

### Post by SenseiDP on 2008-02-22
Hi all,

I have a dual-boot system with XP service pack 2 and Ubuntu 7.10.  I installed Ubuntu to my external HD just a few days ago, with XP unchanged on my lappy's main HD and for a while (2 days or so) both systems booted and ran fine.

Today, not so much.  I cannot get XP to work at all and have no idea why, or how Ubuntu, on a completely separate drive could have affected this.  When I choose to boot XP from GRUB, it seems to work fine, until I try to log in from the XP welcome screen, shortly after which I receive an error that scvhost.exe unexpectedly shut down, or Generic Host Process for Win32 Services unexpectedly shut down.  The only thing I am able to do from this point is do a hard shut down and try again.  Ubuntu still working fine, to my knowledge.

Also, Ubuntu no longer "sees" my main (NTFS) C: drive onto which XP is installed.  I tried to figure this out by booting Ubuntu in recovery mode and was prompted to force a mount of the drive, because it wasn't working properly, or something.  I don't think it worked because I still cannot access my C: drive from Ubuntu, and because I cannot get into XP, I can't get at it from there.

I installed Wine before I started having problems and have since uninstalled it, don't know if that would have any bearing on the issue.  I know this is very broad and quite vague but I am at a serious loss and am a little bit concerned.  Any help would be great.

Dan,

---

### Post by tact on 2008-02-22
Hi there.. others will likely be able to give you more detailed help.  Windows problems are not my strong suit  :)

I suspect you have a windowsXP problem    My wife's laptop is a winXP (exclusively - no dual boot) machine and she sometimes has exactly the problem you report.  Though on her machine usually she can click through the "scvhost" and "Generic host process" dialogs (they pop up one after another about 6 or 8 times) and then her PC works fine.

I did google around cos I thought svchost.exe might be a virus etc...  Just relating this so you know its nothing to do with your dual boot or ubuntu.  

The reflection of this you are seeing when you boot into ubuntu (you dont have to boot ubuntu in recovery mode unless ubuntu is broken)...  when ubuntu warns you that it cannot mount the XP partition unless you "force" it....  is caused by your "hard shutdown" when in winXP.   When you do not properly and gracefully shut down winXP the HDD is left with a "dirty" flag set.   When you try to mount a partition with the dirty flag set ubuntu will warn you.

You got a safe and a (maybe) risky option.
- safe...  boot back into windows and do a nice clean shutdown.  Then go into ubuntu and the partition will mount without warnings.
- (possibly) risky...  use the force option in ubuntu to mount the dirty partition.

If you decide to force mount the dirty you should have access - so long as you follow the instruction on the warning dialog.  Give more info what exactly you are doing and we can help get that sorted.

---

### Post by Crafty Kisses on 2008-02-22
That sounds like an Windows issue, I don't see as how Ubuntu could have caused this, as far as I know a lot of people have problems with svchost.exe, not sure why, maybe the Windows forums could help you. I don't think Ubuntu is the root of the problem.

---

### Post by NineseveN on 2008-02-23
It sounds like a Windows issue more than anything...I don't see how Ubuntu could do anything to affect your XP install. While XP is the most stable Windows OS ever IMHO, it can and will crash out on you for no apparent reason sometimes.  Even though it's rare, it still happens and it looks like you found yourself on the fuzzy side of lady luck.

---

### Post by dcstar on 2008-02-23
> **SenseiDP said:**
> 
..........
Also, Ubuntu no longer "sees" my main (NTFS) C: drive onto which XP is installed.  I tried to figure this out by booting Ubuntu in recovery mode and was prompted to force a mount of the drive, because it wasn't working properly, or something.  I don't think it worked because I still cannot access my C: drive from Ubuntu, and because I cannot get into XP, I can't get at it from there.

I installed Wine before I started having problems and have since uninstalled it, don't know if that would have any bearing on the issue.  I know this is very broad and quite vague but I am at a serious loss and am a little bit concerned.  Any help would be great.

Dan,

If you - for some reason - mounted your NTFS volume as "C" on your Ubuntu system, or pointed to it with Wine, then that could have caused your problems.

Otherwise something has corrupted your XP system, get the Windows disk and follow their recovery procedures.

---

### Post by tact on 2008-02-23
> **dcstar said:**
> If you - for some reason - mounted your NTFS volume as "C" on your Ubuntu system, or pointed to it with Wine, then that could have caused your problems.

Otherwise something has corrupted your XP system, get the Windows disk and follow their recovery procedures.

Bear in mind you (OP) would have had to do something to the NTFS partition while it was mounted or via wine to damage it (like delete/edit a windows config or system file, or do some operation on the file table etc).   

Just installing and uninstalling wine won't have hurt the NTFS partition alone.  Nor will mounting and unmounting the NTFS partition damage the partition.

And as I mentioned in my first post above:
-  my wife's XP-only laptop has the same problem from time to time.  It comes and goes.
- the message you get insde ubuntu about the NTFS partition needing to be force mounted is because XP was not shut down cleanly and that leaves the partition marked (by XP) as "dirty".

---

