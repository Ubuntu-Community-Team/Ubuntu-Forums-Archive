---
title: "Ubuntu 12.04 LTS Dual Boot to full installation"
date: 2014-01-19
forum: General Help
---

### Post by mpacey13 on 2014-01-19
Hey Ubuntu Community!

I'm currently on a Windows 7 / Ubuntu 12.04 LTS dual-boot setup on my laptop and absolutely loving Ubuntu! In fact Ubuntu has entirely taken all priority over Windows and having Windows now as a dual boot has become redundant, therefore I want to transfer from Dual Boot to a full installation, however I don't want to have to reinstall everything because of a full reinstallation.

So far I'm thinking removing windows 7 partition through Gparted and then transferring the empty partition space to my Ubuntu installation, however that magnitude of data would take a significant amount of time to shift over...

Is there a simpler way of doing this?

Cheers guys!
Raptus

---

### Post by Dave_L on 2014-01-19
How big are the current partitions and how are they arranged? Instead of moving partitions, you might be able to set up mount points or symbolic links to the reclaimed space.

---

### Post by mpacey13 on 2014-01-20
Currently all setup on one 1 TB HDD, Windows takes up exactly 512gb, Ubuntu takes up the rest.

---

### Post by Dave_L on 2014-01-20
So you have two primary partitions, each 512gb?

If you're not sure, you can view the information:

```
sudo parted -l
```

```
df -hT
```

---

### Post by grahammechanical on 2014-01-20
If you want my advice, I would

1) Wait until Ubuntu 14.04 was released at the end of April and fresh install that.
2) Create a partition to hold all data and copy the data over.
3) Shrink the Windows partition to 20 - 25 GB and install Ubuntu 14.04 into that.
4) Back up the data to DVD-RW disks
5) Expand the intended data partition as large as I could make it and copy the data on to it.

Reasons?

a) Ubuntu 14.04 has support for 5 years from May 2014 and there are many differences between 14.04 and 12.04 and upgrading sometimes breaks the installation. This is why many here recommend a fresh install, especially if we have heavily modified the desktop.

b) Keeping data on a separate partition puts it out of harm's way if we break the OS and need to re-install.

My final point is to reconsider this decision to remove Windows 7. Many do just that and then ask here for help on how to get Windows back because they need it for some reason. Once Windows is removed it is sometimes impossible to go back. Windows does not need all that space. Use Windows tools to defrag the partition. Do it 2 or 3 times. Then use Windows tools to resize the Windows partition. If you have already backed up the data to another partition then if the re-size operation breaks Windows you have not lost anything that you consider important. Have Windows recovery disks. And, after all, you have paid for Windows 7.

Regards.

---

### Post by dragonfly41 on 2014-01-20
I'll give you my pennyworth of opinion.

I have dual boot Ubuntu 12.04 & Vista on total 512 GB drive (laptop).   I also have external USB drives where other ubuntu installations can be tried out.

Most of my work is in Ubuntu and only occasionally do I use Windows.

But there are moments when you will find Windows useful .. perhaps you have to work on a file which is Windows only.   Only yesterday I visited a government sponsored providers site which had a questionnaire which only recognised Windows browser. Firefox on Ubuntu not recognised!

So personally I share the view that you should hang onto your Windows installation for a while if only as an insurance policy.   

I also share the view that you don't need 512 GB for Windows.   Perhaps shrink to 20-25 GB and in the free space install another partition for Ubuntu 13.04 as advised.   This would give you a "triple boot" (Windows + ubuntu 12.04 + ubuntu 13.04) to allow you to gradually migrate from 12.04 to 13.04 over time.   At some stage you can ditch 12.04.

I agree with other posts that you should create a partition for holding data and downloads.

---

### Post by mpacey13 on 2014-01-21
Yeah my uninstallation of Windows dual boot is in replacement of it being placed into a VirtualBox machine, I only ever use Windows either for Windows Games heavily dependant on DirectX or certain applications that could not be used on Ubuntu, thus it would be more convenient and quicker to access through a Virtual Machine.


However still deciding whether to wait till 14.04 is released or just go ahead with making it full. 

Edit: After some careful reading and research turns out Virtualbox's are run by virtual drivers this I would loose performance, however this is no great loss and a VirtualBox of Windows will still come in handy for particular windows based programs.

---

