---
title: "[SOLVED] Hard Drive Swap???"
date: 2008-02-25
forum: General Help
---

### Post by JimBuntu on 2008-02-25
Ok quick question. 

So I just recently got my new comp up and running in Ubuntu 7.10. I have my old PC that has an 80g Hard Drive in it. It had Ubuntu Studio installed on it. It is also IDE not SATA. Its really old from an HP. 

Can I just take the 80g out of the old comp and put it in the new comp with no problems? The one thing I am worried about is the two different sets of Ubuntu installed on each hard drive. How do I set this up? What if I put the new (old) hard drive in and it starts loading Ubuntu Studio when I restart the computer?

---

### Post by Mr. C. on 2008-02-25
As long as your hardware has an IDE interface and open port, and supports both IDE and SATA at the same time (which it likely does), all you need to do is connect the IDE drive to an existing open IDE cable connector (eg. you may already have and IDE CD/DVD drive).

PCs typically came with 2 IDE ports, each would could accomodate 2 IDE drives (one master, one slave).

You'll want your IDE HD to be a MASTER.  If you have only one IDE port, and have a CD/DVD drive on that cable, set the CD/DVD to SLAVE mode (jumper required most likely) and set the IDE HD to MASTER mode (again, jumper).  Cable select may be an option too - depends upon the IDE drives and the cable.

If you have the standard two IDE ports, place the HD as a master on the unused port.

Once connected, in your BIOS, configure it to boot only on the SATA devices.  Once booted, just partition the disk and set it as swap, and add with swapon or add the appropriate device to /etc/fstab.

MrC

---

### Post by mikewhatever on 2008-02-25
One way is to manually set the boot sequence in the bios, another, always boot from one of the HDDs, and add the second OS to GRUB of the first one. I think the second way is more convenient, so connect the HDD, boot into whatever boots up, and post the outputs of the following from terminal:
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map

Edit: Mr. C, I don't think the OP wants to create a swap partition, but rather connect another HDD. The thread title is, as usually, confusing.

---

### Post by soldats on 2008-02-25
Well it depends on how the old hdd will recognize the new computer devices. Theoretically if you just put your old hdd in and unplug the new one Ubuntu Studio *should* load up just fine. If so the order in which the hdds are set in the IDE cable will boot whatever is first. you should set the second hdd to slave and add the kernal lines to your /boot/grub/menu.lst file. after that grub should recognize each and give you the option to boot either one. all this should work if the older HDD boots up properly.

---

### Post by jeffus_il on 2008-02-25
It can be done but requires a certain level of expertise, a knowledge of grub, boot sectors, and an awareness of your disk partitions names, mounting, and the grub syntax and interaction with your disks. It will require booting the livecd and setting up grub and bios to boot from the disk with the grub menu in the boot sector and then to edit the grub menu with both systems, there are other possibilities like using your bios as a switch between two systems by changing the default boot order, or maybe using Supergrubdisk to set up grub. Are you ready to get involved?

---

### Post by Mr. C. on 2008-02-25
> **mikewhatever said:**
> Edit: Mr. C, I don't think the OP wants to create a swap partition, but rather connect another HDD. The thread title is, as usually, confusing.

Ah, it was the title "Hard Drive Swap???" !

MrC

---

### Post by JimBuntu on 2008-02-25
my new hard drive is set up using a sata cable. My old one only has IDE. The way I want to set it up is just to use the old as more storage space. I dont care about the Ubuntu Studio installed on it. I just want the data and the space, just like if it were an external hard drive. My old hard drive has jumpers for 'ma, sl, cs', what does the 'cs' mean? Can I just leave the the new one set up with the sata cable and change the jumper on the old one to 'sl' which means slave, and then just plug it in using the IDE cable? If so, what part of the IDE cable do I use? The master or the slave part?

Thanks guys, sorry for the weird title of this thread. still getting down the geek jargon.

---

### Post by JimBuntu on 2008-02-25
come on guys...

---

### Post by Mr. C. on 2008-02-25
> **JimBuntu said:**
> My old hard drive has jumpers for 'ma, sl, cs', what does the 'cs' mean?

I already indicated what they were: Master, Slave and Cable Select.

> **JimBuntu said:**
> 
Can I just leave the the new one set up with the sata cable and change the jumper on the old one to 'sl' which means slave, and then just plug it in using the IDE cable? If so, what part of the IDE cable do I use? The master or the slave part?

Yes, you can leave the SATA drive and cable alone.  They have no impact here.  Ignore that bus.

Since we can't see what type of IDE cable your new machine has (if any), or if you are using your old IDE cable from the previous machine, or if any devices are connected currently as IDE devices in your new machine, we can't answer that question for you.  You need to provide the data to us, as was hinted in my original posting.

How many IDE devices are in the new system?
How many IDE ports are in the new system?
Where is the IDE cable coming from (new system? old system?)
Does the cable have any indications or markings of CS or Cable Select on it?
If you have and IDE drive (eg. CD-ROM, DVD), what is the jumper set to on it?

MrC

---

### Post by JimBuntu on 2008-02-25
Sorry bro, I currently do not have anything set up with IDE. I have both my cd/dvd and HDD on sata. I have a new IDE cable that came with my new mobo, There is only one IDE port on my new mobo. I dont see any markings on the new cable except for the normal 'ATA33/66/100/133MB/s' . It has a master and a slave connector on it. My modo is an ABIT AN9 32x SLI if that helps any.

---

### Post by Mr. C. on 2008-02-25
Plug in the IDE drive into the master cable connector, set the master jump on the HD if it is not already set, plug the furthest end of the iDE cable into the MBO.  Plug in power to HD.  Boot.

---

### Post by JimBuntu on 2008-02-25
Ok, wouldn't I want to set the jumper on the old hdd to slave?? This is not going to be my master hdd. Also, is this going to wipe out all of my data on the old hdd?

---

### Post by Mr. C. on 2008-02-25
I am now entirely confused: perhaps stop using "old" and "new" nomenclature and use specifics like:

1: 80G IDE drive (to be used as scratch)
2: 200G SATA drive (w/ubuntu)
3: CD ROM IDE drive (master setting)

etc.

I thought your "new" comp had SATA as the main drive and Ubuntu was installed on it.  You clearly said "I currently do not have anything set up with IDE", so this implies your "new" comp's drive running Ubuntu is on the SATA bus (does not have the master/slave concept.)

If you have NO existing IDE drives, why do you believe setting this sole (80G) IDE drive drive to master is a conflict?

MrC

---

### Post by jeffus_il on 2008-02-25
> **JimBuntu said:**
> Ok, wouldn't I want to set the jumper on the old hdd to slave?? This is not going to be my master hdd. Also, is this going to wipe out all of my data on the old hdd?
Forget about the jumper, Leave it on CS (cable select) hook it up, just make sure that the first boot drive in the bios is the disk with the OS on it.

---

### Post by JimBuntu on 2008-02-25
very sorry, as you can see I only have 86 beans which implies that I am new to this computer game...

The reason why I thought that it might conflict is because of the word 'master'. I do not know how these IDE cables and other cables communicate with the motherboard. Perhaps it might be telling the motherboard that the IDE was the master drive to boot from since it is hooked up to the master port on the cable, and has the jumper set to master. Can you now see how a newbie would confuse this idea??

So what I am getting from all of this is:

1. Hook up the 80g IDE drive to the master portion of the IDE cable.
2. Plug the IDE cable into the motherboard.
3. Leave the jumper on the 80g drive set to master (not cable select). 
4. Plug in power and boot up.

Are my steps correct? Will I have to do anything in BIOS? Is there any downside to doing this as far as speed is concerned?

Thank you for your help.

---

### Post by Mr. C. on 2008-02-25
Excellent!

Your steps are correct.  You may be able to leave the jumper at cable select, but I have seen failures in this mode if the drive is not connected to the correct connector in the cable, or the cable is not a cable select cable.  If you have the jumper, set it to Master.

There will be no speed issue - IDE and SATA are two different buses and will not interfere.

Your BIOS is likely already set to boot from the SATA drive.  Just check to be sure that IDE drives are not set as boot devices before the SATA drive, and all should be fine.  Some newer BIOSes allow you to remove IDE devices as boot devices, so there's no issue.

MrC

---

### Post by JimBuntu on 2008-02-25
Ok, last question I promise. 

I dont have to worry about having Ubuntu already installed on this 80g right? It will just ignore it?

---

### Post by Mr. C. on 2008-02-25
"It" being the BIOS.  The BIOS will boot an OS only from the device(s) the BIOS is configured to attempt, and only in the order listed, trying the first, then if necessary the second, etc.

MrC

---

### Post by jeffus_il on 2008-02-25
```
very sorry, as you can see I only have 86 beans which implies that I am new to this computer game...

The reason why I thought that it might conflict is because of the word 'master'. I do not know how these IDE cables and other cables communicate with the motherboard. Perhaps it might be telling the motherboard that the IDE was the master drive to boot from since it is hooked up to the master port on the cable, and has the jumper set to master. Can you now see how a newbie would confuse this idea??
```

Don't worry about being a newbie, it like youth, it only happens once, enjoy it while it lasts, anyway without newbies, us "oldbees" wouldn't have a reason for being here, right?

---

### Post by mikewhatever on 2008-02-25
Jimbuntu, check this out --> [http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

Clearly defining your goals, so that those trying to help may understand and be effective in their efforts is very important.

---

### Post by JimBuntu on 2008-02-25
Great article. Clears things up...

So, I went ahead and installed the 80g hard drive, and started the system. I was greeted with the same error screen that I had already fixed when I first installed Gutsy. That told me that the comp was booting from the old 80g and not the 320g that was already installed and running perfect. I restarted and went to bios and changed the boot sequence to boot from the 320g first, saved changes to CMOS and exited. Restarted and there is was again, "error. try starting with 'noapic'." Finally I got the system to boot to the 320g with the 80g installed. I then copied all of my data and hoping the problem was fixed, I rebooted. "ERROR", it said. I just turned it off and took the 80g out. I tried to changed the BIOS settings, but it seems that everytime I went back in they were changed back to boot from the 80g. DAMN!! I dont know, maybe there is a step that I missed in the BIOS setup. Oh well, 320g is big enough for now. 

Hope this entire thread can help someone else.

Thanks guys for your help.

---

