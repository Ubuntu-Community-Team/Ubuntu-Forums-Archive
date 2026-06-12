---
title: "Just updated, brightness control gone"
date: 2013-04-09
forum: General Help
---

### Post by Rob Sayer on 2013-04-09
Running kubuntu 12.04 on an acer d270 netbook with atom 2600/cedarview.  Just did a system update.

The kernel was updated to 3.2.0-40-generic-pae.

And I cannot change the screen brightness anymore!  I've had a lot of problems getting this thing to work with kubuntu and I'm not crazy about having to use the terminal again to change the screen brightness.  At least it recognizes the screen refresh rate which it wouldn't do at first.

Before I had to add the acpi_backlight=vendor argument to the grub config file to get brightness control, so I checked to see it if had been overwritten.  It's still there.
This is very frustrating.  My wireless is acting weird too.  That's another thread (literally).

---

### Post by Rob Sayer on 2013-04-10
Well, the wireless seems to be fixed (the tech support here is the best reason to use ubuntu IMO) but the brightness control still isn't working.

I had lightdm installed but I had stopped using it instead of kdm.  I removed it and rebooted it.  No joy.

When I updated the kernel during system update, muon update manager had asked me if I wanted to mark those changes.  I've done that in the past and had had no problem.  I think now that may have been a mistake.

So I'm thinking I may want to revert to the older kernel.  But I've never done that before and don't know  how.

Does this make sense?

Actually I tried the alpha 2 and beta versions of kubuntu 13.04 since the kernel has all the cedarview packages built into it as of 3.7 I believe.  That part definitely worked, but there were just too many other problems for me.  I don't have the linux recovery chops to deal with pre release versions.  So I downgraded to 12.04.  But I'll definitely upgrade when the official release comes out.

But in the interim, I'd really like my brightness control to work without having to open the terminal.

---

### Post by Rob Sayer on 2013-04-10
OK, did a little more research.  Found out how to show the grub menu on boot.

This has flustered me somewhat since it happened in the middle of trying to solve a wireless problem but that seems to be solved now.  I'm calming down.

So I just rebooted to the previous kernel version (3.2.0-39-generic-pae according to uname -r) and the brightness control still does not work.  Not through kde system settings->power management, or with the keyboard, both of which worked before I updated the kernel.  

Copying and pasting "sudo setpci -s "00:02.0" F4.B=30" terminal still works.  But it's a pain.

Any ideas?

---

### Post by Eightfire on 2013-04-10
I'm an owner of the same laptop, following this saga, Rob.  
I'm waiting for Ubuntu 13.04 final before putting Ubuntu or one of the lighter (LU, KU or XU) distros on.

You're saying that the newer 3.7+ kernel fixes the video issues, but without any sort of brightness control?
Is there a bug report for both problems?

---

### Post by Rob Sayer on 2013-04-11
The brightness/video etc worked fine in the 13.04 pre release versions I tried.  There were too many other problems for me.

I solved the problem in 12.04 by installing, then repeating the update process (both apt-get and muon updater) until I was sure there was nothing left.  Then, I installed the cedarview drivers through additional drivers.  Don't do this before updating or you'll lose your video.

The kernel support for the cedarview driver packages was moved into the 12.04 kernel, just not the one that comes with the install iso.

Until I updated the kernel a couple of days ago.

Filing a bug report doesn't sound like a bad idea actually.

---

### Post by Rob Sayer on 2013-04-12
I just tried to remove the three 3.2.0-40 kernel packages with synaptic and then update the grub file.

Synaptic said I have to fix or remove broken packages before it could proceed to remove them.

What is going on here?

---

### Post by Rob Sayer on 2013-04-14
So I tried:

sudo apt-get install -f 				

Didn't work.  I tried removing the newest kernel version through synaptic and it said it couldn't due to broken packages.

I went from mint kde back to kubuntu for the tech support.  Which I'm not getting on this issue.

I guess I'll have to resign myself to using the damn terminal to change the brightness until 13.04 is finished.

---

### Post by Eightfire on 2013-04-14
Compared to you, I'm a blind n00b.  I guess it's a matter now of waiting a couple weeks.

I'm going to try load up Precise Puppy Linux 5.5 from a USB stick.  It runs from memory.
Windows 7 Starter is pretty much an unusable OS.

---

### Post by Rob Sayer on 2013-04-15
OK, I've had some partial success with this.  Modified /etc/default/grub, to which I had previously added this parameter withi8n the quotes:

GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

to:

GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=vendor"

While it still no longer sets the brightness at boot to what I'd specified in kubuntu system settings-> power management, I can now change the brightness with the function keys.  Which is a lot better than opening a file and copying and pasting to the terminal and entering the password every time I changed brightness.

And having to do it again if I went away for a few minutes and the screen saver activated.

Since I doubt that I'm going to bother doing anything else as long as this works for the couple of weeks or so until 13.04 official comes out, I'm going to mark this as solved.

---

### Post by Rob Sayer on 2013-04-15
Which isn't appearing in thread tools.  Sigh.

Come on.  I just searched on how  to mark threads as solved.  The prefix doesn't appear when you edit.

This is not an improvement.

---

### Post by mörgæs on 2013-04-15
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by Rob Sayer on 2013-04-18
I'm supposed to edit the thread title?  How?

Nothing in that link on how to mark threads solved in the new forum format works.  This is a month after that stuff was posted.

Please change this forum back to the old format.  The new one is as bad as unity/compiz.

---

### Post by BlinkinCat on 2013-04-18
Hi,

Here is how to mark as solved for now...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

