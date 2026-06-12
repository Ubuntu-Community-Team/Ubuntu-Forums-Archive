---
title: "Proper way to configure RAID1 in Ubuntu with Intel NUC"
date: 2020-06-07
forum: General Help
---

### Post by vv176 on 2020-06-07
Hey!


I’ve bought an Intel NUC and configured it with a 2.5” SATA SSD and a M2 SATA also, both with 1Tb, to be able to do RAID1.


I’ve read a lot about fake RAID with motherboard (using Intel Rapid Storage Technology) and the own software Linux RAID. I’m trying to choose the best and do it right, but a lot of questions arrive:

1. Firstly, trying to decide what method to use, seems like years ago is when fake RAID was working very badly. I read that today is very different. What do you think? Is it still better to use Linux software RAID?


2. I believe that using fake RAID, if the motherboard fails, you could lose all? That would be a big disadvantage.


3. Yesterday, I tried to install Ubuntu Server 20.04 and using software Linux RAID. I read that I must configure in BIOS AHCI, but with this option I can’t create the RAID later in the Ubuntu installer settings. So I had to choose RAID option in motherboard. Later. I was able to create the RAID in Ubuntu installer.
Doing at this way, I’m using now motherboard RAID or Linux? Is it bad that I didn’t choose AHCI?


I ask because I didn’t set the RAID thru the Intel RST dashboard, but not sure if having selected RAID instead of AHCI can bring problems.

4. When creating the RAID in Linux, if I check both disks, it says “no enough space or available space/volume for boot unit” or something like that. I read that I can use a USB stick to create the boot there, and that’s what I did.
It went well, but now I always need to have that USB plugged in to be able to start the server. Can’t this be done without have to use a USB?
I tried to make a little 512Mb partition in both SSD and format the rest of the space to use them for the RAId, but the “create RAID” option is disabled as soon as I create partitions. I only can do it if I leave the disks unpartitioned...

5. Is there any advantage of use that USB stick as boot loader? In case of a SSD failure or something like that? Not sure if one of a SSD fails if I’m able to boot it or I’d need an external boot like this USB stick.
Sorry for so many questions, but it’s a very complex process for a noob user.


Thank you in advance

---

