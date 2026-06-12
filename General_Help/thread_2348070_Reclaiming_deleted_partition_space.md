---
title: "Reclaiming deleted partition space"
date: 2016-12-31
forum: General Help
---

### Post by RobGoss on 2016-12-31
Hello everyone, I have a machine with multi distributions on it and wanted to remove a few of the unwanted distributions and reclaim the deleted partition space

In Windows I know how to do this but Ubuntu is a little different and wanted to make sure I can regain the deleted space back. I know I can probably do it using Gparted

I'm currently using Ubuntu 16.04.01 if it makes any difference and this is a **Linux only **machine only no Windows

I would like to deleted unwanted partitions and add the** allocated space** back to my main Ubuntu 16.04.01 disk

Thanks so much for any help with this

---

### Post by Mark Phelps on 2016-12-31
Yes -- you can do this using GParted.

Just remove the partitions you no longer need.

But ... you can only then expand your Ubuntu 16.04.01 partition to include the new unallocated space if that space is adjacent to the partition.

---

### Post by yancek on 2016-12-31
If the partitions are not adjacent, you could also simply format them with a Linux filesystem and create a mount point for them on which to store data.  If some are logical partitions, you could run into problems if you delete a lower numbered partition as the partitions with higher numbers will then change.  If you have sda5, sda6 and sda7 and delete sda5, sda6 will become sda5 and sda7 will become sda6.

Posting the output of fdisk or a GParted image of the drive would give more details for someone to advise you if you have problems with it.  Also, GParted has an extremely detailed online manual at the link below.

 [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by Dennis N on 2016-12-31
A suggestion you might want to try:

If you have 2 or more physically separate unallocated spaces, you can create partitions for LVM physical volumes in those and join them into a single LVM volume group for data storage or other use.

---

### Post by oldfred on 2016-12-31
You do have to use the live installer's gparted or a gparted live.
You must have all partitions unmounted, so cannot run from your working install.
And live installer may mount swap, so you have to swapoff to unmount it.

And make sure your main working install is the default in MBR if BIOS or set in grub.cfg in ESP - efi system partition as correct partition to boot from.

       Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I prefer to use about 25GB for /(root) and then have large data partition which I can then mount in every install. Then I have same data in all installs.

---

### Post by RobGoss on 2016-12-31
> You do have to use the live installer's gparted or a gparted live.


**Fred**, So I can't just boot up my main Ubuntu 16.04 and remove the partitions that way does it have to be from the live installer?


> If you have 2 or more physically separate unallocated spaces, you can create partitions for LVM physical volumes in those and join them into a single LVM volume group for data storage or other use.

**Dennis**, I'm not to familiar with **LVM** volumes so would have to read up on it but appreciate you pointing this out


> Yes -- you can do this using GParted.

Just remove the partitions you no longer need.

But ... you can only then expand your Ubuntu 16.04.01 partition to include the new unallocated space if that space is adjacent to the partition.

**Mark**, I was think the same and had a understanding the process with be straight forward but I understand it's Linux and there maybe more to it

Thanks so much guys for the helpful tips, so is it much harder then mentioned above can I just delete a selected partition and just reclaim that space back to my main install which is 16.04? I know Fred stated it much more involved

---

### Post by RobGoss on 2016-12-31
> **yancek said:**
> If the partitions are not adjacent, you could also simply format them with a Linux filesystem and create a mount point for them on which to store data.  If some are logical partitions, you could run into problems if you delete a lower numbered partition as the partitions with higher numbers will then change.  If you have sda5, sda6 and sda7 and delete sda5, sda6 will become sda5 and sda7 will become sda6.

Posting the output of fdisk or a GParted image of the drive would give more details for someone to advise you if you have problems with it.  Also, GParted has an extremely detailed online manual at the link below.

 [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)



Here you go **Yancek** thanks so much

```
Usage:
 fdisk [options] <disk>      change partition table
 fdisk [options] -l [<disk>] list partition table(s)

Display or manipulate a disk partition table.

Options:
 -b, --sector-size <size>      physical and logical sector size
 -B, --protect-boot            don't erase bootbits when create a new label
 -c, --compatibility[=<mode>]  mode is 'dos' or 'nondos' (default)
 -L, --color[=<when>]          colorize output (auto, always or never)
                                 colors are enabled by default
 -l, --list                    display partitions end exit
 -o, --output <list>           output columns
 -t, --type <type>             recognize specified partition table type only
 -u, --units[=<unit>]          display units: 'cylinders' or 'sectors' (default)
 -s, --getsz                   display device size in 512-byte sectors [DEPRECATED]
     --bytes                   print SIZE in bytes rather than in human readable format

 -C, --cylinders <number>      specify the number of cylinders
 -H, --heads <number>          specify the number of heads
 -S, --sectors <number>        specify the number of sectors per track

 -h, --help     display this help and exit
 -V, --version  output version information and exit

Available columns (for -o):
 gpt: Device Start End Sectors Size Type Type-UUID Attrs Name UUID
 dos: Device Start End Sectors Cylinders Size Type Id Attrs Boot End-C/H/S
      Start-C/H/S
 bsd: Slice Start End Sectors Cylinders Size Type Bsize Cpg Fsize
 sgi: Device Start End Sectors Cylinders Size Type Id Attrs
 sun: Device Start End Sectors Cylinders Size Type Id Flags


 
```

---

### Post by Dennis N on 2016-12-31
> Dennis, I'm not to familiar with LVM volumes so would have to read up on it but appreciate you pointing this out

Since you seem open to this idea, I refer you to this guide that I learned from:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

An advantage is there is no risk to existing partitions with resizing or moving as they are untouched. 

Note: gparted will now format a partition as LVM as one of the options - the article says otherwise - is a bit old (but still valid in all respects).

---

### Post by RobGoss on 2016-12-31
> **Dennis N said:**
> Since you seem open to this idea, I refer you to this guide that I learned from:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

An advantage is there is no risk to existing partitions with resizing or moving as they are untouched. 

Note: gparted will now format a partition as LVM as one of the options - the article says otherwise - is a bit old (but still valid in all respects).



Thank you sir I will look it over and see what I can come up with I'm looking for the easiest way possible

---

### Post by Dennis N on 2016-12-31
And another article that I found helpful:

[http://www.linuxjournal.com/content/lvm-demystified](http://www.linuxjournal.com/content/lvm-demystified)

---

### Post by RobGoss on 2016-12-31
Thanks so much Dennis I will have a look

---

### Post by Keith_Helms on 2016-12-31
> **Fred**, So I can't just boot up my main Ubuntu 16.04 and remove the partitions that way does it have to be from the live installer?

You can remove partitions using the running system that are not in use by the running system.  Obviously you can't remove the partition that is mounted as /.  Anything else that is either not mounted to begin with or that you can manually unmount is fair game.  If you remove something that was listed in fstab, remember to remove that fstab entry before rebooting or you will probably get startup errors.

---

### Post by RobGoss on 2017-01-02
Thanks so much for all the advice much appreciated I will be working on this shortly

---

