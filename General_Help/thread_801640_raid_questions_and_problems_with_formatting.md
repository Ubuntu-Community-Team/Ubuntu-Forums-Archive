---
title: "raid questions and problems with formatting"
date: 2008-05-20
forum: General Help
---

### Post by rexxxlo on 2008-05-20
i recently purchased 2 wd 500 gb sata drives and wanted to experiment with raid
i figured that it would be easy but i was wrong 
first off i cant decide on weather to use fake raid software raid or some sort of hardware raid.

my motherboard has the ability to do raid on up to 4 sata drives from bios 
i set it up to use the two mentioned above, then i burned and tossed in the live 8.04 32 bit cd 
it booted up fine, i went to synaptec installed dmraid and followed this guide
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
it seems to work fine up until i get to the creating files systems area this code with the obvious change for my raid controllers name 

> mkfs -t ext3 /dev/mapper/via_hfciifae5
mkfs -t reiserfs /dev/mapper/via_hfciifae7


why is there a 5 and a 7 after the via_hfciifae??

are these the partitions number ?
i have 3 partitions just like the guide says 
i tried to format them with the partition editor but that seems to not work either 
i can format one or two of them but the third will not work and i get an error with that 

what am i doing wrong?

---

### Post by fjgaude on 2008-05-21
Are you using raid0 or raid1? You will not be able to boot from a raid0.

I gave up dmraid several years ago and use only mdadm now. It has worked just fine, but I use a separate boot drive and have all my data on a raid5 array. Has worked just fine over the years.

---

### Post by mrprefect on 2008-05-21
Most 'hardware RAID' available on mother boards and controller cards (unless you are paying a lot of money) are not true hardware RAIDs.

That being said I recommend using a software RAID. I have been using them for 5-6 years now and they work great. Sure they might be a bit slower then hardware but unless you are expecting a lot of high usage you will never notice this.

I've always found RAIDs very easy to set up and recommend using the mdadm raid tools.

Do not go with RAID0, this uses striping and if one of the drives fails the whole array is trashed. Stick with RAID1 or RAID5.

First fdisk the drives and set them to fd Type (raid autodetect)

then assemble the array with mdadm

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1

then format the raid

mke2fs -j /dev/md0

you can check the status of the build with

cat /proc/mdstat

now mount the array

mount /dev/md0 /mnt/mountpoint

*note: this is all off the top of my head so please double check the syntax and don't just copy pasta

---

### Post by rexxxlo on 2008-05-22
so why when i search about raid all the websites say software raid is horrible and hardware is the only way to go ?

but on here i get the exact opposite?

im looking for a performance increase and i have read that raid will help with that and im also looking for a reliability increase i hear raid will help with that too 

i will try the one you mentioned and see what happens until now im running off of one of my other drives so i can start from scratch and not have to worry about anything

---

