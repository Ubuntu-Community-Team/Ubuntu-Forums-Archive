---
title: "upgraded hardware now nothing works! beginner help me please!"
date: 2008-01-09
forum: General Help
---

### Post by fasthands on 2008-01-09
I folk's I am new to Ubuntu and I am impressed! well I was until I upgraded my pc! I am running Ubuntu 7.10, My pc build is as follows:- 
Msi 945GCM5-F ,motherboard, 
POWER COLOR X1950 PRO graphics card, 
INTEL CORE 2 DUO E4500 Processor, 
CORSAIR 2GB RAM KIT 2X 1GB,
And I have a Newlink PCI ATA133 RAID CONTROLLER CARD.
 MSI 52X CD-R/RW, 
And a e-ide dvd writer.
I have a Samsung 80Gig HDD plus I have added a Western Digital 320Gig HDD.
I turned on my pc I am running Ubuntu on the 80 Gig Hdd as this was running Ok until I upgraded to all the above. I have a Samsung 120Gig HDD I did want to run my pc on this HDD but when I installed it everything was ok then I installed the driver for my graphics card from Synaptic. then the pc would not boot up it got so far then just kept crashing! now I can't do anything with the 120Gig HDD. Luckily I had my old 80Gig HDD so I installed that and booted up I am using a restricted driver at the moment to run the graphics card. How do I install the driver for this Graphics card? without crashing my pc. 
Also my dvd and my cdr don't work, When I look in the BIOS the CDR-RW isn't on the list for boot sequence, but it shows up on my screen when I look in computer file browser! also in the file browser ther is cd-rom 1 and 2 what are these they were never there before! plus my WD 320HDD is not showing up in the file browser I thought it would plug n play. How wrong I was :lolflag:
I am really struggling now, and thinking of going back to windows, I am trying to learn about pc's  but I think I am out of my depth here, there is info on line about installing drivers and such but I don't know where to type the things that they say type in. 
can any one give me a fool's guide to sorting my pc I want to use Ubuntu. 
Many thanks, Mark

---

### Post by gwpritch on 2008-01-09
We could probably tackle each one of the hardware changes individually, but seems to me the quickest and easiest way to sort everything out is to do a fresh install with your new hardware. Running the live CD first will give you a better idea if there are any true hardware issues. If all is well, just reinstall.

---

### Post by kdwillia on 2008-01-09
As for the CD and the DVD not being in the Boot Sequence, we will need to know how the devices are connected to the PC.   If they are E-IDE devices, are you connecting them to the ATA133 RAID card?   Or are they connected to controller on the motherboard?   If they are connected to the RAID card, they will not show up in the System BIOS.   To boot from them, you will need select SCSI Boot as the first boot device (what the option says will depend on your boards BIOS).   

At any rate, the ATA card is going to have its own BIOS.   You will see it after your initial BIOS loads and before the O.S. starts to come up.  It should give you some keystroke that you will need to hit to get into its own BIOS.   Then you can look to see if it has the option to boot from CD first.

Actually.. alot of your problems could be the way that your new motherboard is configured and where your drives are plugged in at

---

### Post by fasthands on 2008-01-09
My DVD &CDR are connected to the Raid card, and my HDD are connected to the mother board.

---

### Post by kdwillia on 2008-01-09
Does your motherboard have two IDE connectors on it?

Having the CD & DVD connected to the RAID card does not provide any functional benefit to your setup.  Is the RAID card a new addition to your system, or a piece that was in your older system and you just brought it along for the ride when you built the new machine?

With 4 devices (all IDE or E-IDE) you can connect them without having to use the RAID card.   Each IDE cable should have 3 connectors on it.  One that goes into the motherboard and then two that connect to the devices.   As long as you have the master/slave settings correct on the devices, then all of them will be identified and the system will work accordingly.

If you really want to have the RAID card in the mix, then you probably want to switch the HDD's to it and the CD & DVD to the motherboard.   You still need to tell the motherboard BIOS that at some point, you are going to boot from the SCSI device (that is if the ATA RAID card is left in the machine)

Hope this info helps

---

### Post by fasthands on 2008-01-10
My mother board only has 1 ide slot, that is why I got the raid card, all the hardware I have listed is new, motherboard,graphics card,ram,raid card,processor,western digital HDD 320Gig,I dont have SATA hdd's so I thought I needed the raid card to be able to connect both my hdd's and my dvd,cdrw. I have downloaded the latest driver for the graphics card and tried to install it using this method,
sudo ./ati-driver-installer-8.443.1-x86.x86_64.run
I click allow executing fileas program in the permssions on the downloaded driver file.
all goes well but when the ati driver window comes up I click install, but the res on my screen is so big I can't see the bottom of the install window, and I can't scroll down either. I think there must be a start install button down there because nothing happens. but how do I start the install? I thought I was getting somewhere too. Windows is looming!:(:(:(

---

### Post by fasthands on 2008-01-11
I have found out that basically ati graphics cards are not compatable with Ubuntu, and if you do get them installed you don't get the full potential out of them. in particular the X1950
so I have returned the X1950, and I am going to order a Nvidia card and see where I get with that! But I am really starting to wonder if Ubuntu is all what it claims to be, it seems reading the fourum threads nothing really works correct at all!!:confused:

---

