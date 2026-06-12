---
title: "Ubuntu Mate - unresponsive after fresh install on new hardware"
date: 2020-10-14
forum: General Help
---

### Post by macckos on 2020-10-14
Hello!

I had plenty of issues before I was able to install 18.04 Mate but I did it finally.
So it required removing NVME drive with win10 from Aorus B550 motherboard with 3700x CPU. Video comes from GTX660
I installed it on SATA SSD drive (on sata 2 port). I have 2 hdds on sata0 and sata1. Im rrunning on AMD AGESA ComboV2 1.0.0.2 BIOS

I created EFI partition, root, /home and swap (512MB, 30GB, 90GB and rest for swap on 128GB Drive). After succesfull installation I plugged in back my NVME SX8200 to M.2 port (PCIE-4).
Im finally able to change boot drive to this ssd, run grub, and login.
However after just few seconds im practically unable to click anything. I can hover mouse around and its sharp-responsive, but scrolling something, opening windows - impossible or takes forever to even click on menu and see icons inside.

I am able to run terminal and execute things, install things with apt-get, this seems responsive. 
Htop shows no load at all on anything.

I never experienced such issues, this happened for the first time to me on brand-new expensive machine (don't mind GTX660 - they said I have to wait 2 months for RTX3080).
I tried turning off fast boots, turning on IOMMUS, playing with idle current for cpu as these were most common things i found on the internet on "Freezing ubuntu" but none of that seems to work.
Can anyone help me with this?

---

### Post by TheFu on 2020-10-14
I had a similar issue with Ubuntu-Mate 20.04 on installation into a virtual machine with QXL video drivers. After patching everything, it got faster. Never figured out the exact issue.

```
sudo apt update
sudo apt dist-upgrade
```

I would be concerned trying to run 18.04 on a B550 motherboard.  Really new hardware like that needs the newest kernel line.  If you need to keep 18.04, install the HWE packages to get a more current kernel.

Since this seems to be GUI related, try creating a new userid, then logout and login using that new userid.  Is it still slow?  If it isn't, then there is some setting left over from the old, migrated, account, impacting GUI performance.  It becomes a trial and error problem to find which program, then which specific setting is the issue.  Were it me, I'd just mv ~/.config/ somewhere else and start with all new configs at my next login.

---

### Post by macckos on 2020-10-14
Thanks!
I've run full linux upgrade to 20.04 and issue seems to be gone! Finally!
This was a two days horror for me because I never had simillar issues!

I installed 18.04 because I haven't had tried removing nvme at 1st attempt to install 20.04 so i changed version to try something else. And I was a bit concerned because nvidia SDK manager was not supporting >18.04 verison two months ago... 
Basically it seems 18.04 is too old for B550 chipstet or ryzen 3000 ...
So I wiil write "googleable" thing at the end : ryzen 3000 b550 ubuntu freezing update kernel newer linux nvme drive mouse  :D :D

---

### Post by TheFu on 2020-10-14
I don't remember seeing anything specific to ryzen 3xxx CPUs causing issues with 18.04 or later.  I'm running a Ryzen 2600 on a B450 with 16.04 Server. I don't have NVMe storage, just a SATA SSD. No issues other than RAM speeds - had to slow the RAM from the 3200 Mhz RAM DOCP profile (same as XMP on Intel) to 2866 Mhz to get a stable system. 2933 Mhz wasn't stable and higher speeds for the RAM refused to boot.

I'm looking to build a new Ryzen server, probably one with 13,000 passmarks or faster in the next few months as a replacement for 2 other systems and a backup to the current server. Should be able to get the price under $250 total after the new Ryzens are out and available so the older ryzen CPU prices drop.  Would love to get a 2600 for $80.

---

