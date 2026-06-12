---
title: "/dev/sda and /dev/sdb keep switching after reboot"
date: 2008-03-26
forum: General Help
---

### Post by lobo235 on 2008-03-26
I initially installed Gutsy with only one 20GB IDE HDD connected to the motherboard. This HDD was recognized as /dev/sda. I then bought a Promise SATA card (non-RAID) and connected a 500GB SATA HDD to the card. Ubuntu recognized the controller card and the new SATA drive just fine as /dev/sdb.

The problem I am having now is that when I reboot the computer sometimes the devices are swapped so the IDE HDD becomes /dev/sdb and the SATA HDD becomes /dev/sda. I was having problems trying to mount the SATA HDD using it's device name because it kept changing so I figured out that I could use the **blkid** command to get the UUID for the device and I mounted the SATA HDD using it's UUID since that's how my main partition and the swap partition were mounted and it worked.

I would like to add another 500GB HDD soon and use **mdadm** to create a RAID1 array for backup purposes but from what I have read so far I will need the device names to be static in order to do this. To solve my problem I need to know if there is a way to use the UUID of devices with **mdadm** or if there is a way to keep the device names from switching like they have been doing. Any help will be greatly appreciated!

---

### Post by fjgaude on 2008-03-26
Well, from my limited experience with setting up software raid using mdadm I would say that as you make the array, i.e., --create it, the superblocks within the drives will be written so that mdadm will always know which drive goes where. It makes no difference if the drive name changes, sda becomes sdb and vice versa.

I do believe that Hardy, in beta now, seems to have stopped the name flipping. Gutsy using UUIDs stopped bad mounting and Feisty was open to error. So progress is being made.

No need to upgrade to Hardy just yet. I've moved four drives from an AMD computer to an Intel one and all I did, after installing mdadm, was to issue the command: sudo mdadm --assemble --scan. And the array was up and running. Now this is really "hog's heaven". <smile>

Let us know how you are doing when you add the next drive.

---

