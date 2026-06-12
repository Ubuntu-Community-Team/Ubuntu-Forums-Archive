---
title: "Disk fail/ file system corrupt at the installation on a new machine"
date: 2018-10-28
forum: General Help
---

### Post by neurogml on 2018-10-28
Hallo everyone! 
I`m new to linux operating systems and i would like to ask you some question/solutions for this problem:

[https://bit.ly/2PpCkac](https://bit.ly/2PpCkac)

it happens on every boot, shutdown and reboot of mine Dell XPS 15 9570 with i5-8xH and 256gb toshiba nvme, with 4 days of life.
The efi bios is up to date and the intel RAID is deactivated. The OS was always booting of course but not before a reboot due to this error.
As I understand that problem cames from the linux kernel that seems currupt, so i performed a reinstallation from 0 of the ubuntu OS. Nothing changed.
Then i got another ISO, and tried again but the error was still there. Then I tried with the Kubuntu ISO but nothing. 
Online I`ve red to perform a fsck that found 1 bad magic number in a block saying the ext2 was corrupted. I`v tried to correct it throught the `e2fsck` command (maybe it`s not the correct name but it is similar) but it didn`t worked. On reddit people said it was a hdd fail or ram fail(?) so i performed bot check with windows 10 (both healty) and kubuntu, mem was ok and nvme has ext2 currupted as stated before.

The strange thing happened when i deleted all the partitions with windows leaving 238gb no allocated space. Then I`ve mounted kubuntu and started it live, performing the fsck on the empty nvme and it showed the ext2 curruption! and it was the 3rd time i downloaded the kubuntu ISO! (with 2 ubuntu, no speaking 2 times windows)
I`ve also forgot to mention that sometimes in k/ubuntu (so not every boot of linux) happened a some kind of warning regarding missing drivers of the thunderbolt port in the bios, but it last less than a half second so  didn`t read it i time.

I don`t get it. Booting from a live usb already currupted? can you explain that to me pls?
I don`t have enough knoledge of computer science to diagnose that. I need a debian based OS for neurodebian.

By now I`ve installed windows with a VM becouse I need the pc.

---

### Post by x17andrew71x on 2018-10-28
Is this a new server or an existing one with data? If it is new, when going through the install process of an OS, what steps are you taking with the HDD?
Are you using the guided install? If so, are you selecting use entire disk and set up LVM? Or using the existing partitions?

You need to reformat the partition, removing the existing one and install the OS onto a fresh, clean format of the drive. The partitions seem messed up to me.
Just my initial thoughts upon reading.

Hope it helps.
-x17

---

### Post by neurogml on 2018-10-28
it's a new laptop.
I said deleted all the partitions when it was asked to me, and it started installing the os. And yes i've follow the guide instructions. No i didn't use LVM so, i suppose, using the existing partitions.

How i can check if there are a hidden partition/s?  the hdd should be of 256gb but it show 238gb maybe there is something corrupted in there i don't know.

Thank you for your help!

---

