---
title: "Create extended partition on HD with 4 primary partitions already - options please?"
date: 2017-08-18
forum: General Help
---

### Post by fiddybux on 2017-08-18
Hi all,

I want to add a 3rd Linux OS to my system. I do not want to install different desktop environments onto my existing Ubuntu install - I've had serious pains with that whole malarkey!

I have the following:

```

sda1    dos    100.00  gb    windows        primary
sda2    swap   4.00    gb    swap           primary
sda3    /      15.00   gb    ubuntu root    primary
sda4    /home  113.88  gb    ubuntu home    primary

```

Therein lies the problem; I have 4 x primary partitions already and no way to easily create an extended partition so I can then add further logical partitions to it.

I got as far as this before I realised my mistake when I initially setup this computer about 7 years ago! I've used gparted to shrink sda4. This is where I am up to right now - this moment.

```

sda1    dos      100.00   gb        windows         primary
sda2    swap     4.00     gb        swap            primary
sda3    /        15.00    gb        ubuntu root     primary
sda4    /home    [COLOR="#0000CD"]49.88[/COLOR]    gb        ubuntu home     primary
[COLOR="#FF0000"]unallocated      64.00    gb        unallocated     none[/COLOR]

```

As you can see, I made a bit of space thinking I could create an extended partition, before I hit this issue.

The HD uses MBR (not GPT) so I am unfortunately limited to 4 primary partitions. Unless it is risk free (or very low risk), I do not want to convert to GPT. I'm pretty sure it would involve a lot of moving partitions side to side and so forth (creation of UEFI, Boot Partition etc). If, however, converting to GPT is relatively painless and straightforward, then I'm happy to go down this route if someone can convince me otherwise - I'm no expert, which is why I'm asking! ;)

Failing the GPT route, I think I've got two choices:

1. Backup /home on sda4, delete it, create an extended in it's place, rebuild /home (edit UUIDs in /etc/fstab etc to reflect the new drive UUID etc.), and hope for the best! A lot of work, and no working Ubuntu install while I do it, so all done through Windows or Live media (systemrescuecd, for example).

2. Possibly, just possibly, could I delete the /swap partition on /sda2 (it's much safer to do that and easier to put back afterwards I think), and then make what was formerly sda2 into an extended partition, and create logical drives associated with that?

The main problem I can see with option 2, is that something is telling me that the logical partitions created in the former sda2 slot would be limited to 4GB, is this right?

Or can I, by some magic, shrink sda4 by say 50GB and then link a logical drive to an extended partition where sda2 used to be? So, the 4GB "placeholder" if you like, links to a 50GB block of disk space that I can split up how I want. I think not, but hey, this is why I'm asking!

Or am I basically stuffed here, and the only viable (albeit difficult) choice is option 1?

Is there an option 3 I haven't considered?

Thanks.

---

### Post by Dennis N on 2017-08-18
I would use gparted from a live media, and delete sda2, leaving uallocated space. Then you have only 3 primary partitions, so in the big 64 gB unallocated space you should now be able to make a 64 gB extended partition. You can make logical partitions inside the extended partition you created. One of the logical partitions would a new swap partition. You would also have to edit ubuntu's /etc/fstab to change the details of the swap partition.

---

### Post by oldfred on 2017-08-18
+1 on Dennis N's suggestion.

But you can use gpt with BIOS boot. I did from about 2010 until my first UEFI system years later.
You do need to add a bios_grub partition for grub to correctly install with gpt for BIOS booting and have to reinstall grub.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[URL="http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr"]http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr

[/URL]
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 
   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 

[URL="http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr"]
[/URL]

---

### Post by fiddybux on 2017-08-19
> **Dennis N said:**
> I would use gparted from a live media, and delete sda2, leaving uallocated space. Then you have only 3 primary partitions, so in the big 64 gB unallocated space you should now be able to make a 64 gB extended partition. You can make logical partitions inside the extended partition you created. One of the logical partitions would a new swap partition. You would also have to edit ubuntu's /etc/fstab to change the details of the swap partition.

That is a great idea. Thank you! I don't know why I didn't think of that, so simple. It was getting late and I was tired I suppose!

I suppose then I could grow sda1 to use the 4gb space remaining from the swap, or move sda3 and sda4 left a bit, which would be a longer (more risky) process, but ultimately more useful to me and tidier too.

Thinking about it, I'll grow sda1 (windows) because then it's easier to reverse the whole process in the event that I ever want a larger partition for my Ubuntu /home again (sda4), and I can then shrink sda1 to recreate my swap again.

Don't think I'll bother with gpt at this time. There won't be any performance advantages, so it doesn't seem worth it.

Now to decide on OS...torn between Debian and Arch. Don't suppose there's an Archbuntu is there? Haha.

Thanks both.

---

### Post by johndough2 on 2017-08-19
Hi

Option 3? Is there a possibility of a larger HDD replacement or additional one?

Then clone verything over?

---

### Post by fiddybux on 2017-08-19
> **johndough2 said:**
> Hi

Option 3? Is there a possibility of a larger HDD replacement or additional one?

Then clone verything over?

Not really I'm afraid, but thanks for the suggestion all the same.

---

### Post by fiddybux on 2017-08-19
Worked like a charm...just placed my swap right at the end, set the UUID in /etc/fstab, and we're all back up and running.

Decided to grow sda1, as it is basically much quicker than moving sda3.

```

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  112GB  112GB   primary   ntfs            boot
 3      112GB   128GB  16.1GB  primary   ext4
 4      128GB   181GB  53.6GB  primary   ext4
 2      181GB   250GB  68.7GB  extended
 5      181GB   197GB  16.1GB  logical   ext4
 6      197GB   246GB  48.3GB  logical   ext4
 7      246GB   250GB  4294MB  logical   linux-swap(v1)

```

Thanks peeps!

---

