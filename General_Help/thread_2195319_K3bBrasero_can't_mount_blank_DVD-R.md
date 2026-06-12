---
title: "K3b/Brasero can't mount blank DVD-R"
date: 2013-12-22
forum: General Help
---

### Post by r_avital on 2013-12-22
**Fresh installs** 13.10 64-bit on one machine, and 13.04 on another, both behave the same:

Any insertion of a blank DVD-R disk results in message "unable to mount DVD-R location already mounted."

Attempted the suggestions above: Booted with blank DVD-R in drive, opened up Brasero, attempted to burn ISO image - Brasero still insisted that I needed to put a different DVD-R in the drive.

K3B reacts the same way when trying to burn a DVD.  It will create an ISO image file just fine.  libdvdread4 and libdvdcss are install, so is transcode, probably not relevant to this problem, but thought I'd mention it.

**This was working perfectly fine in Lucid 10.04 for years, with the same batch of blank DVD-R disks, from the same cakebox, with the same hardware/dvd-drives.**

So now, Ubuntu has no way of burning a DVD?  Really?  

Well, sure, it's not the end of the world, but what's the excuse?  I'm now forced to run a Windows VM with other software that happily copies and burns all day long if I wanted it to.

Does anyone have a solution for this?

---

### Post by mc4man on 2013-12-22
I would think the "unable to mount DVD-R location already mounted" nonsense is just that & really shouldn't affect anything (with blank dvd/cd media
media is not mounted, the filesystem on it is & blank media obviously  has nothing to mount

In recent Ubuntu releases the message can be stopped by disabling "automount" in org.gnome.desktop.media-handling as in screen

Still that is just a message that can be ignored. Underneath the message by default is a window asking what to, choosing brasero here works fine, screen 2, scr.3 brasero populated

---

### Post by r_avital on 2013-12-22
Thank you, mc4man, 

I CANNOT get past that message:  In K3B, trying to either burn an ISO or copy a DVD, **the "Start" button is greyed out.  Same in Brasero.**  Otherwise, I'd be happy to ignore the message.  That's why I'm reverting to Windows VMs to burn DVDs.

I did go to System/Details/Removable Media, and made an entry for "Blank DVD" and set it to "Do nothing."  All that does, is prevent any "auto-run" attempts from the OS.  But the message still shows up.

I will definitely try your suggestion to disable automount in org.gnome.desktop.media-handling, as you said.  Once I do that, how will K3B or Brasero mount the blank DVD?

Thanks again :)

Update:  I just tried your suggestion.  Set all media-handling automount options (there are 3 of them) to false (unchecked).  Same behavior as before.

I would start suspecting the DVD drive itself, but we are talking about 4 different DVD drives - one on a laptop running 13.10, two on a desktop running 13.04, and one in a USB enclosure connecting to either one of them.  Could all 4 of them be bad?  Doubtful.

I gather you're getting your DVD drive(s) to actually burn a DVD under 13.10?

I should also add that I ran regionset on all these drives, all are set to region 1.

Thanks again.

---

### Post by oldos2er on 2013-12-23
I've moved these posts to their own thread since the original thread was for an older version of Ubuntu.

---

### Post by r_avital on 2013-12-27
Okay, I have just installed a completely different-make, brand-new DVD drive on the laptop.  Same exact behavior as before.

I would love to ignore the error/warning messages, but the problem is **the Start button in K3B, and the Burn button in Brasero, _*are greyed-out.*_  Can't start the burn process.**

This could not possibly be a hardware issue.

Both Brasero and K3B complain that the blank DVD is "too small" for the ISO image I'm trying to butn, which makes no sense at all, since both machines run Win-7 Ultimate as VMs, where a third-party paid app (DVDNextCopy) is happily burning the same ISO on the same blank DVD.  Again, this worked perfectly on both machines under Lucid 10.04.

Does anyone have this working?  And if so, how?

TIA.

---

