---
title: "Installing new 500GB Sata HD"
date: 2008-01-23
forum: General Help
---

### Post by speed32219 on 2008-01-23
It's been 6 months since my last (ata 100) HD install on my video server with Edgy 6.1.   I now have a need to add another 500 GB HD but I have run out of IDE and I bought a Sata Western Digital dirve since I have 2 Sata ports on Asus MB.  Eventually going to go the USB route but have plenty of Physical HD storage avaiable.

So, I forgot how to mount a new drive and I have never done a Sata drive before.  Can some one give me the steps or point me to an HD installation document.  Any help would be greatly appreciated.

---

### Post by .nedberg on 2008-01-23
You need the device name (probably /dev/sde1 or something similar)

Then make the mount point
```

sudo mkdir /media/mountpoint

```
then you mount it with
```

sudo mount /dev/sde1 /media/mountpoint

```

adjust to fit your needs.

---

### Post by mohnkern on 2008-01-23
Once you've plugged in the drive go to the terminal window and type:

sudo fdisk -l

You should see your new drive now,  it will be /dev/sdX/  (X is some letter)

You can either use fdisk from the command line, or gparted if you have it installed to partition it.

After that, you'll need to put it in your /etc/fstab file to have it mount.

---

### Post by speed32219 on 2008-01-23
Thank you.  Finally got it installed.  I might be experiencing some problems though.  Not sure, but it seems as if I lose connection to it (Sata) sometimes.  Need to do some more testing and do some searching to see if there is a problem with combining IDE and Sata drives with Edgy 6.1.

But I am putting some movies on it right now. Time to watch the Big Screen. :popcorn:

---

### Post by mstephens on 2008-03-07
I am about to buy a 500GB drive for my 1998 vintage Compaq box which I  basically use as a file /media server. Everything works fine with its 30GB PATA drive at the moment. My understanding is that a 500GB drive will work fine under Ubuntu despite the fact that the BIOS may not like it provided I either partition it with a boot partition small enough for the BIOS to see it or with a single huge partition provided the Ubuntu boot stuff is at the start.

As SATA drives are cheaper(and more common)  than PATA ones,  I'm thinking about buying a SATA drive and a separate PCI SATA interface card. So my questions are:

a. Will Ubuntu (currently on 7.04) work with a SATA drive which is connected via an add-in interface card rather than a motherboard which supports SATA directly ? 

b The cards I have seen come with drivers for MS Windows. Does Ubuntu have the necessary drivers built in ? 

c. Assuming the answer to  a and b is yes, will I be able to use the SATA drive as a boot drive (i.e. take the existing drive out) or will I have to boot from the existing drive and mount the SATA drive as part of the startup ?

---

