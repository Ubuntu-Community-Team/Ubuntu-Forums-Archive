---
title: "Adding a second HD to install Ubuntu - Is not working..."
date: 2008-05-04
forum: General Help
---

### Post by jcroot on 2008-05-04
Hi guys!

I'm trying to install a second hard drive to my PC in order to install Ubuntu 8.0.4 and I'm having some problems.

This is my situation:

I have a HP Pavilion a6120n PC

I want to add a second hard drive (160 Gbs) that I found in my room and this HD is in a good condition. I just want to add this second hard drive to my PC in order to install Ubuntu in a separate HD.

Right now I have Windows Vista in my PC so what I would like to have is a "dual boot" between both systems. My problem is that I can't add this second hard drive, my primary (windows vista) hard drive is using a SATA techonoly and the second hard drive that I want to use is using "PATA" or "ATA". The different are the cables, my primary hard drive (where windows  vista is installed) is in a SATA channel (same with my CD ROOM), but I do have a IDE Channel available in my mother board.

I don't know if I can use the second hard drive (PATA/ATA) with my motherboard and use the IDE channel.

I set the second HD jumper as "auto cable select" and is not working, when I try to boot my PC with Windows Vista I get a hardware error. I want to be able to see this second HD as slave when booting Windows Vista.

I'm confuse about how to setup this second HD and if I can use the IDE channel with this motherboard knowing that my primary HD is using a SATA technology. I was thinking probably my CD ROOM is setup as slave and that's why I can't make this second HD as slave.

I will appreaciate any help or manual.

---

### Post by Darkdelusions on 2008-05-04
I would set the IDE drive jumper to master and make sure the bio's is setup to read your vista drive fist

---

### Post by jcroot on 2008-05-04
> **Darkdelusions said:**
> I would set the IDE drive jumper to master and make sure the bio's is setup to read your vista drive fist

Thanks for your reply... If I set the IDE (second HD) jumper to master I will be able to boot Vista and see this HD as a slave?

I want to be able to see the second HD as slave first when booting Vista, and then change it to Master in order to install Ubuntu.

---

### Post by Fenris_rising on 2008-05-04
hi there
i did this yesterday. i have 1 80GB sata drive with ubuntu on it. ON IDE a 320GB HDD for storage and my original 80GB HDD store now has XP on it.
set cd rom to boot first. run the windows install locate your drive and install. at boot i can hit F8 to go into a boot select screen to choose which drive i want to boot from. else it boots straight to ubuntu. one thing i did notice on mine, when i added the 3rd drive i had to go back into bios and set the boot order up again. the only other thing i did was disconnect my other HDD whilst doing the install.

regards fenris.

---

### Post by Darkdelusions on 2008-05-04
> **jcroot said:**
> Thanks for your reply... If I set the IDE (second HD) jumper to master I will be able to boot Vista and see this HD as a slave?

I want to be able to see the second HD as slave first when booting Vista, and then change it to Master in order to install Ubuntu.

You should beable to see you drive (as long as it formated NTFS or any of its fatXX counterparts.)

---

### Post by jcroot on 2008-05-05
I set the second HD as master and make some boot order changes in my BIOS and now everything is working, I'm now able to see my second HD as slave.

I have some question about my second HD.

My second HD is formated in NTFS file system, I bought an external HD few months ago and it came formated in FAT32.

My question is: Why external Hard drives and USB Flash drives are formatted in FAT32?
Should I format my external HD (which use USB port) in NTFS file system or this will cause any problem? I asked this because the other day I was reading about the differences between NTFS and FAT32 and I see that NTFS is better.

I know if install Ubuntu in my second HD (not the external one) ubuntu will automatically format the HD in ext3

---

