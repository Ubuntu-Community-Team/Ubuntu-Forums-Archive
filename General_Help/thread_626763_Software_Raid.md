---
title: "Software Raid"
date: 2007-11-29
forum: General Help
---

### Post by Rufe0 on 2007-11-29
Hi All
I found this
[http://cs.joensuu.fi/~mmeri/usbraid/](http://cs.joensuu.fi/~mmeri/usbraid/)

I know its a bit old and its not in ubuntu but it should still work right? Well it has worked up to the part where you build the raid with mdadm. Here is the code im trying to run

mdadm -C -v /dev/md0 -l=5 -n=3 /dev/disk/by-id/usb-Corsair_Flash_Voyager_A000000000025670-0:0 /dev/disk/by-id/usb-Corsair_Flash_Voyager_A400000000026424-0:0 /dev/disk/by-id/usb-Corsair_Flash_Voyager_A500000000025702-0:0

The error i get is invalid raid level, nomatter what raid level I pick. Tried with 2,3 and 4 sticks with the same results.

Anyone any ideas?

Thnx Rufe0

---

### Post by fjgaude on 2007-11-29
I've never used other than /dev/sda1, etc. to create an array.

Why don't you try:

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```

That is, use the non-UUIDs for the drives.

Under Ubuntu 7.10 md has no trouble auto assembling the arrays build with /dev/sdas.

Let us know what your results are.

---

### Post by Rufe0 on 2007-11-29
Yeah OK I will try that tommorow thanks.

Had another thought, would there be any way to turn 2 of the 4 RAM memory cards into a virtual disk like a HD or USB stick you know what I mean?

---

### Post by fjgaude on 2007-11-29
Off the top of my head, no. I haven't heard of anyone wishing to do that, yet, until now.

I'll think about it.

---

### Post by Rufe0 on 2007-11-30
sudo mdadm --create /dev/md0 --level=0 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

sudo mke2fs /dev/md0

adam@adam-desktop:~$ sudo mount /dev/md0 /mnt/usbraid1
mount: mount point /mnt/usbraid1 does not exist

adam@adam-desktop:~$ sudo mount /dev/md0 /home/adam/Desktop/mntpoint

adam@adam-desktop:~$ sudo hdparm -tT /dev/md0
/dev/md0:
 Timing cached reads:   2192 MB in  2.00 seconds = 1096.63 MB/sec
 Timing buffered disk reads:  140 MB in  3.04 seconds =  46.06 MB/sec



YES! After a little bit of tweaking I now have a 1GB drive with a 46MB/s read speed. Which is about half the maximum quoted speed of the drives times drive number. So I could get 7newer flash sticks and make a drive with 120 to 240MB/sec read speed. Then install the OS and program files to it. Then i would remount all the folders where writing happens all the time to my HD then I wont be using many of my write cycles on the flash.

If the same could be accomplished with RAM that would be great because the read speeds would be measured in GB/sec, it would be cheaper, and there isn't the write cycle issue. I read a website which said such devices do exist as stand alone drives but I cannot find anyone who wants to sell me one.

Thnx for the info, is there a command I can run to test the drive further? Maybe get access and more detailed read write speed analysis? I've tried bonnie++ but that just runs on the HD. Is there something like bonnie++ /dev/md0 ?

---

### Post by fjgaude on 2007-11-30
Congratulations! Good work.

Each of your four drives have a read speed of about 24 MB/sec?

The thing I've found with disk controllers running off the PCI bus is a throughput maximum of 114 MB/sec no matter how many drives in what configuration. You should be getting close to that with your 4x raid0.

Your memory or CPU or both is not fast enough to give you the 114 MB/sec.

RAM disk are coming, not here yet.

---

### Post by Rufe0 on 2007-11-30
The drives are 1gb corsair flash voyager models. They are suposed to have a 19mb/s speed although when I do hdparm on them I only get around 15mb/s. At 46mb/s raid they are each doing 11.5mb/s. Thats more like 76% of actual speed and 60% of max rated speed. Guess thats the penalty of software raid

So do you mean if I got a normal HD array with say WD raptors and a PICe control id only get around 114?

---

### Post by fjgaude on 2007-11-30
Okay, so those flash drives are not that fast... I have one that does 14 MB/sec, and it's rated at 40X.

Software raid can be as fast as hardware raid, if you have fast memory and CPUs and controllers working off a fast bus.

My tests show PCI bus can permit up to 114 MB/sec, and my CPUs are loafing, an AMD 64 2X 4400+, slightly overclocked. DDR SRAM at about 420 MHz. I get this 114 MB/sec using two 77 MB/sec Seagates or three or four 44 MB/sec Raptor WD drives in raid0, or three 77 MB/sec Seagates in raid5.

You see the PCI bus controllers is my bottleneck. I should be at 140 with two Seagates or at 160 with four WDs.

Using fast drives requies a fast bus like PCI-X or PCI-Express controllers for the SATA drives.

---

### Post by Rufe0 on 2007-11-30
Hmm yes I was looking at getting 4x raptor raid 0 on a pciexpress bus. I thought the flash would be nicer though, no noise, power, heat etc.

I thought the HDs would do more than 44 though, that means it would only be like 174 theoretical max. Still the HDs would be slightly faster and slightly cheaper than the flash but the main benefit is the size.

If only you could buy some kind of adapter for RAM, just one stick of ram would be capable of probably a couple of GigaBytes per second the latest ddr3 ones can do like 10GB/sec. Plus you could probably get 4x4gb sticks for the same price as the the Raptors or a load of the fastest flash usbs.

Who cares if you couldnt turn it off much. I am sure you could a) add a battery for short power cuts and b) have a laptop PSU or some other kind of electrical device PSU, which wouldnt turn off with the PC.

---

### Post by fjgaude on 2007-11-30
Say, don't get me wrong, the latest drives do 134 MB/sec. I'm sure Seagate will be advertising them very soon, Hitachi already does.

These new drives, even the ones I have, are noiseless, even in deep seeks. I do have mine mounted with rubber gromets. Drives will get faster as times goes on. I would expect them to be at 200 MB/sec in a year or so.

PCI-Express X1 is only good up to 250 MB/sec, about twice what PCI is. Now I'm not sure what X4 is, but likely 500 MB/sec or more. The Highpoint 2310 PCI-E SATA controllers work at X4 and they have been tested for nearly 400 MB/sec seq read. Now that is fast, and about what most of the big servers are doing now.

For anyone needing fast, big capacity for storage, like me a graphic designer, I think I'll be with disks for a long time to come.

(Oh, the Raptors I have were first generation, slow by today's standards. I don't use them anymore.)

---

### Post by psusi on 2007-11-30
Since these disks are USB the most you can get out of any number of them will be around 50 MB/s since that's the capacity of USB2.  

As for 10 GB/s, even main system ram isn't that fast, and you're certainly not going to get that over the bus.  I have seen cards that you can slap a few gigs of ram in and they supposedly make it appear like a hard disk, but you still ran into the PCI limit.  Not sure if there are newer pcie versions these days.  

Also if a x1 PCI slot is 250 MB/s, then a x4 would be 1000.

---

### Post by fjgaude on 2007-11-30
Well, th only data I have is for the Highpoint at X4 on PCI-E bus. The bus is likely capable of 1000 MB/sec but the electronics on the card is not. In a raid5 array with six and eight drives, drives that have 70 MB/sec throughput, the controller starts toping out at about 350 MB/sec and is flat at about 500.

Sure DDR3 RAM would be good for, say, 16 Gigs storage, and 10 GB/sec throughput. It's likely coming.

All we to do is wait and things change, when it comes to speed, size, reliablity.

---

### Post by Rufe0 on 2007-12-04
USB2 is 480mbs

---

### Post by fjgaude on 2007-12-04
I am thinking along the lines of a RAM board that fits into computer or an eSATA connection. The external drive using eSATA could be very fast if the onboard computer controller is fast.

No way to get fast from USB2 or Firewire, unless their specs get greatly upgraded.

---

### Post by psusi on 2007-12-04
> **Rufe0 said:**
> USB2 is 480mbs

480 Mbps = 57 MB/s

---

### Post by fjgaude on 2007-12-04
Well, fast to me points to raid5 or 6 arrays with many fast disks, resulting in sequential reads of over 300 MB/sec. Today's disk technoligy provides reads for 70 to 130 MB/sec. Just two years ago it was less than 45 MB/sec.

Boy, times are moving us along faster and faster.

---

### Post by psusi on 2007-12-04
It has been over 3 years now since I picked up a pair of WD 10,000 rpm sata raptors.  It was 3 years before that when I got a seagate 15,000 rpm scsi drive, and 3 years before that when I had dual seagate 10,000 rpm scsi drives.  Where are my 15,000+ rpm sata drives today?

---

### Post by fjgaude on 2007-12-04
I guess few folks want them, don't have the controllers to handle them, etc. IOW, bets me.

---

