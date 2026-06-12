---
title: "Weird Issue: CD Drive/Boot (Gutsy)"
date: 2008-01-20
forum: General Help
---

### Post by xOriginalNinjax on 2008-01-20
So, my CD drive went out, so I thought, and I went and bought a Memorex DVD burner.  After installing the NEW burner, the old one started working...and now the new one is unresponsive.  The other issue, I have to boot in failsafe to get anything up now...I can't boot in standard.  Any ideas?


unrelated issue:

For some reason, after booting Ubuntu (Gutsy) if I more than 1 program within 15 minutes after boot up, my computer freezes up, which is totally not cool.  I'm running a 2.1ghz AMD, and 1 gig of RAM, so I'm not entirely sure why it's doing this...unless Gutsy doesn't like my video card...or something.

---

### Post by xOriginalNinjax on 2008-01-20
bump?

---

### Post by torgrot on 2008-01-20
Is the DVD drive sata or ide?  If it is IDE how did you jumper it?  Master Slave or Cable Select?  It could be that you have two drives jumpered to Master or one drive is Cable Select and the other drive is Master or Slave.  If the IDE cable has three different color connectors on it, it is a cable select cable and you should jumper both drives as cable select.  If not, make one master and one slave.  If it is a sata drive, your on your own.

torgrot

---

### Post by xOriginalNinjax on 2008-01-20
IDE, and I'd assume jumper...wow...I thought I knew computers...haha.  It's a 2-color cable, blue and black...3 ends.  Blue end is in the m-board, black on the opposite end is in the new drive, black in the middle is in the new.  I also have the spot on the m-board used to be connected to, should I just run a 2nd IDE cable from that spot to the new drive, and leave the other hooked up to the old drive, or what?

I'm seriously shocked...I never knew there were other ways to do this...

---

### Post by xOriginalNinjax on 2008-01-21
bump?


I unplugged the new drive, and am still having the boot issue...so, now I'm REALLY stumped...and kinda peeved...I'm beginning to be half-tempted to go back to XP...as much as I love Ubuntu, Gutsy has not been agreeing with my computer...

wait...is there any way for me to do a quick revert back to Feisty?  Or revert back from an update?  My computer was running fine until the x-server update I had yesterday...

---

### Post by torgrot on 2008-01-21
That is a cable select cable.  You need to jumper both drives to Cable Select.  The drive connected to the end of the cable is the master and the one in the middle is the slave.  Go into bios after you have them connected correctly and choose auto detect for those drives.  Set the boot order to first boot off the CD/DVD drive that you made master(end of the cable)  Now put the liveCD in the drive connected to the end of the cable and try rebooting.
Let me know if you can boot the CD then.

One of the x-server updates the other day was seriously borked.  They pulled it and put out another which does work now.

torgrot

---

### Post by xOriginalNinjax on 2008-01-21
> **torgrot said:**
> That is a cable select cable.  You need to jumper both drives to Cable Select.  The drive connected to the end of the cable is the master and the one in the middle is the slave.  Go into bios after you have them connected correctly and choose auto detect for those drives.  Set the boot order to first boot off the CD/DVD drive that you made master(end of the cable)  Now put the liveCD in the drive connected to the end of the cable and try rebooting.
Let me know if you can boot the CD then.

One of the x-server updates the other day was seriously borked.  They pulled it and put out another which does work now.

torgrot

Ok.  I haven't had any issues from the CD...just from my hard drive install...unless I'm in GNOME Failsafe.  but let me go into BIOS and see if I can't get that setup...brb...

---

### Post by torgrot on 2008-01-21
Do you have more than one kernel in your grub menu?  If you do you could try loading one of the older kernels.  You might be able to get the current x-server updates that way.

torgrot

---

### Post by xOriginalNinjax on 2008-01-21
> **torgrot said:**
> Do you have more than one kernel in your grub menu?  If you do you could try loading one of the older kernels.  You might be able to get the current x-server updates that way.

torgrot

I didn't see any...but I can check again here shortly...


and I realized I can't boot any bios setups...USB keyboard...and I can't find my old PS2 keyboard...sunuva....ugh...

---

### Post by torgrot on 2008-01-22
Well if you can select the safe mode, you can select from the top menu bar 
System->Administration->Update Manager  then click on check, it will prompt you for your password and should show a list of update you can install.  One of which should be x-server something install all of the updates and reboot.

torgrot

---

### Post by xOriginalNinjax on 2008-01-22
> **torgrot said:**
> Well if you can select the safe mode, you can select from the top menu bar 
System->Administration->Update Manager  then click on check, it will prompt you for your password and should show a list of update you can install.  One of which should be x-server something install all of the updates and reboot.

torgrot

Then I already installed it.  I checked that.  It was running fine after the update, but then I rebooted to try to get my drive running, and it did a drive check, and hasn't ran right since...I don't know what the issue is any more...

---

### Post by torgrot on 2008-01-22
There were at least two x-server updates, the first was pulled when it became apparent that there was something wrong, about two days later another x-server update became available from the repos to fix what had gone wrong with the first one.  It sounds like you got the first one and maybe not the second one.  You need to do the check part again in order for the new versions in the repos to show up.  The changes wouldn't take effect until you restarted the x-server, which you did when you rebooted.

torgrot

---

### Post by xOriginalNinjax on 2008-01-22
> **torgrot said:**
> There were at least two x-server updates, the first was pulled when it became apparent that there was something wrong, about two days later another x-server update became available from the repos to fix what had gone wrong with the first one.  It sounds like you got the first one and maybe not the second one.  You need to do the check part again in order for the new versions in the repos to show up.  The changes wouldn't take effect until you restarted the x-server, which you did when you rebooted.

torgrot

The first one (about 4 days ago now, IIRC), woudln't even download from the server for me.  Then the new one came out, and it installed just fine yesterday.  I don't remember the other one disappearing from my list for sure though...is there anyway to go uninstall that package if it DID get installed alongside the new one?

---

### Post by torgrot on 2008-01-22
If you can recheck the updates in update manager and it isn't listed you have the right one.  You can get back to a default configuration by typing this into a terminal:
dpkg-reconfigure xserver-xorg

torgrot

---

### Post by xOriginalNinjax on 2008-01-23
Awesome, the boot issue is solved.


Now to see about the CD drive...



is there anyway to boot to BIOS with a USB keyboard?  Mine doesn't activate until the Ubuntu loading screen comes up...which sucks bad.

---

### Post by xOriginalNinjax on 2008-01-24
bump?

---

