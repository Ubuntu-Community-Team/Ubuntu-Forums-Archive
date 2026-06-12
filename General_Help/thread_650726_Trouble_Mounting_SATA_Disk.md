---
title: "Trouble Mounting SATA Disk"
date: 2007-12-26
forum: General Help
---

### Post by ItsJweed on 2007-12-26
I got a 320 GB SATA hard drive for Christmas and just installed it in my 7.10 server today. My computer was old, so in order to connect it I had to also install a PCI RAID controller which also supports running SATA drives when not in RAID configuration. So the hard drive is connected through a PCI card. I'm having trouble mounting it. When I do a "fdisk -l" it doesn't show any drives. Obviously there is no mention of it in the fstab as well. Is there a command I can run to make it rescan my hardware and detect the PCI card I installed? I have a feeling if I just reinstalled the entire server it would work but that is a lot of work if there is an easier solution... Any ideas?

---

### Post by ijason on 2007-12-26
i'm running a pair of hard-drives via a cruddy compUSA pci/ata100 card... it sees it them both as serial hard-drives, without any need for weird mounting techniques. the only thing that i can suggest is reboot a few times and watch really sharply during your CMOS posting to see if the card is displaying the drives.

even my cheap-o card posts during boot, showing what drives are attached to it. you may have a pci slot that isn't working properly if you're not getting any post during the boot sequence. 

another option is that you have to use a bios menu on the controller card to enroll the hard-drives. it may say 'hit esc now to configure' or similar during your boot up. 

good luck!

---

### Post by ItsJweed on 2007-12-26
There is a way to enter its setup during the boot and I have. It shows the hard drive as connected and doesn't give me any other options. Yet when ubuntu (server) is booted it doesn't see the drive.

---

### Post by ijason on 2007-12-26
hmm, that is odd. :confused:

your fdisk -L doesn't show any different drives from having the new HD installed and not?

perhaps, try booting off a live-cd and see if it can see the HD without any further manipulation. i'm not familiar with the differences between the home/server versions of ubuntu, but surely that would eliminate install-specific problems with getting the drive to work

---

