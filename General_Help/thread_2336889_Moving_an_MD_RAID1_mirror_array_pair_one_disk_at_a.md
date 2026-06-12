---
title: "Moving an MD RAID1 mirror array pair one disk at a time"
date: 2016-09-12
forum: General Help
---

### Post by aoakley on 2016-09-12
I have a Linux Software MD RAID1 array (pair of SATA drives, mirrored, EXT3) on another Linux system. The array holds data only, it is not bootable and does not hold OS files; the old system boots from flash memory.

I've built myself a new Ubuntu 16.04 Server with an SSD as the boot/root drive. Lovely.

I want to transfer the RAID1 array to the new server. I understand I can move both drives at the same time and then recreate the array with:

sudo mdadm --assemble --scan

My question is: Can I move the drives ONE AT A TIME, and if so how?

The data is valuable to me so I want to check it arrives okay on the new server, before I remove the second drive from the old server. I have backed up the most important data (family documents, photos and home videos) but the rest of the data is nearly 1TB and I cannot afford a backup solution for that (I am on a budget).

So ideally I'd like to move the first drive from the old server to the new server, boot up the new server and see my data on the RAID1 array with the second drive "missing", check a couple of files for confidence, and then add the second drive back into the array on the new server.

I'm hoping the answer will be "sudo mdadm --assemble --scan" again, and that it will handle the "missing" drive automagically, but I would appreciate any advice.

I've searched and found various articles on MDADM RAID migration, but none about doing the migration of RAID1 mirrors one drive at a time.

This is Ubuntu 16.04 Server with no desktop installed (commandline only). Many thanks.

---

