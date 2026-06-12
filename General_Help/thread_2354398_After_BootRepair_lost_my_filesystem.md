---
title: "After BootRepair lost my filesystem"
date: 2017-03-02
forum: General Help
---

### Post by tehada on 2017-03-02
I had two Ubuntu on my computer 16.04 - my current system and old 14.04 which I used year before. Everybody has this day in their life when they decided to make some clean up... I already regret that I decided to delete my old OS using *BootRepair* and then *OSUninstaller*! It seems that two operation system used one filesystem or something similar because after uninstalling 14.04 my I  can't login as root in 16.04 in graphic mode, only guest session, although I can root using terminal. Right after that I do **ls** and it shows root directory (**bin/**, **etc/**, **dev/** and so on). In **home/** there is folder **deleted-os/ **and there is another root directory (**bin/**, **etc/**, **dev/, abhanak/**- my user's directory on 16.04, **home/tehada** - user's directory on 14.04 and others). So it is real chaos and I understand it. The question: is there any chance to leave 16.04 with only one user directory? Since my knowledge in architecture of filesystems is poor I cannot be sure that it so. I have no idea where to start digging to solve it. Log files does not provide me crucial information about my issue!

BootRepair generated this [http://paste2.org/M3cdJjBD](http://paste2.org/M3cdJjBD).

Edit1: [h=3]How can I make ubuntu to boot with filesystem in **home/deleted-os/**?[/h]

---

### Post by oldfred on 2017-03-02
Boot-Repair does no change to partitions.

It looks like you have a copy or old copy of grub in MBR from a BIOS install, but your system is UEFI and Ubuntu is installed in UEFI boot mode. Did you install Kali in BIOS mode? Grub will not install correctly in BIOS mode on gpt partitioned drive unless you also have a bios_grub partition. But better to be UEFI as all your other installs are UEFI.

Make sure you have UEFI on and choose to boot the ubuntu entry from UEFI.

---

### Post by tehada on 2017-03-02
Yes, Kali is installed, but mode I don't remember!

---

