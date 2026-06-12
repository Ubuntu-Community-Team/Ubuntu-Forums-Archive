---
title: "initramfs after &quot;unlock&quot; of locked SSD"
date: 2013-06-18
forum: General Help
---

### Post by cigtoxdoc on 2013-06-18
The Crucial M4 256 GB SSD on one of my secretary's PCs locked up after a momentary power failure last night.  I got the unlock procedure from a Crucial support tech, and SSD unlocked on first try using another PC with SATA drives, but boot into Ubuntu (generic 48) gave a whole bunch of gibberish ending with an initramfs prompt.  Entering help gave a whole list of commands without any explanation of what to do with them.  I repeated unlock procedure and moved SSD back to my secretary's PC and same initramfs error came up.  The SSD also has a Win XP Pro SP3 partition and it booted normally so drive is likely OK.

What to do next?  All production data are backed up on SpiderOak so worst case is to reload 12.04 64-bit.  My first choice of action would appear to be YannUbuntu's disk repair CD.  Is that likely a good choice or is there something better.  In laymen's terms, what has really happened?

Thank you,

John

---

### Post by cigtoxdoc on 2013-06-18
First, this problem likely would not have occurred if I had my secretary's PC on an UPS (now inistalled).  Second, if I had been doing frequent image backups, I would have been in a more secure position.  However, there is a happy ending.  I used another PC to download a copy of boot-repair-disk-64bit.iso, which I then burned to a CD-ROM.  I then used the boot-repair CD-ROM in advanced mode to reload GRUB.  I restarted PC from SSD using the Ubuntu partition.  Numerous lines of text appeared on the screen (probably telling me that I had displeased the gods of Ubuntu) and fiinally I did get the 12.04 login screen and was able to login in.  After checking the operation of mission-critical programs, I rebooted the PC and it booted correctly w/o warning messages.

If you are using SSD drives, and have PCs on UPS.  Always make sure you have recent images of your Ubuntu partition and off-site backup so that you can recover from a crash of a SSD.  The Crucial tech I spoke with was ready to send me a new SSD if I couldn't unlock the one I had.

John

---

### Post by zero2xiii on 2013-06-19
Hay,

I just wanted to suggest going that route, guess you found it yourself.

Please mark your thread as solved for other forum goers to see that is has been solved.

Thanks :)

---

