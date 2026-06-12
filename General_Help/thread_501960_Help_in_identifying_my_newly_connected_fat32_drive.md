---
title: "Help in identifying my newly connected fat32 drive"
date: 2007-07-16
forum: General Help
---

### Post by friction on 2007-07-16
i am a new user of Ubuntu 6.06 LTS (dapper) and direly need help on : 

i need to mount and use my fat32 drive (preloaded with stuffs in it) have trouble in finding the drive letter that ubuntu would give it ! being a single boot and with this one configured as the primary slave, i would expect /hdb1 to be default drive letter... and carried out mounting the drive... 
          
          sudo mkdir /media/windows
          sudo mount /dev/hdb1 /media/windows -t vfat -o iocharset=utf8, unmask=000

... only to find that the primary drive (hda1) was sitting in that slot as hdb1 tooo ! 

so, help me in this to get me back on track 


Also 
is there any way i can upgrade to the latest 7.0X version without having to loose all the installs and settings ? 

i would indeed aprreciate much needed help in this by saying "Thanks" 

....

friction

---

### Post by brent113 on 2007-07-16
what you can do is list all your harddrives in the system with

```

sudo fdisk -l

```

Try using that to find your harddrive and then post back if that works.

About upgrading to feisty 7.04, yes you can do that either over the internet using

```

gksu "update-manager -c"

```

or you can download and burn the cd and it will automatically detect an upgrade.  You will still have all of your programs and settings.

---

### Post by friction on 2007-07-16
the fdisk command listed the drives ... but as i mentioned earlier 

there were 2 drives 
hda     partitions:    hda1(linux)    hda2 (extended)  hda5 (swap)

hdb   was excatly the same with the same serials and everything.... 

i would require further info on how to tackle this problem 



and thanks for the update info too  
     (i am able to get the update available as 6.10 and the command terminal says  " warnings.warn("apt API not stable yet", FutureWarning) 
any reasons to worry about ?? ? 

friction

---

### Post by brent113 on 2007-07-16
I think you alluded to it, but I want to make sure.  Both drives do register correctly in the BIOS right?

can you post the output of

```
sudo lshw -C disk

```

---

### Post by friction on 2007-07-16
Hi Brent 

thank you for following up ! no respite yet for me !!! ~!! 

Here the output for what you asked me for 

*-disk:0
       description: ATA Disk
       product: QUANTUM FIREBALL CX13.6A
       vendor: Quantum
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: A3F.0B00
       serial: 134925323503
       size: 12GB
       capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
       configuration: mode=udma2 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 12GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 564MB
          capabilities: extended partitioned partitioned:extended
  *-disk:1
       description: ATA Disk
       product: QUANTUM FIREBALL CX13.6A
       vendor: Quantum
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: A3F.0B00
       serial: 134925220623
       size: 12GB
       capacity: 12GB
       capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
       configuration: mode=udma2 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.1,1
          logical name: /dev/hdb1
          capacity: 12GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.1,2
          logical name: /dev/hdb2
          capacity: 564MB
          capabilities: extended partitioned partitioned:extended
  *-cdrom
       description: DVD writer
       product: BENQ DVD DD DW1620
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: B7C9
       serial: MY0Y55547015946M0014
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audi o cd-r cd-rw dvd dvd-r
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc

it is not recognised in this too ! the other is supposedly a Maxtor IDE disk drive with 200Gb capacity ! 

So, any tips on proceeding would definitely be appreciated....

---

### Post by brent113 on 2007-07-17
hmm, I'm getting to be at a loss for options within this os.

What i might try is unplugging the current drive that linux is installed on (leaving only the one that it can't see in) and then booting from the live cd.

What i'm hoping for is that fdisk -l and lshw -C disk will display the right things when the drive is isolated.  Try that and let me know how it goes.  We'll go from there then.

PS.  If there's nothing important on the drive I'd fire up (on the live cd) GParted from the System/Administration menu and format it and verify the flags are correct

---

