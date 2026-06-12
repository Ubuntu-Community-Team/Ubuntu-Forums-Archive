---
title: "dos-partition gone?"
date: 2008-02-13
forum: General Help
---

### Post by oui on 2008-02-13
bonjour

I did work yesterday morning in Puppy-Linux 4.0 alpha 6 frugal installation (starts like a live-CD) loged in my partition hda6 a ext2-partition for Kubuntu 7.10 remastered with KDE4 because Kubuntu don't work properly as user (Kopete has not the list of the messenger provider's in the user directory so it not possible to add any provider and to use Kopete so I help me with Puppy linux to contact my buddies). I can't remember what I exactly did but nothing happened any more, so that I did press my "I" interruptor to reset the system

after restart, I had to see that the PC was not rebootable any more:

- grub was away
- hda1 (20 Gbyte) (NTFS with Windows XP) was reduced to about 2 Gbyte
- hda2 (1 Gbyte) (Vfat) was away
- hda3 (30 Gbyte) (freeDos partition) was away
- only hda4 with within hd5 (SWAP) and hd6 (above Kubuntu) were intact.

today I did reinstall grub in MBR and change menu.lst

Kubuntu did start as usual and beginns with a check of the partition hda6 and show different messages concerning claims about hd1, hda2 and hda3. I did hoppe to find a text file with this message and look in tmp and var but I don't find the file with the error messages.

what can I do to save the error message and see them after the start?

what can I do to find the gone dos partitions?

salut

---

### Post by az on 2008-02-13
You can use Testdisk to restore your drive's partition table.  Stop using the drive until you can fix the partition table.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by oui on 2008-02-13
bonjour az

thank you for the link, it is really very interesting !

salut

---

