---
title: "kernel errors"
date: 2007-02-01
forum: General Help
---

### Post by rocketman768 on 2007-02-01
Hi all. I built a custom 2.6.18.6 kernel. It seems to work fine except for some complaints at boot up. Here they are (from dmesg):

[    0.136072] PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved
[    0.136109] PCI: Not using MMCONFIG.
[    0.165529] intel_rng: FWH not detected
[    0.166149] PCI: Failed to allocate mem resource #6:20000@50000000 for 0000:01:00.0

Are these bad, and if so, what are the causes? Thanks a million!

BTW...3.4 GHz Pentium D on an Intel board with PCI-express and SATA.

---

### Post by rocketman768 on 2007-02-01
Also, anybody finding Edgy more unstable than the last version? I have had several freezes in the past few weeks.

---

### Post by Quaker on 2007-02-08
Hi!!!, I have the same problem!!
I've looking around the www for the answer, but i haven't found nothing yet...
What i found is that the most affected computer are ASUS with intel processor and HP with intel processor....
And that problem aperead after the realease of the kernel 2.6.10

---

### Post by capink on 2007-02-11
saw this on another forum

# echo "blacklist intel_rng" >> /etc/modprobe.d/blacklist

[http://sidux.com/PNphpBB2-viewtopic-t-257-start-0.html]("http://sidux.com/PNphpBB2-viewtopic-t-257-start-0.html")

---

### Post by rocketman768 on 2007-03-10
This doesn't work for me. In fact, modprobe tells me that "intel_rng" is not a module (cannot be found).

---

### Post by rocketman768 on 2007-03-10
Ah, cuz intel_rng was compiled into the kernel instead of as a module. It was under a strange location in menuconfig tho: Device Drivers -> Character Devices. Ok, well at least I got rid of ONE of the lines of errors.

---

