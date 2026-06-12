---
title: "Desktop PC halting due to non root ext4 partition being full. Best fix action?"
date: 2022-01-25
forum: General Help
---

### Post by ozark_hillbilly on 2022-01-25
Ubuntu 20.04 LTS 

Recently I started to receive a "memory full" error message running the Chrome Browser.
And then things became increasingly erratic with the operating system in general.
Eventually the OS crashed and now I am booting off a Live USBDrive.

If I try to boot off the hard drive it progresses to the point where the word UBUNTU is displayed
at the bottom of the screen and then the screen suddenly generates text that quickly scrolls off the top of the screen.
But two lines remain on the screen and they mention something about: 

journaling sdb6 

The text shows two memory byte values; used and available.
The used value is 99% of the available amount. Looking with gParted shows this ext4 (/dev/sdb6) partition to be completely full (30G).

The boot partition, on a separate drive, has nearly 200G of free space. Is the Linux OS trying to load data into the full ext4 partition
because it was setup to use that partition for such purposes? If so, how do I redirect the OS to use a different memory location?

What is the recommended path forward? 
I have data backups on both the two hard drives and a zip drive. I would rather not reformat if at all possible and the disk partition sdb5
has 30-40G free space I could resize down and apply to sdb6. I definitely would like the OS to start using more of the boot partition as it
has all that unused memory available.

Is all this "spinning my wheels" and I need to wipe the non boot drive? It checks out OK using the 'Disks' utility app and Smart Data & Self Tests.

p.s.  I did attempt changing partition sizes using gParted and left the process running and went to bed. This morning gParted showed no changes to the disk partitions.
       Not sure why that happened.

---

### Post by ozark_hillbilly on 2022-01-26
wiped drives...ugh

---

### Post by rsteinmetz70112 on 2022-01-27
Not sure what your second message means, but can you post the /etc/fstab to show where /dev/sd6a is getting mounted?

---

### Post by Impavidus on 2022-01-27
Sorry, I didn't see your message right away.

A boot partition in the most literal sense is a partition with the mountpoint /boot. They are used, have a particular purpose with storage methods that the bootloader can't deal with, but are normally smaller than 1GB. So I assume that's not what you mean.

Ubuntu stores files in whatever directory it was designed to do so. By assigning mountpoints to your partitions, you can decide which directory ends up on which partition.

---

