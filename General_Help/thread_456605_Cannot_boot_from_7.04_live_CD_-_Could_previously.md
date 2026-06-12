---
title: "Cannot boot from 7.04 live CD - Could previously"
date: 2007-05-27
forum: General Help
---

### Post by Doc.Caliban on 2007-05-27
I booted my Dell XPS Gen2 laptop from the 7.04 live CD and it worked fine.  I installed Ubuntu and have been using it for a week or so.

I'm trying to boot from the CD again so that I can resize my partition, but it skips past the CD and boots from the hard drive.  The BIOS is configured properly, and I've even used the Dell boot menu to boot from the CD.  No luck.

Ideas?

-Doc

---

### Post by merlinus on 2007-05-27
Is it possible that the cd has been damaged?  Can you see the contents of it from windows?

-merlin

---

### Post by mmilitia9 on 2007-05-27
Just go to Applications>Add and Remove and search for GParted.  Install that so you can just partition without the CD right in Ubuntu.

Or redownload the CD

---

### Post by merlinus on 2007-05-27
If you are wanting to re-size your ubuntu partition, I do not hink this will work, as it cannot be unmounted whilst you are using it.

You will still need to boot from a live cd.

If you are wanting to re-size windows,  defrag it first, and then be sure to unmount the volume whilst in ubuntu.

Good luck!

-merlin

---

### Post by Doc.Caliban on 2007-05-28
Meh, I figured it out and it's too embarrassing to admit what I'd done.   Sorry to waste your time!

However, I did manage to boot and use Gparted.  I reduced the size of the partition by 15GB (it's a 100GB partition) and hit "Apply" a couple times.  It gave an error but the partition was in fact reduced in size.

Now the problem is that when I run install for XP (gotta play those games) it does not see an unused partition to install to as expected.  Ideas?

-Doc

---

### Post by merlinus on 2007-05-28
Generally it is best to install windows before ubuntu, as it expects to be on the first partition.

So if you have not done much configuring or downloading of linux apps, perhaps it is best to begin again, especially with everything you have already learned!

;)

-merlin

---

### Post by Wim Sturkenboom on 2007-05-28
> **Doc.Caliban said:**
> Meh, I figured it out and it's too embarrassing to admit what I'd done.   Sorry to waste your time!We promise we will not laugh :p . But others can learn from your mistakes so please let us know what went wrong.

---

### Post by Doc.Caliban on 2007-05-28
[This tutorial ]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")makes it look pretty easy.

---

### Post by Doc.Caliban on 2007-05-28
> **Wim Sturkenboom said:**
> We promise we will not laugh :p . But others can learn from your mistakes so please let us know what went wrong.


I'm only telling you this because it is in fact funny.  Mind you, I've been burning CD's since the blanks were $25 each and a single speed burner was over $1,000 to buy...

I wasn't paying attention to what I was doing and when I burned the disc again I ended up making a disc with the damn ISO file on it instead of burning the contents of the ISO onto it.

I'm filling out my ID 10 T form now.

-Doc

---

### Post by Doc.Caliban on 2007-05-28
> **Doc.Caliban said:**
> [This tutorial ]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")makes it look pretty easy.

One thing that's odd is this bit:

"The main partition of a standard Ubuntu installation is /dev/hda1"

Mine is /dev/**s**da1    Does that make sense?

-Doc

---

### Post by Wim Sturkenboom on 2007-05-28
Yep, if you have a SATA or SCSI disk.

---

### Post by Doc.Caliban on 2007-05-28
I just have IDE.  I'm not going to worry about it though since all the partitions look right and stuff.

---

### Post by merlinus on 2007-05-28
FWIW, I have one IDE drive, and all my partitions are sd rather than hd.  The hard drive is listed as sda.

No problems, though....

-merlin

---

### Post by strabes on 2007-05-28
In feisty I believe all disks are listed as "sdxx"

---

### Post by jimbob on 2007-05-28
Not so in my Feisty.  Here is output of fdisk on my Feisty system with one SATA and one PATA:

 fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2301    18482751   83  Linux
/dev/hda2            2302        2432     1052257+  82  Linux swap / Solaris
/dev/hda3            2433        4228    14426370   83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2549    20474811   83  Linux
/dev/sda2            9602        9729     1028160   82  Linux swap / Solaris
/dev/sda3            2550        5105    20531070   83  Linux
/dev/sda4            5106        9601    36114120   83  Linux

Partition table entries are not in disk order

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

