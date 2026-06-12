---
title: "Setting up a home NAS"
date: 2007-07-29
forum: General Help
---

### Post by yknivag on 2007-07-29
Having for some time now been frustrated at never being on the same PC as the file I need to access and also fast running out of room on some machines I've decided to set up a NAS. This will also form the backbone to a MythTV installation in due course.

Below is what I'm intending, but before I commit £300UKP to this project I'm after some opinions as to whether the following will work :o)

_Hardware_

Old PC (AMD K62-350 with 512MB RAM)
Motherboard has 2 IDE channels
100MB NIC
HighPoint 454 RocketRAID controller card (4channel) - NEW (~£65)
40GB IDE HDD (for system)
4x400GB IDE HDD (for data) - NEW (~£50/ea)
DVD RAM (for backups)

OS - Ubuntu Fiesty Fawn Server with Samba.

_Configuration_

This is where I'm having doubts. I've been using Linux for about 5 years now in various flavours and am fairly competent at the basics but I'm not an expert by any stretch of the imagination.

_Disk | Controller | Usage_

A | MB-IDE0-Pri | 40GB (system)
B | MB-IDE0- Sec | EMPTY
C | MB-IDE1-Pri | DVDRAM
D | MB-IDE1-Sec | EMPTY

E | RAID-IDE0-Pri | 400GB
F | RAID-IDE0-Sec | EMPTY
G | RAID-IDE1-Pri | 400GB
H | RAID-IDE1-Sec | EMPTY
I | RAID-IDE2-Pri | 400GB
J | RAID-IDE2-Sec | EMPTY
K | RAID-IDE3-Pri | 400GB
L | RAID-IDE3-Sec | EMPTY

Drive A would contain the local system:

/boot	250MB
/	25GB
/swap	5GB
/home	9GB

Drives E, G, I & K combined into 1 x 1200B RAID5 array and partitioned as follows:

/vhome	(to contain "samba shared" home directories for all users)
/servers	(storage for web and database servers)
/torrent	(dedicated partition for storing torrent downloads)
/nas	(large file storage and future space for MythTV)

_Conclusions_

This will leave me the option then of creating another seperate 1200GB RAID5 array with another 4x400GB disks on the currently empty F, H, J & L positions.

So, will this work? Has anyone tried something this big on such a small budget? The Highpoint card comes with Linux drivers, I'm in two minds as to whether to use the card to set up the RAID or simply to use Linux software RAID but I'll be running this from a very small processor.

I'd really appreciate peoples' thoughts...

---

### Post by yknivag on 2007-07-29
No thoughts anyone?

Will it work as described? Or am I being an idiot for trying?

Is there actually any benefit either way between using the "hardware" RAID on the card or the built in "software" RAID in the kernel?

Yours confused,

Gavin.

:confused:

---

### Post by dando80 on 2007-07-30
I would be more inclined to ditch the RAID cards and go with SW RAID on a faster system than a K62 350. You don't need to worry about losing a RAID card then.

---

### Post by yknivag on 2007-07-30
Thanks for you reply dando80. I'm still very much in two minds about which way to go woth the RAID.  The Highpoint card will allow me to do either (I'd need an IDE controller card *anyway* to get the necessary number of channels even for software RAID).

Whay kind of processor/memory would I be needing to look for to get software RAID to work effectively? How powerful does it need to be? (Or is that an answerless question?)

---

### Post by dando80 on 2007-07-31
From my limited experience with AMD K6-2, I wouldn't put much stock in them for performance. Then again you are going to be using 100Mb/s NICs so I guess blazing file serving performance isn't that important? It is a bit of a "how long is a bit of string" situation.

---

### Post by yknivag on 2007-07-31
Hmm, 100Mb/s NIC more than fast enough - this is an IDE solution not SCSI so the whole thing is limited by bus speed anyway.

I'm intruigued though by what I need in terms of processor power to make software RAID work.  The machine I'm intending to use has a 350MHz processor and several people have said it won't be fast enough, no-one seems to have a view on what *would* be fast enough.

Anyone have any suggestions as to what speed processor I'd need to make this scale of software RAID function under Linux?

---

### Post by fjgaude on 2007-08-02
Well, if all your data will be going down the 100Mb/s NIC, that's 12MB/s, I guess your CPU speed likely will keep up with it.

If you have a 33MHz PCI bus, and I don't know that you do, then software RAID will be just as fast as the Highpoint RAID card, I think.

I use software RAID5 with a throughput of 113MB/sec, but am using a fast box (AMD 64 2X 4400+ at 2.2GHz), and the throughput is limited by the PCI bus SATA controller.

I would think your CPU will be fast enough to support a read/write throughput of 12MB/sec. Give it a try with or without the new controller. If with, then compare the hardware with the software approach.

frank

---

### Post by yknivag on 2007-08-04
Hi Frank, thanks for the advice.

I need the highpoint card anyway to give me sufficient IDE channels to connect all the drives so I guess I can try both ways.

The MB has a 100Mhz bus so it's not going to be lightening fast either way.  I just don't want it sat at 100% CPU usage all day...

---

### Post by fjgaude on 2007-08-04
The Highpoint has its own CPU so your CPU usage will be way down to need nothing. Now if you use Linux software raid then it's your CPU that is hammered. <grin>

Let us know how things work out as you get everything in place.

frank

---

### Post by yknivag on 2007-09-20
Been a while wince I updated this thread.

Slight change of placn too, I've purchased a second hand Adaptec 2810SA SATA Hardware RAID card for an unbelievable price. Which means I'll not be buying the Highpoint.

As it's genuine hardware RAID and using SATA drives as opposed to IDE it should run a lot faster and allow me to utilise my existing hardware.

The card comes with manufacturer's drivers for RedHat and SuSe (kudos to Adaptec for supporting Linux) but I'd be interested to know if anyone has managed to get one running under Ubuntu (or any Debian release for that matter).

---

### Post by fjgaude on 2007-09-21
Since no one has replied, I'll point you in a direction: you can always convert RPMs to DEBs using the converter software that's available from the Ubuntu distro site using Synaptic or apt-get.

```
sudo -apt-get install alien
```

Now you can use it like:

```
alien -c mypackagefromadapteci-1.xxx.i386.rpm
```

And you should be there. You can do these before you do anything else, like buying SATA drives.

Good raiding,
frank
[http://yantrayoga.typepad.com/noname/](http://yantrayoga.typepad.com/noname/)

---

### Post by cbhatt on 2008-04-23
Hi all,
I'm looking to set up a NAS as well with a slightly different config with the Adaptec 2810SA. I will use 5 ports for a RAID 5 array, 1 for a hot spare, and the 2 remaining ports for a RAID 0 array for my MYTHTV backend.

Since there are no more posts here I assume that the 2810SA works with Ubuntu with no issues. Is that a safe assumption?

What did you do to get the card and arrays working under Ubuntu?

Thanks
-Chirag

---

### Post by fjgaude on 2008-04-23
Gosh, I just noticed your reply... use alien to convert the rpm file to deb. That should permit you to use the driver that Adaptec was so kind to write for Linux.

Again, let us know how you are doing.

---

