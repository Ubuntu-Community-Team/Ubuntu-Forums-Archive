---
title: "Upgrading to 15.04"
date: 2015-12-22
forum: General Help
---

### Post by Softa on 2015-12-22
I'm trying to upgrade to 15.04, and I just got this message...[ATTACH=CONFIG]266314[/ATTACH]
Can someone explain to me what I should do next?  Thanks

---

### Post by Vladlenin5000 on 2015-12-22
> **Softa said:**
> I'm trying to upgrade to 15.04, and I just got this message...[ATTACH=CONFIG]266314[/ATTACH]
Can someone explain to me what I should do next?  Thanks

No, it's pointless. Do your backups if you haven't already and install any currently supported release - 14.04 LTS or 15.10 (15.04 support will end in just a few days) - from scratch. Your system is in a state that strongly recommends AGAINST any attempt of online upgrade.

---

### Post by sideburns on 2015-12-23
Hello, there!  I'm the OP's brother and tech support guy.  Normally I don't like giving up that easily, and recently spent two days repairing an upgrade to my Fedora box using only a CLI because the upgrade munged the nVidia drivers.  However, this time you're right.  We've backed up the home folder, created a LiveUSB and tried to reboot.  I say "tried," because the options for shutdown and reboot were grayed out, and the commands were gone when I used a terminal.  We finally had to power-cycle, only to learn that the computer can't boot from USB, and the system's no longer bootable.  Now burning a DVD, and will report back if/when needed.  (I did keep a printout of /etc/fstab, so that I can get the mountpoints right.)

---

### Post by sideburns on 2015-12-23
I've burned a DVD and my sister booted from it.  It gave her the option to upgrade rather than reinstall, so we did that, because if it failed we could always do a new install.  As it happens, it wasn't needed.  Live and learn.

---

### Post by Vladlenin5000 on 2015-12-23
Great news :-)

---

### Post by sideburns on 2015-12-23
And, now we all know that a live USB/DVD can (sometimes) upgrade an unstable system leaving you with a working computer.  (I'd also suggest putting /home on its own partition, and making a copy of /etc/fstab before you start.)

---

### Post by QDR06VV9 on 2015-12-23
> [COLOR=#000000][INDENT](I'd also suggest putting /home on its own partition, and making a copy of /etc/fstab before you start.)
[/INDENT]
[/COLOR]

That is good advice:KS most of the old timers have preached this in every thread that was appropriate.
It is refreshing to see that it is now catching on..
Cheers and Kind Regards

---

### Post by sideburns on 2015-12-23
I've been doing it, now, for over a decade and when I helped my sister migrate to Linux, I made sure her box was properly set up.  Don't judge my experience by the number of posts I've made here; read my .sig.

---

