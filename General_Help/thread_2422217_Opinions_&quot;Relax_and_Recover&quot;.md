---
title: "Opinions: &quot;Relax and Recover&quot;"
date: 2019-07-03
forum: General Help
---

### Post by GhX6GZMB on 2019-07-03
[Lubuntu 19.04]

I'm looking for a backup solution that will allow me to make a full recovery (bootable) disk/DVD/USB device. A lot like the Win 10 system recovery.
I'd like to be able to reinstall the complete system with my preferences and settings as well as installed programs and my own data files.
In short: my HDD crashes, I buy a new one, and after booting from the recovery device everything is back as before.

DD is not really an option, why should I save a lot of empty space as well.

I found this: [http://relax-and-recover.org/](http://relax-and-recover.org/)

Does anyone have experience with / opinion about this solution?

Pointers to other solutions are also very welcome.

---

### Post by HermanAB on 2019-07-03
There are many ways to do it, ranging from super complicated, to super simple:
# cat /dev/sda > /dev/sdb

---

### Post by GhX6GZMB on 2019-07-03
Yeah, but that doesn't give me a bootable media that will bring my PC back to its original state.

---

### Post by cruzer001 on 2019-07-03
I like simple

[https://clonezilla.org/](https://clonezilla.org/)

---

### Post by poorguy on 2019-07-03
Perhaps this is what you are wanting.

[https://itsfoss.com/backup-restore-linux-timeshift/](https://itsfoss.com/backup-restore-linux-timeshift/)

---

### Post by Artim on 2019-07-03
The other above are all cool.  My favorite, being a technophobe, is called **SystemBack** and here are instructions for installing it:

[https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10](https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10)

---

### Post by HermanAB on 2019-07-03
"doesn't give me a bootable media"
It does, if the media is a USB stick, an SD card or a HDD - after a small manual tweak to fstab and mtab.

So, it does require some familiarity...

---

### Post by GhX6GZMB on 2019-07-04
@Artim:
Brilliant! Exactly what I was looking for.
I now have a USB stick that is bootable and also contains the whole system, my setups and personal files, plus Live boot and install. Great!
It's really sad that it's no longer being developed, but at it is, it does do exactly what it should.

Thank You.

---

### Post by Artim on 2019-07-05
[SIZE=6]Yaaaay![/SIZE] :popcorn:
 It doesn't need any further *development*, just a maintainer - and that's what the PPA maintainer is doing.  I like it better than Timeshift.  Something almost exactly like it *is* being maintained for MX-Linux, my *other* favorite distro.

---

### Post by TheFu on 2019-07-05
If this is solved, please help out the community and use the "thread tools" button near the top to mark it SOLVED.  That prevents people from wasting time.

---

### Post by GhX6GZMB on 2019-07-14
Unfortunately, I have to set this thread back to "unsolved"
SystemBack does indeed make a backup, but **restore** doesn't work... which kind of makes the whole exercise futile.

I'm now back to copying /etc and /home (including subdirectories) to an external drive, this is somewhat unsatisfactory, though.

You were all very friendly in suggesting things, but sort of leaving it at the point of "yeah, we're all professionals, let's see what the greenhorn finds out himself".
Could you please be a bit more specific?

Thank You.

---

### Post by Artim on 2019-07-14
Restore in Systemback is a *reinstall* from your newly created iso, if you like.  My backups (snapshots, if you do that) are stored on a separate drive.  How did you do yours?

---

### Post by rbmorse on 2019-07-14
Does Systemback handle UEFI installations?

---

### Post by Artim on 2019-07-15
[Here]("https://launchpad.net/systemback") is the project's web site.  I didn't find any info on UEFI installations, but I *assume* it does.

---

### Post by GhX6GZMB on 2019-07-15
The reinstall from a USB stick went fine when trying to restore. Some parts of the system were restored as well. But at some point a window popped up with non-functioning items and from there on everything stopped.
SystemBack is unfortunately not 100% reliable, and should I one day need to do the reinstall, I'll probably kill myself from frustration.
It might work well with older Lubuntu versions, but for 19.04 it's a no-go. I suspect there are issues recognizing LXQt.

---

### Post by TheFu on 2019-07-15
A backup tool shouldn't need to know anything except the file system and core Linux stuff.  GUIs shouldn't matter at all.

---

### Post by GhX6GZMB on 2019-07-15
I agree completely, but it's the only explanation I have so far.

---

### Post by GhX6GZMB on 2019-07-15
OK, found a solution, though still far away from the "**bootable USB backup stick that restores everything**".

I've installed TimeShift, which is a GUI on top of rsync, and it works tediously, but is wonderfully reliable.

To provoke a HDD crash, I did an rm -r /*

This killed my laptop within seconds (as expected).

A reboot with my installation DVD, followed by an install of TimeShift and a restore of my system brought it back 100% with all settings etc.

I can live with this.

Thanks to all.

---

### Post by TheFu on 2019-07-15
If you wanted something like that, **back-in-time** is a similar tool. I don't know if it is better or not. I used it on a relative's computer because that person was prone to accidentally deleting things.  B-i-T is a GUI to rsync+hardlink versioning, but hides all the rsync parts.  Like rsync, the target file system must be a Unix formatted file system, not NTFS or Fat-whatever.

---

### Post by GhX6GZMB on 2019-07-16
Yes, that was the only pitfall. The USB stick must be formatted to ext4 first.

---

