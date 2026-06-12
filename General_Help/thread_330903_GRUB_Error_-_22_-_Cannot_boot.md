---
title: "GRUB Error - 22 - Cannot boot"
date: 2007-01-03
forum: General Help
---

### Post by puterno on 2007-01-03
Long story short, I have one internal and one external hard drive. I have XP Pro on the internal, and 2 partitions. And I had the external for files, USB 2.0. I thought i would install Linux to see what it was about on the external so i made 2 extra partitions, one a SWAP (5GB) and one for the Linux core (ext3). 

I decided to get rid of it due to wireless problems, so I plainly wiped the partitions containing Linux (I merged the SWAP + Core into one NTFS partition.). 

So, I had XP and a file partition + a clean partition. 

I rebooted....     To find that GRUB still came up, and this time, gave an Error 22 code. I could not boot into XP. I unhooked the external which had linux on it, still the error came up. How did it migrate to the internal HD? OK... SO. I wiped my internal drive. Both partitions clean. Reinstalled windows XP... Restarted with Just the internal plugged in and nothing but the clean install. GRUB ERROR 22.  

SO... I figured BIOS or something? - So, I flashed the bios. GRUB ERROR 22. I then took the Hard drive to another computer, and still got the error. How is this possible?

I'm thinking the last resort is buying a new HD, and trashing this one. 

Thanks for any help you can provide in advance. Let me know if you need more information.

Internal: Samsung 80GB (65BG / 7 GB)(ntfs/fat32)
External: Samsung 250GB (170GB ntfs /5GB swap/65GB ext3 -> 170GB ntfs/ 70GB ntfs)

Overall, I wiped the entire internal, and all but the 170GB partition on the External. But i didn't have the external plugged in during the last reboot attempt.

---

### Post by Old Pink on 2007-01-03
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Ah Error 22. Never again shall you fool me. :rolleyes:

---

### Post by djsamsel on 2007-01-03
i would suggest googleing an iso called supergrub and using it to remove grub from your master boot record (mbr). you should be in good shape then.

---

### Post by puterno on 2007-01-04
OK, new problems. 

Made the CD image, went into supergrub, removed the GRUB/ and fixed the windows apparently. On boot up, it said. "NTLDR is misssing" instead of "ERROR 22" which is a nice change, but still bad. 

I fried one hard drive already :( - a 20GB pin broke.... sniff*. 


Let me know what i can do: My plan at the moment is:

Make 1 single partition.
Install XP
copy e:\i386\ntldr c:\
copy e:\i386\ntdetect.com c:\

let me know :P

Thanks for the help so far.

-Put

---

### Post by Old Pink on 2007-01-04
You should've followed my link, it's foolproof, your system becomes fully operational again in 5-10 minutes. 

Have no experience with supergrub, can't comment on your situation.

---

### Post by quartzy on 2007-01-04
I understand the problem is GRUB has setup shop in the MBR and isn't interested in leaving, rather than wanting to use GRUB as the boot manager you want to use windows? 

Can you do [this]("http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s05.html")?

---

### Post by puterno on 2007-01-05
Problem has been resolved. 

I re-soldered the pin to the 20 GB HD and it's working now as well. 

I had to wipe the Hard drive and then reinstall windows to restore the ntldr /mbr.

---

### Post by Jose Catre-Vandis on 2007-01-05
> **Old Pink said:**
> You should've followed my link, it's foolproof, your system becomes fully operational again in 5-10 minutes.

This is not always the case, I had a hardware issue (that wasn't immediately evident) too that caused error 22, had to unplug IDE1 to boot up then replug in on next cold boot to get the thing working properly

---

### Post by puterno on 2007-01-06
I hate following long instructions :P.
I'd rather screw around with formatting, etc until something works, then do it all over again next time i mess it up...
-P

---

