---
title: "Live CD boot problem w/Gateway M675 notebook"
date: 2004-12-12
forum: General Help
---

### Post by Vortical on 2004-12-12
(if this belongs in the LiveCD forum, mods/admins please move this thread)

Hello,

First, I have browsed and searched (albiet quickly) for an answer to this problem already.

I'm new to ubuntu and linux in general.  I have never used or installed anything other than Windows in my entire life, so please bear with my noobiness.

I'm trying to use the latest Ubuntu Warty 4.10 LiveCD to boot on my notebook.  My basic machine specs are:

2004 Gateway M675 notebook
3.0 ghz P4 CPU
1 gig PC3200 DDR SODIMM
ATI Radeon Mobility 9600 64mb vram
17" LCD Display (set to 32-bit color @ 1400x900 res.)
External USB 2.0 Hard-drive
Windows XP Home w/SP2
ACPI Management

The problem that I'm encountering is as follows.  I put the ubuntu liveCD into my DVD drive and restart my computer from Windows.  As the computer is restarting, it detects the ubuntu CD and brings up the LiveCD boot options screen.  Now, when I select the 'normal boot', everything appears to be fine and I eventually see a screen with the ubuntu logo and a progress bar below it.  When the progress indicated on the bar shows approximately 1/5th complete, the computer suddenly dies (as if it lost power immediately or something).  It does not restart, it just sits as if I had turned it off.

However, when I choose the 'fail-safe mode' from the LiveCD boot menu, this problem does not occur and ubuntu loads fully without any problems.

So my question is, what should I do to remedy this problem?

I have tried to come up with a list of things that I should focus on for troubleshooting this:

17" widescreen 1400x900 resolution is causing the problem
External USB 2.0 Hard-drive is causing the problem
ACPI is causing the problem

Now, I don't know what to DO about any of those things, but its what I have come up with.

I will VERY much appreciate any help/advice/info regarding my situation.  Thank you very much.

Tom

---

### Post by Vortical on 2004-12-14
Sorry if it is a forum foul to bump our own pust, but I have some updated info on my issue.

I tried the Knoppix 3.8 LiveCD for the first time after I grew tired of trying to get the ubuntu to load.  It also encountered a shutdown problem during bootup, however I have found the reason for it.

After searching on the Knoppix forums for awhile, I found some information that explained what was happening when I tried to boot with the Knoppix LiveCD.  It is my ACPI management that has to be disabled.  In the case of Knoppix Live CD, this can be performed with a simple command line option during bootup.  

So, since I still want to use ubuntu (it looks more appealing to me than Knoppix based on what I've read), does anyone know how to tell the ubuntu LiveCD to not use ACPI support?  Like I said, in Knoppix it was a simple command line option, is there something similiar I can do with ubuntu?  I never see a command line during bootup with ubuntu.

Once again, any help is greatly appreciated.

---

### Post by jdong on 2004-12-14
Ubuntu Live is MORPHIX, which is in turn a modified KNOPPIX. **noacpi, acpi=ht, acpi=off** are all acceptable ways of turning off ACPI.

---

### Post by Vortical on 2004-12-18
[QUOTE=jdong]Ubuntu Live is MORPHIX, which is in turn a modified KNOPPIX. **noacpi, acpi=ht, acpi=off** are all acceptable ways of turning off ACPI.[/QUOTE]

Okay thank you very much, however I don't know where during the Ubuntu LiveCD boot process to enter those commands.  Like I said before, I don't see a command prompt/console during boot.

---

### Post by smtanner on 2005-02-23
I have this laptop and it works fine with the hoary livecd and acpi enabled.  The problem is the thermal-zone acpi module.  Somewhere from kernel 2.6.4 to 2.6.9 this problem was fixed so using kernel 2.6.10 or later should work fine with your laptop.

---

