---
title: "How to uninstall Ubuntu?"
date: 2007-03-21
forum: General Help
---

### Post by GchadB on 2007-03-21
I have two hard drives. Windows on one, and ubuntu on the other... i want to format the ubuntu hdd to NTFS... how do i do this... i've been trying and searching for some help, and this is my last resort before buying a new one...
Is there a simple software program out there? i'd prefferably like to do it from wiindows...

Anybody? HELP!

---

### Post by MikeDX on 2007-03-21
Not sure why you'd want to do that, but you could always just boot up windows and from there, go to computer management and disk manager where you should be able to repartition your drive and format the drive as NTFS.

I'm not sure what grub will say about this though...

---

### Post by Juzz on 2007-03-21
So you don't want to run ubuntu anymore?

Do you have grub as bootloader now?
If not then it is rather simple to delete / reformat the partition - Start -> Run -> diskmgmt.msc

Then select the partition on the hd and choose format.

However if you have Grub as bootloader then you need to restore windows own bootloader brfore you do that...

---

### Post by profXavier on 2007-03-21
Sure, so as I understand, you have two HDs or maybe two partitions.

HDs are physical media that you put into your computer.  Then you can partition those disks into, you guess it, partitions.  Once you have a partition, you can do what you want with it, without affecting the other partitions, and each can have their own type.

Now, you can use Partition Magic, in Windows, to allow you to manager your hard drives and your partitions.

I could go on... but I am not sure how much you want to know.

---

### Post by GchadB on 2007-03-21
Well guys thanks for the suggestions, but i solved my problem.
I never thought to use my windows disc to do the formatting for me, but it eventually came to me and problem solved...

And MikeDX i wanted to remove Ubuntu from my system because the driver for my motherboard just got released and i was keen to install Vista, and i was just trying out Ubuntu... oh and when i installed ubuntu i didnt leave a big enough partition for Vista... oh and the Grub boot loader was just simply deleted...

Juzz take a tip from me, formatting the hdd that has grub saved on it deletes it totally.

Prof. im not that useless with computers, just with Linux... Im a "Linux Virgin" he he...

well thanks for all your suggetions. i've learnd a few things none the less, and i hope you guys have from me!

Luv ya all

Mwa Chad

---

