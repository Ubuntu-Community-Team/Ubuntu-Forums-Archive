---
title: "BIOS, LinuxBIOS, and GRUB. Please help me!"
date: 2006-12-18
forum: General Help
---

### Post by october1917 on 2006-12-18
One week before my Operating hd destroyed. So i uninstalled it and i created a new partition on my Slave hd (120GB WD) into which i installed Ubuntu 6.10. Unfortunately i forgotten the jamber to "slave" position and after that as expectable, it could boot only if the jamber was on the "slave" position.

I installed a second hd (250GB Western Digital too) in order to make a new installation. Unfortunately, it couldn't understand it.

I tried to connect the 2 disks in any possible way, changing the order of the hds on the cable, changing the jamber positions, or using the secondary IDE.

Depended to which way i installed the disks it returned something of the above:
* BIOS recognized the 250Gb but, the primary slave (120GB) appeared as "not installd"
or
* BIOS recognized the 120Gb but, the primary slave (250GB) appeared with incomprehensible characters (like chinese). This was corrected after clear cmos.

With all the connection ways, the pc couldn't boot, or just stopped everything displaying only the intel logo. Also the live CD tries to boot but it stops at the half of the loading process!!!!!

1) In your opinion, it could be the BIOS (which is at least 7 years old without upgrade) which blames for it?
2) If yes, is it a good idea to try linuxBIOS?
3) My estimation (which if it's correct it will extricate me from upgrade my BIOS) is that the problem is that both the hds have the GRUB installed, moreover that the 120GB hd has Linux installed while it had the jamber on the "slave" position. If it's possible i would like to indicate me how should i uninstall the GRUB from the 120GB disk.

Thank you.

---

### Post by scrooge_74 on 2006-12-18
I sometimes have problem with an old Pc I have at the office which is about 6 years old.  If I take the disks out and change the order or introduce a new disk the PC takes a long time to recognize them, I just put them on cable select option and let the BIOS sort it out after putting them on a different cables so each one is master and then the CD is the slave to any of them

I dont have experience with linuxBIOS

And I dont think Grub is responsable for your problems it is most likely the BIOS

---

### Post by october1917 on 2006-12-18
I tryied it too. Nothing happends.

---

### Post by scrooge_74 on 2006-12-18
try to boot the machine with only one disk as cable select? Maybe you can get it to recognize the disks one at a time

Have you ever change the internal battery of the motherboard? That have been an issuer for me in the past

---

### Post by october1917 on 2006-12-18
The 120gb disk boots if the jamber is alone in the slave position.
The 250gb disk boots if it is alone and there is no jamber (single or master)

I tried to install the disks one at time, but nothing happens.

I haven't ever change the battery, but i ininstalled it before, and reinstalled it after 15min, but again nothing.

What do you think about my supposal, (i mean that GRUB blames, which is installed in both of the disks)?

---

### Post by scrooge_74 on 2006-12-18
Ok, before letting the PC boot, does the bios recognize both disks? If you can manage to get the PC to see both  disk in BIOS then you should be able to use a live cd and boot from there and fix the GRUB.

Is the only thing I can come up with

---

### Post by october1917 on 2006-12-18
The only thing i wanna do, is just copy some files from the 120bg hd to the 250gb hd in order to format the the 120gb, and have it as deposit.

But in order to do this i first must be able to run Ubuntu (with both the disks installed), either from a hard disk, or from the Live CD. And as i said, if both disks are connected, the live CD doesn't load. It stocks at the half of the loading bar...

---

### Post by scrooge_74 on 2006-12-18
Try damn small linux, should boot, pick both  disk and let you move things and surf at the same time. It has done wonders for me in the past.

Then you can reinstall as you please

---

### Post by bulldog on 2006-12-18
You can have both disks as master on separate IDE ports,primary master and secondary master both connected to the end of the cable.

You can set one as primary master with the jumper on master at the end of the cable and set the second disk as slave with the jumper on slave at the middle connector of the cable,both on the primary IDE port.
So you can do with the secondary IDE port.

If your 250GB disk is fully recognized by the BIOS with all the GB's listed you have a special BIOS chip,most of the older chips don't recognize such large disks without an upgrade.

It helps to set them on auto in the BIOS so it can figure out for it self which one is the master and which the slave.

But GRUB has nothing to do with it that's something I'm pretty sure of.:D

---

### Post by october1917 on 2006-12-18
> But GRUB has nothing to do with it that's something I'm pretty sure ofOhhhhhhhhhh. That's not good. Actually i observed that:

If the 2 disks are connected to the same cable in ANY possible order, and with ANY jamber position, the Live CD stops while it creates the fstab file.

If the 120 is set to slave, than only 250 is recognizable from the bios.

If both are set to cable select then the image of the BIOS is the above ](*,)

Is there a possibility to have damaged IDE cable???

---

### Post by bulldog on 2006-12-18
Just try another cable and you know,but did you try to set them both as masters on separate IDE ports?
You have to use two cables of course and notice the jumper settings!!
If one of them fails again switch the cables to see if it fails again.
If it does there could be an issue with your IDE controller on the motherboard.

And you can try a BIOS update,got to the web page of the manufacturer of the motherboard and search for a newer one.
Download it and see for a flash.exe program arounf there,you'll need it.
Make a boot able floppy or cd-r and put this files on it.
There should be a Howto on the manufacturers web page for more information.

---

### Post by october1917 on 2006-12-18
> Just try another cable and you know,but did you try to set them both as masters on separate IDE ports?Yes. I've done it.

I'll try the above. I will make a changing between the cables. But the cables aren't the same. The one for the hds, has more dense fibres than the one for the CDs. Is it appropriate for this job?

---

### Post by october1917 on 2006-12-18
It seems that the primary IDE cable was damaged. I replaced it with the secondary IDE cable (wich is slower than the disk's one - is the one with the wide stripes) but it does its job.

Tommorow i'll buy a new one so that i can connect both the 2 disks and both the CD/DVD in order to verify that exactly there was the problem located.

Thank you all.

---

### Post by scrooge_74 on 2006-12-18
Can you connect them to different IDE cables?

---

