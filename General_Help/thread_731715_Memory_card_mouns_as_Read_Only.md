---
title: "Memory card mouns as Read Only"
date: 2008-03-22
forum: General Help
---

### Post by Lothas on 2008-03-22
This problem is driving me crazy!!! I bought a 2 GB micro SD card for my PDA phone and I'm reading it with a cheap usb card reader. For a while it worked ok but then one day, Windows Media Player stopped reading the music on the card because it says that it's read only. Whenever I try adding files to the card, Ubuntu says that I don't have permission to do it! I don't know what to do and I haven't found a useful solution on the forums.

P.S.: The micro SD card doesn't seem to have a write/protect switch...

---

### Post by nsche on 2008-03-28
Did you try [FONT="Fixedsys"]sudo mount -o remount,rw [device] [mountpoint][/FONT]

I think that will work.  I am not sure why it is being mounted ro initially.  Take a look at /etc/fstab to see if there is a clue there.

Good luck
Norm

---

### Post by OsakaWilson on 2008-04-21
How do I find the information that is supposed to go into the []?

---

### Post by Lothas on 2008-04-24
This is what I get from "mount":

/dev/sdc1 on /media/disk-1 type vfat (rw)

I tried the sudo mount -o remount thingy but it didn't help. This is showing some weird behaviour. Apparently some folders are write protected and some arent. I have 1 pendrive and 1 microSD card and they both behave differently... I'm baffled :(

---

