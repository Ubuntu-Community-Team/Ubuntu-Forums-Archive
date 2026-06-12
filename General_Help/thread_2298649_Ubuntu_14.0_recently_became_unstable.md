---
title: "Ubuntu 14.0 recently became unstable"
date: 2015-10-12
forum: General Help
---

### Post by kzembower on 2015-10-12
I'm trying to fix a problem that just recently occurred. Over the last three months, my Ubuntu 14.04, on a homebuilt computer, has become increasing unstable. I've had 14.04 on this same hardware for a year or so, without problem. In the last three months, I've noticed these symptoms, with increasing frequency:
* Window with focus becomes 'grayed-out'. Mostly this was in the browser Firefox. I switched to Chromium, and this seems to have lessen the frequency, but not made it go away entirely.
* Icons on the left side of the screen disappear suddenly. When this happens, I'm usually able to click the close button to close all windows. The screen is blank, except for the orange background color. Sometimes, an empty frame appears, that reminds me of the frame around Firefox, with an 'address bar' at the top. Only option is to hard-reboot with the power switch.
* If I have a terminal window, or Emacs open, trying a command or exiting Emacs results in a message displayed that the file system is read-only, and I'm unable to save my work.

As I said, this is relatively recent, in the last three months, compared to the year or more that Ubuntu 14.04 ran on this hardware without a problem.

Could this be a symptom of a virus or malware infection? I know that this is pretty rare on a Linux system, and I'm behind a firewall on a DSL modem, but rare isn't the same a zero possibility.

Any advice or suggestions are appreciated.

-KevinZ

---

### Post by ian-weisser on 2015-10-12
> **kzembower said:**
> Only option is to hard-reboot with the power switch.
A kernel reset (RT-ALT+CTRL+SYSRQ+R+E+I+S+U+B) doesn't work? 


> **kzembower said:**
> message displayed that the file system is read-only, and I'm unable to save my work.
One symptom of a failing hard drive. Less likely (but also possible) are a failing power supply or motherboard.

---

### Post by efflandt on 2015-10-13
When that happens open a terminal (Ctrl+Alt+T) and do: **dmesg | less**
And look for any errors related to your hard drive (since logs in /var/log cannot be written to once remounted read-only).

When your system spontaneously remounts your partition(s) from read-write to read-only (to protect the drive) that is a sign of a failing drive. Normally a drive reserves space to remap good sectors in place of bad sectors transparently automatically regardless of OS. But when all of the error sites are used up and you start seeing bad sectors, that is a bad sign that things can only get worse. So if you have not backed up elsewhere what you want to save, do it now.

The 1 TB Seagate drive on my desktop purchased in 2010 began failing when it was about 3 years old, which I noticed when I suddenly did not have write permission (due to remounting read-only). My Linux partition at the far end of my drive began failing when I got into Steam and games started filling up my available space in that partition (where same amount of data is trying to store in physically smaller sectors). I managed to nurse it along for awhile by running e2fsck and/or marking out badblocks from a system on another drive. But when that started happening more frequently, I shrunk Win7 using its own Disk Management before imaging that to a new drive on an eSATA drive caddy, then swapped drives to reinstall Ubuntu on a larger partition, and copy over my home directory from the old drive. Just a few game files were corrupted and VERIFY INTEGRITY OF GAME CACHE... in steam replaced those files.

---

### Post by kzembower on 2015-10-16
@efflandt: Do errors like these indicate an immenant hard disk failure:

[41925.623038] ata1.00: status: { DRDY }
[41925.623038] ata1.00: failed command: READ FPDMA QUEUED
[41925.623040] ata1.00: cmd 60/00:68:00:2e:93/01:00:bc:00:00/40 tag 13 ncq 131072 in
[41925.623040]          res 40/00:5c:00:56:04/00:00:58:00:00/40 Emask 0x50 (ATA bus error)
[41925.623041] ata1.00: status: { DRDY }
[41925.623042] ata1.00: failed command: WRITE FPDMA QUEUED
[41925.623043] ata1.00: cmd 61/f0:70:78:a0:45/00:00:72:00:00/40 tag 14 ncq 122880 out
[41925.623043]          res 40/00:5c:00:56:04/00:00:58:00:00/40 Emask 0x50 (ATA bus error)

Because they're mentioning the SATA and ATA bus, I suspect that they might.

Thanks, again, for your advice. I wouldn't have thought of the hard disk right away.

-Kevin

---

