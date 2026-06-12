---
title: "Ubuntu 12.04 failing to boot: Grub rescue?"
date: 2014-05-30
forum: General Help
---

### Post by quark3 on 2014-05-30
Hey guys!

So, I booted up my PC this morning and got this:

```
Verifying DMI Pool Data ............ Update Success (I'm pretty sure this was my BIOS)
error: symbol not found: 'grub_unregister_command'.
grub rescue>
```

And it gives me a command prompt.
I tried tons of normal Linux commands (reboot, fsck, help, echo, shutdown, WHATTHEHELLISGOINGON) to no avail: I always got a command not found error.

So, I cut the power and turned my PC back on again. This time it hung at a purple screen with a few graphical glitches. Cut power.
I got the GRUB select OS screen and went for normal Ubuntu. I got a kernel panic (!), it was something to do with being out of sync, killing init, and a segfault.

Reboot again.

Grub screen. Ubuntu recovery. Hang at "loading ramdisk".

Reboot again.

Grub rescue, yet again. Same as the first one. I haven't been able to convince anything else to load, it's stuck on grub rescue no matter how many times I reboot.

So, I've tried the magic reseat, pulled out my graphics card (right now I'm using the integrated) and fiddled with my 2 HDDs (Both SATA connected, one has Ubuntu and the other has my home folder) but nothing seems to be working. Any ideas?

Am I gonna have to just reformat?

P.S A bit of extra info about my system:
Ubuntu 12.04 (Originally Mythbuntu 10, packages removed and ubuntu installed and updated)
ATI X1050 256MB (I've had problems with my graphics before (involving drivers and GNOME) but those were mostly fixed after installing LXDE as my desktop environment. Now OpenGL is my only real problem left.)
2 SATA HDDs (1. 50GB, contains Ubuntu. ext3 formatted. 2. 500GB, contains my home folder and a few QEMU images I've been playing with. I think it's FAT formatted for Samba.)

I'm not really sure how it happened, I let a friend play FTL last night and when I came back the PC was off and they were eating something. I didn't really think twice, but I'm gonna ring them and ask ASAP.

---

### Post by oldfred on 2014-05-30
Everytime you turn off power you may damage something, and that is what may have happened the previous night.

Best to remember the Elephants.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

And at grub> or grub rescue you are not at a full terminal, but just grub which has a few limited commands to try to boot.
      
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If files are corrupted you need a full fsck, which you have to do from a liveDVD or flash installer.
      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by quark3 on 2014-05-30
I tried to follow the thread on how to boot Ubuntu with the grub rescue, but i got a command not found on ls. (Oh, and boot). Is it time to just make a LiveCD and start fresh?

(Oh yeah, I'll try to fsck.)

---

