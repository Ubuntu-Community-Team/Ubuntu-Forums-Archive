---
title: "XP froze, Unclean shutdown, Grub error 18"
date: 2008-05-05
forum: General Help
---

### Post by LeoSolaris on 2008-05-05
OK here's the story. My girlfriend has a custom box her little brother put together years ago. I stuck Ubuntu on it for her a month or so ago, and till now, it was peachy.

The only reason Ann uses XP is for her shockwave downloaded games. (Not the Java ones that Ubuntu can play online.) I say this because she was in the middle of a game and all of the sudden XP completely froze. Nothing worked, Ctrl+Alt+Backspace, light push of the power button, mouse... total system lock up. So she did a forced power down.

That happens from time to time, so she didn't think much of it till she turned it back on. The first time grub gave her an error 18 (Out of range on the hard drive for BIOS) Every time after that first one, it simply drops me to the Grub command line.

I poked at it a little with knowledge gleaned from my books, but no joy, so I checked it with a LiveCD of Gutsy. The first time it froze mid-load at the Busybox, leaving me with a command line. Second time, I got it to load to desktop. (I'm figuring that was a fluke, but I may be wrong)

In the LiveCD I get what I had expected. XP is inaccessible because of the unclean shutdown, and the Ubuntu partition is just fine. I copied all of Ann's personal files over to her USB hard drive with only one issue arising, the last .avi refused to copy. It just kept adding time. I had to turn it off to force it to stop. I haven't had time yet to check to see if the rest of the copy actually copied.

I am at the point now where I can do complete reinstalls or a repair. What I need to know is what happened...  was this a hardware failure, or an attack on XP that tried to mess with the MBR where Grub is. I still don't understand why Grub suddenly could not access the Ubuntu partition after an XP crash. The part of Grub that is on the MBR is just fine, the commands work on the Bash-like line, but it keeps saying that the Ubuntu kernel is unreachable, and needs to be within the first 1024 cylinders of the hard drive. It was working just fine.

Before I do anything drastic, like remove XP entirely and grow Ubuntu's partition so the Kernel will be in the first 1024 cylenders, I would like a few opinions on this.

Is it a hardware failure? It seems to be just because of the new limit on kernel placement that wasn't needed before... but I do not know.

Help!
Leo

OK An Update:

I fired up Ann's desktop just a little bit ago with the LiveCD still in (I had forgotten about it last night apparently). I wanted the Grub terminal and to see the problem again, so I selected "boot from first hard drive" on the LiveCD. It dropped me straight into Grub Stage 2 (OS list) that it was adamantly refusing to go to last time with the Error 18. I selected XP. It started to boot, got the XP loading splash screen, and it went for quite a while, then froze again. I hard to do a forced shutdown. On restart I did get Grub stage 2, and this time I picked Ubuntu. It loaded fine, except for the automatic attempt to mount the XP partition, which in this case is to be expected because of the unclean shut downs. I am going to try to repair the XP partition, now that Grub is back. (Going to try shutting it down a few times and restarting, just to be sure)

Something that I forgot when I made this post... A couple of days ago, the computer started making an odd whining noise. Ann popped it open and dusted with some canned air. It worked for the rest of the day and the next till the incident described above. I mention this because when I fired up the computer today, it made the same noise as it started up. The noise stopped after Ubuntu fully loaded.

All in all so far, this has been extremely weird. A working computer shouldn't give errors like this, then suddenly just work again.

Update v2.0

Hmm  This has been really strange. After some the repair disc froze on me, I restarted into XP from the hard drive, and selected safe mode. After a hell of a long time, it finally did the check disk, and restarted. I rebooted once again to safe mode, and I got to the desktop. I poked around, and did a virus scan, then rebooted. This time it started normally and got to the desktop. I still have no earthly idea why or what happened. I did notice that Ubuntu started to freeze when I booted it, after all of this, but I tapped the side of the case without thinking and it continued instantly.

I have a couple of theories, and if none of them make a bit of sense, let me know...

1) Ann may have got a small drop of liquid on the hard drive's disc when she was blowing it out with canned air, and it just happened to hit it at that moment.
2) The hard drive is starting to fail. It is 6 years old after all.
3) Something on the motherboard glitched.
4) An attack on the system made it in and really screwed with something. (I still haven't found evidence of this yet, but it makes me nervous)
5) The computer is trying to evolve sentience.

Hopefully someone out there who knows more than I can shed some light on this disturbing event.

---

### Post by gsmanners on 2008-05-05
Try to find out where the noise is coming from, and I suspect that is what is causing the trouble. More than likely you have a bad power supply or a CPU/GPU fan that needs replacing.

---

### Post by Zorael on 2008-05-05
Not having heard of this issue before and hardly in a position to call myself an expert on the subject, I'd install **testdisk** when running in a live cd environment and have it try to recreate partition tables, just in case. The system would have to be rebooted after this.

Then I'd umount any partitions that may have been automatically mounted (in **/media/** when on the live cd, with **sudo umount *<directory>***), and forcefully check their file systems.

This command should output nothing if you've succeeded in unmounting everything.
```
$ mount | grep /dev/sd
```
To get an idea of what /dev/sdX partition is which, enter this to see your partition tables.
```
$ sudo fdisk -l
```

To proceed with the file system checks, do this.
```
$ sudo fsck -fM
```
-f should force a check, -M should limit it to non-mounted partitions. Checking a mounted file system *will* result in corruption.


If it ends up not scanning the XP partition somehow, just supply the /dev/sdX path to fsck to explicitly ask it to check it.

---

### Post by LeoSolaris on 2008-05-05
Thanks for the help guys!

Unfortunately, when I sat down just a few minutes ago to poke at her system, it froze on booting both XP and Ubuntu. At first it would not even recognize that the hard drive was there.  Makes me wonder if the hard drive is going. I am going to pop it open and check to see if the HD's cords came loose, then I will give test disk a shot.

While I have it open, I will listen to see if I can pinpoint the noise, too.

Leo

P.S I was curious and went to check out ventrilo. That will be nice once they get a client for Linux out. The server side is already there, but that is meaningless without a client to use it.

---

### Post by jimv on 2008-05-05
6 year old HD?  Problems booting both OS's?  Files not copying? Hard drive not recognized at times?  I'm fairly sure that the drive is dying.

I had a drive die not too long ago, and all kinds of weird things were happening.  Vista would boot, but hang right before logging in.  Ubuntu (live cd) would hang while trying to copy files off of that HD.  I put a new drive in, got rid of the old one, and everything was fine.

---

### Post by LeoSolaris on 2008-05-06
Yep, came to that conclusion myself when I just stopped this morning. I am starting to wonder about her motherboard though, apparently Ann replaced the HD just two years ago. A computer really shouldn't go through drives that fast, even if they are left on for weeks at a time. (I did recently break her of that habit at least.)

Maybe she did just get a cheap hard drive through...

Thanks guys! I usually sell computers before they give their death spasms, so this was a new experience. The desktops that i have had for long periods of time have all lasted intact for 5-6 years, but I did build them new, from top tier parts. I have no idea what quality hardware Ann's brother put in there. (Great guy, but a little on the cheap side.)

Leo

P.S. And I was really hoping that it was evolving!

---

