---
title: "[SOLVED] Slow disk performance on i440BX"
date: 2007-08-05
forum: General Help
---

### Post by jb_ on 2007-08-05
Hey there.

I used to have a Celeron 500 machine with SiS chipset running Ubuntu 6.06 as a basic webserver. It had Apache, PHP etc.  I ended up with a P3 733 machine with an i440BX based mobo (Asus P2B-VM) and I had a spare 80gb IDE Seagate, so I decided the server was due for an upgrade, and it could also take on NAS duties after this.

I DD'd over the partitions onto the new drive, expanded them etc and fixed up the X config so I had a working X server, all was well. Only after I set up Samba and made some shares I noticed when copying to the machine over 100mbit LAN it would copy for a while, then drop to 0% (in windows networking monitor thing in task manager) then carry on after about 5 secs or so. I discovered that the hdd couldn't keep up and it was filling whatever buffer it has. hdparm -Tt was reporting about 9.50MB/s buffered read.

I didn't really know how to fix this so I got my Linux nerd friend to help (he works at a data centre, and has Ubuntu server on all their machines, so he knows what he's doing) and he's stumped too.

Here's a list of what we've done:

Upgraded to 6.10, then 7.04.
Tried about different 5 kernels from 2.6.15-23-386 through to 2.6.20-16-386 (I wont list them all)
Tried fiddling with the DMA modes and 16/32bit IO
Reset BIOS
Booted from live cd and re-run hdparm benchmark (to elimitate anything left over from the old SiS mobo)
And I tried a VIA PCI raid controller, but I couldn't get that to work.

Now I know the 440BX is a common chipset, so I have no idea why I would be getting awful transfer rates. Can anyone give me any suggestions?

Bare in mind I'm a bit of a Linux noob, so try to give good instructions, and hopefully I can answer any questions you may have.

Cheers.

---

### Post by fjgaude on 2007-08-05
How old is your disk drive, one, two, five years?

frank

---

### Post by jb_ on 2007-08-05
About 6 months. It has less than 3,000 hours on it.

---

### Post by jb_ on 2007-08-05
Ok never mind. It appears 32 bit IO was NOT turned on. I now get about 23MB/s second which is more than enough 100mbit ethernet.

---

### Post by fjgaude on 2007-08-05
Great, you can mark this issue solved, using Thread Tools menu at the top of your post.

frank

---

