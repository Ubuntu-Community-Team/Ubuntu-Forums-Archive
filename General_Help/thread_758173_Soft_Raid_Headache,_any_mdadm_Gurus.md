---
title: "Soft Raid Headache, any mdadm Gurus ?"
date: 2008-04-17
forum: General Help
---

### Post by lxme on 2008-04-17
Hello all.

I had a two drives, 3 Raid Arrays working perfectly fine with Gutsy, they were correctly set up with mdadm (or so I thought) until I upgraded to Hardy.
It still worked fine at first, but since kernel 2.6.24.14  it doesn' anymore.
original mdadm.conf

```
mid@erle:~$ cat /etc/mdadm/mdadm.old
DEVICE /dev/hda1 /dev/hdc1
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=59df1a2f:7478dca4:ada2e0d6:c55a2a62
DEVICE /dev/hda2 /dev/hdc2
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=33f9e0da:19e9dcf1:0fdd0b94:652c63a7
DEVICE /dev/hda3 /dev/hdc3
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=862f6e2d:48446df6:0b14c76b:55463eb6
DEVICE /dev/hda4 /dev/hdc4
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=bcf75a4e:d44b010a:d285d6ff:1f3c4043
```


I first realized my drives were changed from /dev/hda and /dev/hdc to /dev/sda and /dev/sdb
Fine, I changed my mdadm.conf to reflect the changes and I can now assemble the arrays manually.

updated mdadm.conf

```
mid@erle:~$ cat /etc/mdadm/mdadm.conf
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=59df1a2f:7478dca4:ada2e0d6:c55a2a62
DEVICE /dev/sda2 /dev/sdb2
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=33f9e0da:19e9dcf1:0fdd0b94:652c63a7
DEVICE /dev/sda3 /dev/sdb3
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=862f6e2d:48446df6:0b14c76b:55463eb6
DEVICE /dev/sda4 /dev/sdb4
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=bcf75a4e:d44b010a:d285d6ff:1f3c4043
```


Still, sometimes the arrays wouldn't always mount at boot time. I found out my drives path /dev/sd(n), keep being shuffled around. what is not an issue for fstab thanks to UUID seems to be one for my mdadm.conf.
I did some research to find a fix, and found out mdadm was supposed to assemble the arrays  thanks to the partitions superblocks and not the .conf

But my partitions superblock still point to /dev/hda and /dev/hdb :(
ex:
```
erle:~$ sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 21f8564e:6dcb5a14:9bddd82b:7ca7d896
  Creation Time : Sat Aug 18 02:20:15 2007
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Aug 18 12:06:39 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : df02b0ae - correct
         Events : 0.5

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       3        1        0      active sync   /dev/.static/dev/hda1

   0     0       3        1        0      active sync   /dev/.static/dev/hda1
   1     1      22        1        1      active sync   /dev/.static/dev/hdc1

```
and
```
mid@erle:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 21f8564e:6dcb5a14:9bddd82b:7ca7d896
  Creation Time : Sat Aug 18 02:20:15 2007
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Aug 18 12:06:39 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : df02b0c3 - correct
         Events : 0.5

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1      22        1        1      active sync   /dev/.static/dev/hdc1

   0     0       3        1        0      active sync   /dev/.static/dev/hda1
   1     1      22        1        1      active sync   /dev/.static/dev/hdc1
```

How can I fix that without loosing any data ??

Is there a way to update the md superblock ?
I tried 
mdadm -A --update= <various parameters here>
but no success.
or do I need to zero it then recreate it ?
will I loose any data?
Is my mdadm.conf ok ?

Thanks in advance for the precious help here !

Lxme

---

### Post by fjgaude on 2008-04-17
You have three stripped partitions and one mirrored partition on two drives, yes?

I've never tried to do what you have done... but that's okay if you have had success.

I've gone from an AMD motherboard to an Intel one, carrying the same four **raid5** drives without issue. From Feisty to Gutsy to Hardy without issue. The only thing I did in each case was install **mdadm** and then run:

```
sudo mdadm --assemble --scan
```

That did it every time.

**mdadm** doesn't care what the drives were called, or called now, it knows what is from the initial create with the superblocks. No need to change the mdadm.conf file. Go back to what it was originally.

You likely have something else going on with hardware failure, intermittent, something like that. If you have only one drive with a slight random failure, fault, then you will see things strange happening. With only two drives with four partitions expect the unexpected: **Make data backups**.

Backups are as necessary using raid as it is with JBODs.

Let us know how you are doing.

---

### Post by lxme on 2008-04-17
thanks for your contribution fjgaude  
I did read your thread on this forum while searching for a fix.

as you said, mdadm.conf is not needed to start my arrays at boot time. the superblock is the key.
as for  mdadm --assemble --scan here is the result

```
sudo mdadm --assemble --scan
mdadm: no devices found for /dev/md1
mdadm: no devices found for /dev/md2
mdadm: no devices found for /dev/md3
```

What seems totally wrong to me is indeed my drives superblocks

 mdadm -E /dev/sdb1
still refer to my old path: 

```
      Number   Major   Minor   RaidDevice State
this     1      22        1        1      active sync   /dev/.static/dev/hdc1

   0     0       3        1        0      active sync   /dev/.static/dev/hda1
   1     1      22        1        1      active sync   /dev/.static/dev/hdc1
```

those /dev/.static/dev/hdc1 and  /dev/.static/dev/hda1 seems completly out of place here shouldn't they read something like  /dev/.static/dev/sdb1 and  /dev/.static/dev/sda1 ??

---

### Post by fjgaude on 2008-04-17
I have no knowledge of what .static is.

From my experience the drive names don't make any difference. **mdadm** shows what they were named when you first built the arrays and to mdadm they stay that way, no matter what. There is no need to change them... the superblocks count. But from what I know you can't change them without losing your data.

Several times I have changed slots where drives were located and the array didn't care... I don't notice what drives are called anymore. Hardy seems to have fixed any drive name change but you are going from PATA to SATA... some only SATA will exist. I see no reason that your hd type drives don't work correctly now.

There is a way to get at the backup superblocks, but I've never had to do that. Such would be required by a drive going bad, unless you have a failinig drive.

```
sudo e2fsck -b 32768 98304 163840 /dev/sd[nn] 
```

I have three block numbers just as examples. The size of your drive determines where the blocks can be found. Do a **man e2fsck** to see what I'm pointing to.

I suppose you don't have backups of your important data? How old are the two drives?

---

### Post by lxme on 2008-04-18
> There is a way to get at the backup superblocks, but I've never had to do that. Such would be required by a drive going bad, unless you have a failinig drive.

Code:

sudo e2fsck -b 32768 98304 163840 /dev/sd[nn]

Thanks, but yes, my drives are working fine, I can assemble them manually, so this seems a bit risky to do. 
furthermore, as far as I know, my superblocks doesn't seems that bad, do they ?
Do you know any urls pointing to explanations on how to interpret the results of an mdadm examine command ?


> 
I suppose you don't have backups of your important data? How old are the two drives?

Bingo.. but of course I could do one, providing I find enough disk space somewhere to do it.
But really, I wouldn't like to go through this. 
The drives themselves must be 4 years old now.

What about the command mdadm --zero-superblock would tha be of any use? would I also loose the content of the drive ?

---

### Post by fjgaude on 2008-04-18
I believe the --zero-superblock command removes the drive from being apart of the raid array, just as changing the tag from raid to non-raid.

Have you tried the -D, the --detail command:

```
sudo madam -D /dev/md[nn]
```

That shows really what the array is.

I don't have any URL that would help with what you are going through.

You cannot --build or --create without destroying the data on the drives.

What about a --force assemble?

```
sudo mdadm --assemble -f /dev/md[nn]
```

That might work.

---

### Post by lxme on 2008-04-18
> 

Have you tried the -D, the --detail command:


```
 sudo mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Aug 18 12:26:41 2007
     Raid Level : raid0
     Array Size : 97675008 (93.15 GiB 100.02 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Aug 18 12:30:48 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : e09311a2:acd5c147:766062dd:2427fe40
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8       50        0      active sync   /dev/sdd2
       1       8       66        1      active sync   /dev/sde2
```

I wish I could decrypt those results..

And for a --force assemble?

```
sudo mdadm --assemble -f /dev/md2
mdadm: no devices found for /dev/md2
```

Same for all other arrays :( :( :(

Also, even though I dont believe it's a Hardy related problem, maybe I should have posted this topic in the development forum? the sticky about Hardy makes me wonder..

---

### Post by fjgaude on 2008-04-18
Interesting... the -D command shows that the array is healthy, perfect in fact.

It has to do with Hardy no seeing hd[n] drives any more and setting them to sd[n].

I'm at a loss as to what to suggest. Try using the sd[nn]s you get from the -D command for each array in the mdadm.config file and see if you can force an --assemble --scan.

You can try the Hardy forum but I'm not optimistic: I'm there with both raid and virtualization issues daily if not more often. Hardy is just about to go into Release Candidate today or Monday. Then in one week or so will be released. I can't say I've seen anyone comment on troubles from hd[n] drives. I'm sure there is something within mdadm or md that has caused your issues, at this point.

Let us know if you make any progress in mounting.

---

