---
title: "WARNING- Fixing XP Killed my Ubuntu Partition and MBR"
date: 2007-02-24
forum: General Help
---

### Post by JohnPhys on 2007-02-24
Hey all,

I'm not where this should go, but I thought I would post about it.

My WinXP Pro drive (sata, sda1) seems to be having bios issues, and totally crashed while I was in windows, and then wouldn't boot.  To try and recover the drive, I booted with the WinXP Pro CD, went to recovery mode, and ran chkdsk on the drive.  That may have been a newb mistake.

My Ubuntu (Dapper) is on hdc1, as is the mbr that boots my machine.  Apparently, windows assumed it was on (hd0) according to the motherboard.  I know winxp has issues while booting if it's not (hd0) (hence the swapping lines in grub for winxp boot), but I had no idea windows would try to read that file system and mbr when I ran chkdsk.

To make a long story short, when the chkdsk completed and I rebooted, my MBR *and* partition tables on hdc were gone, it seems windows just got rid of them.

Recovery proceedure was to boot Edgy live cd, enable universe repositories, apt-get install gpart, run gpart /dev/hdc (looks for lost partitions, it found them!), parted /dev/hdc, rescue partitions, grab grub boot cd, manually boot ubuntu from hdc1, then sudo grub-install.

I tried to reinstall grub to /dev/hdc multiple times from the livecd, and couldn't get it to stick.

Anyways, I just though I'd post, and ask where I might be able to post a more detailed how-to on this, in case someone makes the same mistake I did!

I should make a note that I did NOT type "fixmbr" while I was at the windows prompt, and was never prompted about that in any manner.

---

### Post by lwc on 2007-02-24
Hehe, that's not my flavor of multiple OSes. My way is here:

1. Install GAG in the MBR (easier to config than Grub, btw, my favourite SBMGR (a better alternative) cease to work in SATA drives :-( )
2. Install Grub on the Linux partition, not MBR.
3. Whenever Windows overwrites the MBR, overwrite it w/ the GAG floppy again.
4. Use a small disk partition program called BootIt NG (shareware). It is a self-contained boot floppy.

---

### Post by JohnPhys on 2007-02-24
What's GAG?

---

### Post by FuturePilot on 2007-02-24
If you loose Grub it's pretty easy to reinstall it.
1. Boot the live CD
2. Mount your Ubuntu partition (in Dapper you can do System>Administrator>Disks then find the correct partition put a "/" for the access path and click Activate)
3.
```
sudo /sbin/grub-install /dev/hda
```
or in your case hdc instead of hda

Reboot and everything should be back to normal

---

### Post by JohnPhys on 2007-02-24
Thanks FuturePilot, any idea where I could post a howto on this?  I'm not sure where that info should go anymore.

---

### Post by captainpotato on 2007-03-27
FuturePilot - you are right, it is easy to do, but is there any way to stop it happening in the first place? That's how I found this thread - searching for a way to stop it happening at all.

I'm having an issue with my laptop doing this with Win2000 on it, and I'm thinking of getting a PCMCIA-CF card adapter and putting GRUB on it, rather than the MBR, but I'd prefer to find a better solution than this.

---

