---
title: "trying to mount 4 raid array 0 drives...."
date: 2008-04-10
forum: General Help
---

### Post by dottedquad on 2008-04-10
Hello all, I have 4 raid array 0 IDE drives.  BIOS finds the drives with out any problem.  Next, I'm trying to figure out the command to see if linux found the drives.  Finally, I would like to mount the drives.  Could someone please help me mount the raided hard drives?

-Thanks,
     Rich

---

### Post by sdennie on 2008-04-10
Are you using software or hardware RAID?  If you are using software RAID and set the RAID up in Windows, I think you are probably out of luck seeing them as a single device under linux.  If you are using hardware RAID, it will depend on what RAID controller you are using.  Some RAID controllers will just make the array appear as a single disk while others are more complicated.  [http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html) might be a good place to start.

---

### Post by fjgaude on 2008-04-10
If your four drives were created in the BIOS as fakeraid, the program **dmraid** can be used to see the drives as one, as a raid0, if that is how there were setup.

You will have to install dmraid in Ubuntu and then use the **man dmraid** to understand how to use the program.

Now if your have hardware raid, you will need to have a driver supplied by the manufacturer of the raid card that works with Linux.

Let us now how you are doing.

---

### Post by dottedquad on 2008-04-10
By hardware you mean: using a hardware such as a card plugged into a PCI slot?  If so, I'm using a card plugged into my PCI slot with all 4 harddrives plugged into it at raid 0.

-Thanks,
     Rich

---

### Post by fjgaude on 2008-04-10
How did you setup the raid0?

If you don't have a driver for Linux for the PCI card, then you will have to use dmraid, as I suggested earlier. This is what is called fakeraid... limited to the PCI bus speed of about 110MB/sec throughput.

---

### Post by dottedquad on 2008-04-10
> **fjgaude said:**
> How did you setup the raid0?

If you don't have a driver for Linux for the PCI card, then you will have to use dmraid, as I suggested earlier. This is what is called fakeraid... limited to the PCI bus speed of about 110MB/sec throughput.

When the computer gets booted up it goes through the cycle of finding the harddrives and gives a list of those 4 hard drives saying Array 0 by each hard drive.

Thanks,
     Rich

---

### Post by dottedquad on 2008-04-10
dmraid worked wonders for my SATA Raid PCI controller card.  I'm now struggling with my second RAID PCI controller card for my IDE drives.

---

### Post by fjgaude on 2008-04-10
What seems to be the problem with the second controller card?

---

### Post by dottedquad on 2008-04-10
> **fjgaude said:**
> What seems to be the problem with the second controller card?

It's the user(me) that's having the issue trying to mount my IDE drives that are raided at 0.  I'm trying to figure out why dmraid is not finding the hard drives.

when I run the command sudo dmraid -r I receive the follow:
/dev/sda: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0
/dev/sdb: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0

There are no signs of the IDE drives.  What should I do now?

-Thanks,
     Rich

---

### Post by Zack McCool on 2008-04-10
How are they set up?

Raid 0 (striping) is usually set up so that you'd have 2 drives combined into one logical drive.  You indicated that all 4 drives are configured as array0, but how many logical drives are configured?

In the OS, you wouldn't see the individual IDE drives, but rather the logical drives that the RAID adapter presents.  

It looks like you are being presented with 2 logical drives, sda and sdb.

---

### Post by dottedquad on 2008-04-10
> **Zack McCool said:**
> How are they set up?

Raid 0 (striping) is usually set up so that you'd have 2 drives combined into one logical drive.  You indicated that all 4 drives are configured as array0, but how many logical drives are configured?

In the OS, you wouldn't see the individual IDE drives, but rather the logical drives that the RAID adapter presents.  

It looks like you are being presented with 2 logical drives, sda and sdb.

the sda and sdb are my SATA Drives which are setup and mounted correctly.  I'm having issues trying to setup my 4 IDE drives which bios is saying it's already setup as Array 0.  Now I need to mount the Raid set so I can view them in linux.

-Rich

---

### Post by fjgaude on 2008-04-11
> **dottedquad said:**
> It's the user(me) that's having the issue trying to mount my IDE drives that are raided at 0.  I'm trying to figure out why dmraid is not finding the hard drives.

when I run the command sudo dmraid -r I receive the follow:
/dev/sda: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0
/dev/sdb: sil, "sil_ahbiejbgcgaf", stripe, ok, 312579712 sectors, data@ 0

There are no signs of the IDE drives.  What should I do now?

-Thanks,
     Rich

Okay, you have four stripped drives in raid0 array... working off a Silicon Images chip off a card or on your motherboard? Did you setup the four drives in the BIOS?

You mount the array with this command after you have created a mountpoint:

```
suod mkdir /home/raid
```

If this is okay with you as a mountpoint. If not change to what ever you wish.

Then you mount:

```
sudo mount /dev/mapper/sil_ahbiejbgcgaf /home/raid
```

This assumes you placed a filesystem on the array when you created the raid0 array. If not, then in Ubuntu you could do this:

```
sudo mkfs -t ext3 /dev/mapper/sil_ahbiejbgcga
```

I trust you have read the **man dmraid** pages and understand what it has said.

Let us know how you are doing.

---

### Post by dottedquad on 2008-04-12
> **fjgaude said:**
> Okay, you have four stripped drives in raid0 array... working off a Silicon Images chip off a card or on your motherboard? Did you setup the four drives in the BIOS?

You mount the array with this command after you have created a mountpoint:

```
suod mkdir /home/raid
```

If this is okay with you as a mountpoint. If not change to what ever you wish.

Then you mount:

```
sudo mount /dev/mapper/sil_ahbiejbgcgaf /home/raid
```

This assumes you placed a filesystem on the array when you created the raid0 array. If not, then in Ubuntu you could do this:

```
sudo mkfs -t ext3 /dev/mapper/sil_ahbiejbgcga
```

I trust you have read the **man dmraid** pages and understand what it has said.

Let us know how you are doing.


What you just explained to me I have done a while ago to mount my two SATA drives which have been working from the beginning.  The issue I'm having is getting dmraid to find and locate my 4 drives hooked to my ITE IT8212F chipset raid controller which is seated in my PCI slot.  Until than I can't mount something that hasn't been found.

-Thanks,
     Rich

---

### Post by dottedquad on 2008-04-12
after running dmraid -l I found out that dmraid doesn't support ITE IT8212F chipset so i'm assuming my other alternative is to compile the drives within the kernal?  Which, I haven't tried and scared to even try :-/ since i rather not break my working system.  Is there anything else I can try?

-Thanks,
    Rich

---

### Post by fjgaude on 2008-04-12
What do you get when you enter:

```
sudo dmraid -tay
```

What am I missing about what you are trying to do?

---

### Post by dottedquad on 2008-04-12
> **fjgaude said:**
> What do you get when you enter:

```
sudo dmraid -tay
```

What am I missing about what you are trying to do?

I greatly appreciate you dealing with my ignorance with this matter.  I'm brand new to the linux world.

When I ran the command above I received the following output:

sil_ahbiejbgcgaf: 0 625159424 striped 2 128 /dev/sda 0 /dev/sdb 0
sil_ahbiejbgcgaf1: 0 625153347 linear /dev/mapper/sil_ahbiejbgcgaf 63

---

### Post by fjgaude on 2008-04-13
You are saying that the kernel doesn't recognize the ITA raid chipset, but mdraid is showing that you have a Sil, Silicon Image, chipset.

I can't help you with compiling kernels... never have done it in the last 20 years.

---

### Post by dottedquad on 2008-04-14
> **fjgaude said:**
> You are saying that the kernel doesn't recognize the ITA raid chipset, but mdraid is showing that you have a Sil, Silicon Image, chipset.

I can't help you with compiling kernels... never have done it in the last 20 years.

Yes that is what i'm saying.  I have two SATA drives hooked up to a Sil, Silicon Image, chipset card that is seated in another PCI slot.  And when I run that command it shows the logical drives in on the Sil, Silicon Image, chipset card and nothing for the ITA Controller card for my IDE drives.

I was reading up on the ITA raid chipset and apparently something about the Kernal change in Ubuntu caused the loss of support for the ITA raid chipset unless you compile the drives into the kernel.

-Rich

---

