---
title: "Very slow SSD speeds (12.10)"
date: 2012-11-08
forum: General Help
---

### Post by bbuk89 on 2012-11-08
I recently upgraded my ultrabook to have a 128GB SSD (Crucial v4).

The speed of installing ubuntu was shockingly slow, worst i've ever experienced. Once installed i did some testing and the speeds show as being good and boot time is alright but when it comes to installing anything it is taking an absolute age.

Using apt-get is fine downloading, again when it comes to unpacking things go extremely slow (Took 10 minutes to install Terminator). Running firefox is becoming a burden as well.

Benchmark:

```
$ sudo hdparm -Tt /dev/sda

 /dev/sda:
 Timing cached reads:   12428 MB in  2.00 seconds = 6218.55 MB/sec
 Timing buffered disk reads: 718 MB in  3.01 seconds = 238.78 MB/sec
Ultrabook Specs:
```

Intel i5-3317U
4GB RAM
128gb Crucial v4 SSD
Any help would be greatly appreciated.

Many thanks

---

### Post by oldfred on 2012-11-08
Welcome to the forums.

My install to SSD from ISO on hard drive was about 9 minutes.

My SSD is a low cost OEM Microcenter SSD, so not fast as yours.

fred@fred-Precise:~$ sudo hdparm -Tt /dev/sdd
[sudo] password for fred: 

/dev/sdd:
 Timing cached reads:   8660 MB in  2.00 seconds = 4338.05 MB/sec
 Timing buffered disk reads: 548 MB in  3.01 seconds = 182.14 MB/sec

It seems like it may be processor? But I have an older dual core with 4GB of RAM, so you should be getting good speeds.

Have you turned AHCI on in BIOS? Made some settings in fstab to reduce writes?

Have you checked  resources in System Monitor or top to see if some process is using up everything?

---

### Post by dcstar on 2012-11-09
> **bbuk89 said:**
> I recently upgraded my ultrabook to have a 128GB SSD (Crucial v4).

The speed of installing ubuntu was shockingly slow, worst i've ever experienced. Once installed i did some testing and the speeds show as being good and boot time is alright but when it comes to installing anything it is taking an absolute age.
.......
Any help would be greatly appreciated.

Many thanks

Be aware that you cannot just reuse SSDs in the same way as normal rotational drives.

If a SSD has been used previously with a non-TRIM aware filesystem or OS then all the writeable blocks will eventually get consumed and the SSD will be forced into the slow real-time READ-ERASE-WRITE procedure instead of the quicker WRITE procedure (this is an over-simplified explanation, do a web search for the full story).

**Just deleting partitions is not going to do the job!** You may need to manually run the wiper.sh command to tell the SSD what to clean up:

[http://ubuntuforums.org/showthread.php?t=1490602](http://ubuntuforums.org/showthread.php?t=1490602)

If ever doing a full reinstall on a SSD it is always recommended to do a total ATA Erase of the device using the tools provided by the manufacturer.

You also **must** have the "discard" option set in your /etc/fstab file.

---

### Post by antoine on 2012-11-21
I have the same problem, also with a Crucial V4 SSD.

I wanted to use it as a replacement for a 5400 rpm HDD, but I put the HDD back, since the SSD was slower.

Ubuntu was also very slow to install (about 2 hours), and installing the updates took even more time. 
Downloading the files was fast, but uncompressing/installing the packets was very slow, with iotop giving transfer speed in Kb/s.

Benchmarking the drive with the disk utility from ubuntu 12.10 gave me the following results:
251 Mb/s read speed
21 Mb/s write speed

It seems that the read speed is OK, but the write speed seems very bad (the HDD on my desktop computer has a 80Mb/s write speed, which is nearly four time faster).

However, I am not sure this is a problem with Ubuntu, as I also tried the drive with windows 7, and the computer also felt slower than with the HDD (although I would be happy if someone found a solution).

---

### Post by Mark Phelps on 2012-11-21
I was having similar problems with my Crucial 128GB M4 SSD.  Ran a speedtest on it and was getting less than half the performance expected.  

Then, I was reading through the Crucial SSD forums and found a thread that described the problem -- the SSD partitions weren't aligned properly.

I did that by using a free alignment utility -- but those generally only run in Windows.

You should search through the Crucial forums to see if anyone knows a utility you can run in Linux or run from a boot CD.

---

### Post by oldfred on 2012-11-21
Did you change a few settings to reduce writes and journal. Install would still be slower but on my system it was 9 minutes and it is a slow SSD.

       With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler
# to see what scheduler you are using:

       fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

Older versions with issues.
       Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

    [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

    If you use a recent copy of gparted to partition, it will use correct alignment. 
       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by SlugSlug on 2012-11-21
adding discard to my ssd killed performance when deleting loads of files. Instead I'd recommend fstrim via weekly cron.

Alignment can be done in live disk / gparted
[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)

the difference to me was a couple of MB/s  - not much

Also I did not bother with all not no access time etc etc today's SSD's can be written too by some say as much as a HDD so there is no real point trying to stop writes

AHCI is the main one to look at (in BIOS)

---

### Post by SlugSlug on 2012-11-21
what do you get from

Make sure you have 9GB free on /
```
dd if=/dev/zero of=/tmp/output bs=8k count=1000k
```mines

```
1024000+0 records in
1024000+0 records out
8388608000 bytes (8.4 GB) copied, 35.8142 s, 234 MB/s


```

---

### Post by SlugSlug on 2012-11-21
an the other way 

```
dd if=/tmp/output of=/dev/null bs=8k
1024000+0 records in
1024000+0 records out
8388608000 bytes (8.4 GB) copied, 25.8014 s, 325 MB/s
```

---

### Post by jim_deadlock on 2012-11-21
One other thing that nobody has mentioned yet, you should connect your SSD to the SATA3 (6Gb) connector on your motherboard to gain the maximum speed.

---

### Post by SlugSlug on 2012-11-21
am still on SATA2 :(

---

### Post by antoine on 2012-11-21
Thank you for all the advices. I have recreated the main partition with gparted to ensure that it is correctly aligned.
I have created it as a ext2 filesystem, and it looks Ok (the start of the partition is at 2048)

Here is the output of the fdisk program:

```
root@goto10:/home/antoine# fdisk /dev/sdc

Commande (m pour l'aide): p

Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 têtes, 63 secteurs/piste, 15566 cylindres, total 250069680 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets
taille d'E/S (minimale / optimale)*: 512*octets / 512*octets
Identifiant de disque*: 0x5ecdbc60

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdc1            2048   250068991   125033472   83  Linux
```

It looks OK to me, the start of the partition is 2048 .

I have not used the "discard" mount option as it looks like it is not recognised for the ext2 filesystem.

Here is the output of 

```
root@goto10:~# dd if=/dev/zero of=/mnt/output bs=8k count=1000k
1024000+0 enregistrements lus
1024000+0 enregistrements écrits
8388608000 octets (8,4 GB) copiés, 47,1802 s, 178 MB/s
```
And the other way

```
root@goto10:~# dd if=/mnt/output of=/dev/null bs=8k
1024000+0 enregistrements lus
1024000+0 enregistrements écrits
8388608000 octets (8,4 GB) copiés, 31,4607 s, 267 MB/s

```

I have also tried copying the file
```
root@goto10:~# dd if=/mnt/output of=/mnt/output2 bs=8k
1024000+0 enregistrements lus
1024000+0 enregistrements écrits
8388608000 octets (8,4 GB) copiés, 72,5745 s, 116 MB/s
```

Those speeds look faster than what I had (not very fast for a SSD, but still faster than my HDD).

However, the disk benchmark tool of Ubuntu still provides the following values:
Read speed: 260 Mb/s
Write speed: 19,7 Mb/s 
(it looks like the write speed is becoming smaller each time the bench is run).

Regarding the SATA port, I think I only have SATA 3Gb ports on my motherboard (asus P8H61).

I will try reinstalling ubuntu on the disk with those parameters to see if its better, and post the result after it is done (or canceled if it takes too much time).

---

### Post by antoine on 2012-11-21
I installed ubuntu 12.10 on the ext2 partition previously created, and I had no problem installing and applying the updates. In fact, I couldn't believe my computer was so fast. 

I then tried installing ubuntu 12.04 (this was the version I tried to install the first time), and it also installed quickly with quick apt-get updates.

In my case, I am really glad to see that this disk can work correctly. 

I will try putting it back in my laptop and reinstalling with a swap partition on the disk.

---

### Post by SlugSlug on 2012-11-21
yer  you should have some swap. may I ask why ext2? ext4 is fine

---

### Post by antoine on 2012-11-21
In fact, I have used ext2 because of oldfred response:
> With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
ext2 seemed to be simpler to setup for a test, but now that I know that the drive is working correctly, I now plan to reinstall with swap and ext4.

---

### Post by oldfred on 2012-11-21
I will have to update my notes. Several users have posted issues with 12.10 and ext2, not just with SSD. May be a bug?

Some swap is suggested, but unless hibernating you do not need a lot. And if you have a lot of RAM you may never use it.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by SlugSlug on 2012-11-22
Some good info here
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by antoine on 2012-11-22
Hello,

I have re-installed with a swap partition, and I think I can confirm that the problem (at least in my case) was caused by the journalling:
I first reinstalled with the new partition layout, and used ext4 with the default installer option. The install was slow (file copy was fast, but the final configuration steps were slow), and the first boot was also slow (probably slower than with the HDD).

Then I reinstalled with the new partition layout, and an ext2 filesystem. The install was very fast, and the boot was really quick.

I then tried with btrfs. The install was slow, but booting the installed system was quite fast (not as fast as with ext2, but faster than with ext4).

I finally reinstalled with ext4, but instead of using the partition tool from the ubuntu installer, I used gparted and tune2fs to turn off journaling.
The install was fast, and the boot was also fast.

I haven't installed the updates yet, because my internet connection at home is currently down. However, it looks like journaling is incurring a huge performance penalty.

---

### Post by oldfred on 2012-11-22
Understand that we turn journaling off on a boot partition for speed, but the trade off is reliability. Without journal fsck will be slow, but if partition is small that is not a huge penalty. But major issues that journal would allow fixes then may not be fixable.

If just a boot drive then reinstalling system is not a big deal. But if storing any important data backup is more important.

---

### Post by SlugSlug on 2012-11-23
I Also read on that arch wiki a power outage has higher chance of corrupting  your data

---

