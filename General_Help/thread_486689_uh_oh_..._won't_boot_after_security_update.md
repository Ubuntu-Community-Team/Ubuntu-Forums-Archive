---
title: "uh oh ... won't boot after security update"
date: 2007-06-28
forum: General Help
---

### Post by ChrisC on 2007-06-28
Howdy folks -

I've been on Ubuntu for a couple years now, sticking to LTS releases so I'm currently running dapper, awaiting the next LTS release.  This morning the computer froze up, so I did a hard reboot, and now it doesn't seem to get past the mounting of the root partition.

I do get the grub menu so I know that the hard drive hardware seems to work.  If I let it go through the default entry (2.6.15-28-k7), it gives me the Ubuntu splash page and:

Loading essential drivers ... ok
Mounting root filesystem ...

... and that's where it usually hangs.  After a while it sometimes proceeds further to a text-mode screen that said "Reading files needed to boot ..." and hangs there.

If I select the "2.6.15-28-k7 recovery" option on the Grub menu, I get a text mode screen showing the drivers loading and drives mounting, and then it hangs with the following messages coming in very slowly:

[transcribed, not exact]
hda dma_timer_expiry: dma status = 0x61
hda dma timeout error status 0x23
device fault index error
opcode was unknown
dma disabled
ide0 reset success

and that continues with similar mesages for about a minute, then a big flurry of messages including fun terms like "I/O error" and "kernel panic".  Once it hung there after "kernel panic" and once it threw me into a BusyBox shell.

While I was composing this and I was rebooting it again to see what the messages were exactly, it actually sucessfully booted.  Yay, maybe I dodged a bullet!  So I immediately started to back up my files to DVDR, and halfway throug the DVDR write it froze, just like the original freeze that started all this.

I said in the subject of this post that it did this after security update, but that may be a red herring.  I did do a regular weekly security update a few days ago, but it did not include any kernel updates or anything else requiring a reboot, and it didn't ask me to reboot, so I didn't.  I just had to reboot this morning when it froze, so the update may have nothing to do with it.  Just thought I'd mention it.

Now, all this may simply indicate a hardware failure of the hard drive, but I've got 1:1 RAID on this machine.  And it's real hardware RAID (see arcoide.com) so there is absolutely zero drivers or OS involvement in it.  As far as the OS is concerned there's one drive, and there's one cable from the motherboard to the RAID assembly.  Further, when I boot it reads the Grub menu no problem, so I suspect a corrupted write that hit both drives, instead of a simultaneous hardware failure of both drives.

Note that my reboots are failing in a couple different ways, so I suspect perhaps flaky hardware or some weird corruption.  Every time I reboot I seem to be rolling the dice on what's going to happen.

Can anyone recommend any troubleshooting steps before I spend all weekend rebuilding this machine?  I'm not a fan of rebuilds, preferring to keep it down to just once every 5 years or so :)

My latest periodic (weekly) backup files exist in my home partition.  Assuming that partition is OK, and I've got the BusyBox shell, what exactly would I do to write those backup files (directories, actually) to DVDR, via command prompt commands?

Finally, note that my sig says I will pay for help.

Thanks!

- Chris

---

### Post by unklelar on 2007-06-28
Just wanted to say to you that the very same exact mofocking thing happened to me after an update yesterday. I've had Ubuntu 6.06 for about a year now without any problem. I am really pissed and find it disheartening that Ubuntu is  releasing  updates that are so destructive. 

I wish I could offer concrete suggestions to you, but I have no idea how to overcome this. I can't even get my live disk to boot. At least with windows, there are options to recover at least some valuable data. This is the kind of **** that drives people away from Linux.....and that now includes me.

Sorry to take away from your post.

---

### Post by ChrisC on 2007-06-28
Wow!  So is it really possible that a non-kernel security update caused this mess?

Ubuntu folks, I'll be happy to troubleshoot with you in order to isolate what may be a more widespread problem, but I need to hear from you ...

---

### Post by ChrisC on 2007-06-29
Anyone?

---

### Post by ChrisC on 2007-06-29
Anyone?

---

### Post by ChrisC on 2007-06-30
One more bump before I dismantle and rebuild this computer and hope the /home directory merge goes smoothly.  I wasn't planning on doing this kind of overhaul until the next LTS release ...

Help?

---

### Post by mummra1 on 2007-07-01
Yes!  I have the same problem after I did the update 3 days ago. Does anyone know how to remedy this??

---

### Post by ChrisC on 2007-07-01
Just following up in case someone else has a similar problem.  I dismantled the computer today and took the two redundant hard drives off the RAID controller and removed the controller.  I then hooked up just the primary HD and the boot problem remained exactly as before.  I hooked up just the secondary HD and the machine booted normally!  I quickly made a current backup of my files before continuing.

It could very well be that this was just a simple hard drive failure.  Both HDs were purchased and installed in Dec 2004, and the secondary actually failed just a couple months ago (and was immediately replaced).  So it looks like the primary just to a little longer to go down the same path.

The RAID controller was set to write to both HDs but READ only from the primary.  Apparently the primary was failing to read properly but the RAID controller didn't recognize this.  I downloaded Hitachi's drive test utility ("Drive Fitness Test", bootable CD ISO) and ran it on both drives and the primary HD failed pretty badly.  Lots of corrupted sectors, and it made the most godawful sounds when it was testing those sectors.

I've placed my order with NewEgg for a replacement hard drive, will arrive Tuesday ...

It's too bad that this RAID controller (ArcoIDE MicroRAID) can't read randomly from BOTH HDs and go ahead and fail over if one of them starts giving weird reads.  I had an older model RAID controller that did that.  If I get time this week I'll call them up and ask them about this.

So, anyway, the moral of the story for this audience (Ubuntu users/admins) is that this is what it looks like if you get corrupted sectors in your root partition.  I still think there might have been something weird with the last security update, but there were no responses to this thread so maybe not ...

---

### Post by ChrisC on 2007-07-01
Or just a couple responses ... Either the security update did cause this, or it's just a coincidence and it's actually the machine reboot that EXPOSED the fact that you'd had a root sector corruption happen since the last reboot.

---

