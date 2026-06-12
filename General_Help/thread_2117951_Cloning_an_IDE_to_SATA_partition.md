---
title: "Cloning an IDE to SATA partition"
date: 2013-02-19
forum: General Help
---

### Post by mountainman70 on 2013-02-19
My old ide computer reached the end of it's life and I have a new (for me) sata computer now. It has an 80 gig HD and later I am going to upgrade to a 160 gig.
For now I have Wxp on it. I have used Gparted to make a partition of 40 gig for Ubuntu 12.04 on the 80 gig.
I have Ubuntu 12.04 on an IDE 80 gig HD that I am using as an external drive using a usb  IDE to SATA cable convertor.
Is there any way to just clone the IDE Ubuntu 12.04 to the 40 gig partition of the SATA HD?

Thanks for any replies.

---

### Post by Mark Phelps on 2013-02-20
I would suggest Clonezilla ... but it won't clone a larger partition to a smaller space, even if the partition is mostly empty.  IF you can get the space used in the original partition down to where it would fit on the other drive, you can then use Clonezilla.

---

### Post by aarons6 on 2013-02-20
yes and no.. 
you can user rsync to copy all the files to it.. but i wouldnt expect it to boot up the same as it did..

for this you have to install ubuntu on the new drive.

does your new computer have any ide ports?
if so you can just use both drives..

---

### Post by albandy on 2013-02-20
If your new disk is empty, you can do this:

Lets supose:
New disk: sda
old disk: sdb

Start with the ubuntu live cd and type:
sudo dd if=/dev/sdb of=/dev/sda

this should copy all the disk, maintaining uids. 

Now you have your disk cloned, open gparted and resize the partitions as you want.

---

### Post by auxilium on 2013-02-20
Hi,

You may try Ghost for Linux or G4L

You may put it to your pendrive and make your pendrive bootable.

Booting from your pendrive you can start cloning your HD

To make the pendrive bootable you may use Unetbootin




Cheers,

---

### Post by auxilium on 2013-02-20
Check this out, you may find it useful

[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

---

### Post by mountainman70 on 2013-02-20
> **Mark Phelps said:**
> I would suggest Clonezilla ... but it won't clone a larger partition to a smaller space, even if the partition is mostly empty.  IF you can get the space used in the original partition down to where it would fit on the other drive, you can then use Clonezilla.

Thanks to all who replied. 
I D/Led and burned Clonezilla to a cd. 
I then used Gparted to resize the external IDE usb ubuntu 12.04 HD to 34.25 gig making it smaller than the SATA partition.
I then rebooted with the Clonezilla cd and choose the IDE sdc1 as source and then choose the SATA sda2 as destination. After it finished I had a bootable clone copy of my IDE Ubuntu 12.04 with all my settings and programs on the SATA sda2 HD.

Am I right in assuming Clonezilla will clone the Wxp partition and the Ubuntu partition both to another HD?

Thanks for the help.

---

### Post by Mark Phelps on 2013-02-20
> **mountainman70 said:**
> Am I right in assuming Clonezilla will clone the Wxp partition and the Ubuntu partition both to another HD?

I haven't actually tried cloning multiple partitions one at a time, but Clonezilla does have the option to clone the disk -- ALL the partitions.

---

### Post by mountainman70 on 2013-02-20
> **Mark Phelps said:**
> I haven't actually tried cloning multiple partitions one at a time, but Clonezilla does have the option to clone the disk -- ALL the partitions.

I cloned the SATA HD to the external usb IDE HD but for some reason the IDE to SATA adapter will not let me choose on the IDE usb HD which OS I want to open. The linux screen with the windows option is there but the arrow keys will not move so I can only open Ubuntu. The windows partition is there and I can see the files but cannot open the os. So I guess it cloned ok.

---

### Post by orb9220 on 2013-02-20
I found [Redo Backup]("http://redobackup.org/") easier to clone whole disk or selected partitions.
Same under the hood engine as Clonezilla just a lot easier to use.
And can install the partitions back just fine as long as it is to same size or larger hardrive.
.

Did a complete Disk Win7,Winxp & 3 Ubuntu / /home swap partitions. And backed up to usb external. Then just backed up the 3 Linux partitions.

Now can install different distro and set those up install apps adjust settings then back those up also to external usb. 

Now can switch distro's on the fly in 20mins. Or restore my complete hardrive to a freshly installed new one if need arises.
.

---

### Post by mountainman70 on 2013-02-20
> **orb9220 said:**
> I found [Redo Backup]("http://redobackup.org/") easier to clone whole disk or selected partitions.
Same under the hood engine as Clonezilla just a lot easier to use.
And can install the partitions back just fine as long as it is to same size or larger hardrive.
.

Did a complete Disk Win7,Winxp & 3 Ubuntu / /home swap partitions. And backed up to usb external. Then just backed up the 3 Linux partitions.

Now can install different distro and set those up install apps adjust settings then back those up also to external usb. 

Now can switch distro's on the fly in 20mins. Or restore my complete hardrive to a freshly installed new one if need arises.
.

I tried Redo Backup but was not sure if I was doing it right. I've been reading the instructions and will try it again. But since I can not get the arrows to move to choose the Windows OS in the external IDE HD I not sure if it is cloneing right .

---

### Post by auxilium on 2013-02-20
You may also try Hiren's Boot CD

Its compact with many utilities, Gparted and G4L was also included. You may download the iso and burn it to cd or you may use it in you pendrive and boot on your pendrive

[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

---

### Post by orb9220 on 2013-02-20
> **mountainman70 said:**
> I tried Redo Backup but was not sure if I was doing it right. I've been reading the instructions and will try it again. But since I can not get the arrows to move to choose the Windows OS in the external IDE HD I not sure if it is cloneing right .

Yep steps are straight forward
Backing up.

1st window - is pick hardrive to backup. Usually first one
2nd window - Partition list click on which to backup all selectd by default
3rd window - Pick device to backup to. I always after browsing to location create a new folder with Distro name & date for folder name.
4th window - Is default name for backup file based on date. I leave that alone but can rename if you wish.
Click next and will backup depending on sizes of partitions can take 10mins or an hour.
.

---

