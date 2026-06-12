---
title: "Extreme slow NTFS in Windows 7 after dual boot"
date: 2012-11-13
forum: General Help
---

### Post by Erraten on 2012-11-13
Dear all

After I recently decided to try my luck with Linux and  changed to the good side of OS so to speak I experience some problems which I appreciate your help and advice.

My problem is that  I have a data partition in NTFS that is extremely slow under Windows. I am talking about 5 minutes until I can open the first folder. If I access it under Linux it is accessible in normal speed.
After about 10-15 minutes waiting and trying it start to behave normal and I can access files in reasonable speed.
I do not have this problem if I mount the drive under Ubuntu

I have no idea what the problem is, but I sure appreciate your support. 
It seems some process or something is blocking my access which I can only explain with the way the hard disk is partitioned. 

I've used and fiddled with computers for a while but I am an absolute newbie in Linux and Ubuntu. Recently I set up my laptop with one internal hard drive to dual-boot Ubuntu 12.04 and Windows 7. I followed an explanation on the Ubuntu website on how to do and it worked fine. Also both system run smooth and start fast.

The only thing that is dead slow is the data drive under Windows..

Now, I have a hard drive that looks a bit fragmented:

100MB  Primary NTFS  Windows System reserved
100GiB  Primary NTFS Windows partition 
207GiB Extended partition for Linux
    10GiB Ext4 Root
    2GiB  that Linux RAM thing which name I forgot in the format that is suggested
    195GiB ext 4 for storage under Linux
630GiB Primary NTFS for Data (before this was also an Extended Partition and I thought changing it into primary will solve the problem - well, it didn't..) 

I appreciate any help and suggestions - I realize this might not be a Linux issue but the dual boot brought me into this mess so I am begging you for help.

Thank you all in advance already.

Paul

---

### Post by Bucky Ball on 2012-11-13
Welcome to the forums. You might be better to ask this in a Windows forum as I can't see it has anything to do with Ubuntu, but you never know your luck, someone may have some ideas. This problem occurs only in Windows. When you are booted into Windows, Ubuntu is not running and plays no part in proceedings, therefore is not the cause of this issue. You also haven't changed or altered the data partition in anyway during the Ubuntu install, I assume, and it is working fine in Ubuntu. 

I suggest defragging in Windows a few times with something like Powerdefragmenter (I think it's called, from memory; been a long time) rather than the default one. See if that makes any diff.

---

### Post by sgage on 2012-11-13
> **Erraten said:**
> Dear all

After I recently decided to try my luck with Linux and  changed to the good side of OS so to speak I experience some problems which I appreciate your help and advice.

My problem is that  I have a data partition in NTFS that is extremely slow under Windows. I am talking about 5 minutes until I can open the first folder. If I access it under Linux it is accessible in normal speed.
After about 10-15 minutes waiting and trying it start to behave normal and I can access files in reasonable speed.
I do not have this problem if I mount the drive under Ubuntu

I have no idea what the problem is, but I sure appreciate your support. 
It seems some process or something is blocking my access which I can only explain with the way the hard disk is partitioned. 

I've used and fiddled with computers for a while but I am an absolute newbie in Linux and Ubuntu. Recently I set up my laptop with one internal hard drive to dual-boot Ubuntu 12.04 and Windows 7. I followed an explanation on the Ubuntu website on how to do and it worked fine. Also both system run smooth and start fast.

The only thing that is dead slow is the data drive under Windows..

Now, I have a hard drive that looks a bit fragmented:

100MB  Primary NTFS  Windows System reserved
100GiB  Primary NTFS Windows partition 
207GiB Extended partition for Linux
    10GiB Ext4 Root
    2GiB  that Linux RAM thing which name I forgot in the format that is suggested
    195GiB ext 4 for storage under Linux
630GiB Primary NTFS for Data (before this was also an Extended Partition and I thought changing it into primary will solve the problem - well, it didn't..) 

I appreciate any help and suggestions - I realize this might not be a Linux issue but the dual boot brought me into this mess so I am begging you for help.

Thank you all in advance already.

Paul

I have dual booted Windows and Linux for years, and have never experienced this.

You might want to try the defrag suggestion, but since you say the ntfs partition works fine under Ubuntu I doubt that's it. It might be a more subtle filesystem corruption. First thing I would do is try a chkdsk on the partition in question and see what it finds. 

In Windows, in the file manager right-click on the drive in question, select 'tools', 'scan disk for errors', and give it a whirl...

---

### Post by dannyboy79 on 2012-11-13
can you show is the output of this command? it will show us your partition table exactly
```
sudo fdisk -l
```

I am also not sure what you mean when you said, "before this was also an Extended Partition and I thought changing it into primary will solve the problem - well, it didn't.."

---

### Post by Erraten on 2012-11-13
Hello Everyone.
Thank you all for your quick replies - I really do love time zones.
I will try to answer the question in reverse order: 
 
@Dannyboy

here is the result from your code line:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf4bdb80b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   200706047   100249600    7  HPFS/NTFS/exFAT
/dev/sda3       200706048   634985189   217139571    5  Extended
/dev/sda4       634986496  1953523711   659268608    7  HPFS/NTFS/exFAT
/dev/sda5       200716110   221182919    10233405   83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6       221182983   225375884     2096451   82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.
/dev/sda7       225375948   634985189   204804621   83  Linux
Partition 7 does not start on physical sector boundary.

Disk /dev/mapper/cryptswap1: 2146 MB, 2146765824 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4192902 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
Disk identifier: 0xe15b3873
```

Even though I tried to make the partitions start at the last partitions end, gparted always found a way to put some unused megabytes in-between. This is why is looks so fragmented.
I do realize that the alignment of the partitions looks very bad like this now.

> I am also not sure what you mean when you said, "before this was also an  Extended Partition and I thought changing it into primary will solve  the problem - well, it didn't.." 

What I meant by this is: Now sd5 sda6 and sda7 are part of the extended partition sda3 and sda4 is an own primary partition.
Before sda4 was also part of the extended partition sda3. Last week I shrank the sda3 and created the sda4 as a primary because I thought that is the root cause of the problem.

@sgage:
I will try chdsk and post the result. It is a brand new hard disk though. I totally forgot about that tool - thank you for reminding me.

@Bucky Ball:
As above: It is a brand new drive and it works with reasonable speed under Linux. I am not really counting the milliseconds here It takes literally 10 minutes before I can access is. The reason why I post it here is because I thought it might have to do with the 'invisible Linux partition' between the Windows system partition and the Data drive and somebody had the problem before and nows how to tell Windows how to deal with it. Naja you are right - I will try in a windows forum as well..

Nevertheless I hope I can still find an answer here ;-)

Cheers

Paul.

---

### Post by westie457 on 2012-11-13
Occasionally if a partition is not unmounted properly before a system shutdown and you then boot into another operating system you can get the symptoms you are describing. This has happened to me in the past. Now all non-system partitions are unmounted before shutting Ubuntu down. Never have worked out what exactly causes the issue. Once or twice this has also happened with USB sticks.

---

### Post by Bucky Ball on 2012-11-13
Invisible Linux partition? Never heard of it, sorry ... ;) Have you any more details on that?

---

### Post by westie457 on 2012-11-13
> **Bucky Ball said:**
> Invisible Linux partition? Never heard of it, sorry ... ;) Have you any more details on that?

I did not say 'invisible Linux partition' and quite probably did not word it correctly. What I meant was when a partition is not unmounted cleanly file-system corruption occurs. 

A case in point is as I was writing this post my system crashed and had to hold the power button to force a shut-down. On restarting I chose 'recovery mode' and ran 'fsck' because in the lines of text was a line that said 'recovery is needed on a read-only file-system.

I did try Ctrl+Alt+PrtSc with 'reisub' to safely log out and log in again. Unfortunately that did not work.

@Bucky Ball I did not read properly the post before mine. So apologies from me for getting the wrong end of the stick.

---

### Post by Bucky Ball on 2012-11-13
@ Westie: Understood. You didn't say that, Erraten did.

---

### Post by audiomick on 2012-11-13
Just a thought; the NTFS partition in question is not nearly full, is it?

---

### Post by Erraten on 2012-11-14
Hi Guys
Back from work. Will check the ckdsk now and defragmenting. Just quickly answering the nice people who take time to post:

@audiomick: No, the NTFS is 200GB used of 650GB available. It is all freshly copied as a chunk so I am not sure if it actually could be fragmented. Yet I give that suggestion of another user a shot.

@Buck Ball: You DON'T know the famous invisible Linux partition? You can choose it now in gparted.. ;-)
Ok, misleading post, I admit. What I meant was the ext4 and SWAP partition(s) that cannot be seen under under Windows..

Cheers

Steffen

---

### Post by dannyboy79 on 2012-11-14
> **Erraten said:**
> 
[CODE]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf4bdb80b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   200706047   100249600    7  HPFS/NTFS/exFAT
/dev/sda3       200706048   634985189   217139571    5  Extended
/dev/sda4       634986496  1953523711   659268608    7  HPFS/NTFS/exFAT
/dev/sda5       200716110   221182919    10233405   83  Linux
Partition 5 does not start on physical sector boundary.
/dev/sda6       221182983   225375884     2096451   82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.
/dev/sda7       225375948   634985189   204804621   83  Linux
Partition 7 does not start on physical sector boundary.

What I meant by this is: Now sd5 sda6 and sda7 are part of the extended partition sda3 and sda4 is an own primary partition.
Before sda4 was also part of the extended partition sda3. Last week I shrank the sda3 and created the sda4 as a primary because I thought that is the root cause of the problem.
Just so you know sda4 is NOT a primary partition and neither is sda4, they are part of the extended partition. I am wondering if you tried to do something with NTFS partitions and GParted that isn't possible and it somehow messed up your NTFS partitions.

Can you still access sda4? It's a NTFS partition within the extended partition.

---

### Post by oldfred on 2012-11-14
It is normal not to see Linux partitions under Windows as Windows does not work with Linux formats. Main reason for the shared NTFS data partition.

If sda4 is inside the extended it is a partition error and many system  tools stop working. But it looks like sda4 is outside the extended  partition.

By definition sda4 is a primary partition in MBR(msdos) partitioning. sda1 thru sda4 are the 4 primary partitions. The first logical is sda5, but when repartitioning numbers can change, but all logicals will be sda5 or above and all primaries will be sda1 thru sda4.

---

### Post by dannyboy79 on 2012-11-14
> **oldfred said:**
> It is normal not to see Linux partitions under Windows as Windows does not work with Linux formats. Main reason for the shared NTFS data partition.

If sda4 is inside the extended it is a partition error and many system  tools stop working. But it looks like sda4 is outside the extended  partition.

By definition sda4 is a primary partition in MBR(msdos) partitioning. sda1 thru sda4 are the 4 primary partitions. The first logical is sda5, but when repartitioning numbers can change, but all logicals will be sda5 or above and all primaries will be sda1 thru sda4.not sure what you're seeing but I clearl see his fdisk -l output as showing sda3 being an extended partition making all partitions after that logical and NOT primary. COrrect me if I am wrong please

---

### Post by oldfred on 2012-11-14
Order in a fdisk or parted list does not matter. Sectors do. And partition numbers do matter in MBR partitioning. If you have sda4 inside the extended it will report errors.
So extended ends at 6349851789 and sda4 starts at 634986496 and ends just before end of drive.

Drive:
255 heads, 63 sectors/track, 121601 cylinders, total [COLOR=Red]1953525168[/COLOR] sectors

Device Boot Start End Blocks Id System
/dev/sda3 200706048 [COLOR=Blue]634985189[/COLOR] 217139571 5 Extended
/dev/sda4 [COLOR=Blue]634986496[/COLOR] [COLOR=Red]1953523711[/COLOR] 659268608 7 HPFS/NTFS/exFAT

---

### Post by dannyboy79 on 2012-11-14
> **oldfred said:**
> Order in a fdisk or parted list does not matter. Sectors do. And partition numbers do matter in MBR partitioning. If you have sda4 inside the extended it will report errors.
So extended ends at 6349851789 and sda4 starts at 634986496 and ends just before end of drive.

Drive:
255 heads, 63 sectors/track, 121601 cylinders, total [COLOR=Red]1953525168[/COLOR] sectors

Device Boot Start End Blocks Id System
/dev/sda3 200706048 [COLOR=Blue]634985189[/COLOR] 217139571 5 Extended
/dev/sda4 [COLOR=Blue]634986496[/COLOR] [COLOR=Red]1953523711[/COLOR] 659268608 7 HPFS/NTFS/exFATok, thanks for the correction.

---

### Post by Erraten on 2012-11-15
Hello Everyone
I wanted to post a screenshot from gparted, but I can find a quick way to upload it.
The partitions sda1 sda2 and sda4 are primary. (System reserved, Windows and data)
sda5 sda6 and sda7 are inside the extended partition sda3 (all the linux stuff).
**Before** I had the sda4 also as part of sda3 inside the extended partition, but I changed it because I thought it might be the root cause for the slow drive.

Yesterday I ran the chdks and it came back with no errors. the (windows) defrag shows me 16% fragmentation. That doesn't seem too bad (not too good either, I know) - I will download a good free defrag to run it and try again. Don't think that is it though.. :(

Cheers,

Paul

---

### Post by Bucky Ball on 2012-11-15
Just attach the screenshot by using the paperclip icon in 'Go Advanced'. Don't put it in the body of your post, please. ;)

---

### Post by audiomick on 2012-11-15
> **dannyboy79 said:**
> sda4,... part of the extended partition.

I think following posts have sorted this, but just for the record, this can't be true. Logical partitions, i.e. those inside the extended partition, always start with sdx5. See, for instance, here

[http://tldp.org/HOWTO/html_single/Partition/#logical]("http://tldp.org/HOWTO/html_single/Partition/#logical")
in section 2.1.3. Logical Partitions

The numbers sda1 to sda4 (or sdb or sdc or whatever) are all primary or extended partitions. All higher numbers are logical partitions.

---

### Post by Erraten on 2012-11-20
Alright Gents, here it comes.
After playing with it some more I figured that onl some folders are slow, others not. Also the more stuff I installed, the problem occurs in C-drive as well.
The first folders on the list in Explorer work fine, the later ones don't. Then I tried to acess with keyboard instead of mouse by coincident and IT WORKED!
talked to a mate after re-installing the mouse driver didn't help and got a hint that the graphics driver might
Be the root cause. After de-installing that it works now fine at all times.

Here in short:

The problem is solved - reason was the broken graphics driver in Windows which explains why in Linux all was fine.

Thank you all for your time and support.

P.S. Still can't get the screenshot up - but  can assure you that I have only four primaries and the rest are logical, if they are called sdx or not.
Audiomick: your post contradicts itself. You say everything above sda4 should be extended and logical AND called sdx. I have higher numbers than sda4, so they should be logical but they are not called sdax5.. This is a different topic, so maybe you can reply by message.
Thank you.

---

### Post by Bucky Ball on 2012-11-20
Please mark thread as 'Solved' from Thread Tools at top right and post a new thread regarding any further issues rather than burying them here where you limit your chances of help. ;)

---

### Post by Parker32 on 2012-11-21
If this is a UEFI system, then reinstalling would be the quickest and straight forward way for getting a working installation. I recommend removing partitions sda5 through sda7, as they seem to be created by you. Then install Ubuntu from ubuntu-12.04-desktop-amd64.iso in UEFI mode (when selecting to boot from CD at boot time there should be two options for booting from CD one with UEFI and one without) to ensure that you're installing with UEFI support enabled. A partition layout with a Ubuntu partition and a separate home partition is a good choice. For using suspend to HDD (hibernate) you should choose at least the size of your RAM as the size of the swap partition. There is one additional step to be performed to re-enable hibernate in 12.04. After installation has finished you should have a Ubuntu with the grub-efi-amd64 package installed on your hard drive. The installer should have recognized the correct UEFI system partition (there is a specific GPT partition code for the UEFI system partition), put a grub-efi-stub in there and register it in the UEFI boot variables.

---

### Post by oldfred on 2012-11-21
Most of the new computers and almost all with Intel i-series chips have UEFI/BIOS systems. But if Windows7  is in BIOS mode, you would have to totally reinstall to convert from MBR to gpt partitioning. If system was sold in BIOS mode the recovery partition is sure to be BIOS mode also. 
But some Windows 7 and all Windows 8 systems are UEFI with gpt partitions.

So it can be difficult to convert from BIOS boot to UEFI boot. And all installed systems need to be installed in the same mode either both UEFI or both BIOS.

---

