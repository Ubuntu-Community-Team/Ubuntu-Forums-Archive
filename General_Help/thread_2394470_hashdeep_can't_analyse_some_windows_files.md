---
title: "hashdeep can't analyse some windows files"
date: 2018-06-16
forum: General Help
---

### Post by alex346 on 2018-06-16
Hello,

When coming to check integrity of linux backups, files, archives - the hashdeep CLI tool looks great.
It's old, but still awesome. I am using it long time and its very functional.

Now I have to save some desktops HDD images - through clonezilla and make the checkup process after that - HDD's from machines should be cleared/wiped.

Now, when I have the image, I have successfully restored the images on the virtual machines -vbox (under win, ubuntu) and onto the kvm on ubuntu.

The system after the restoration is bootable, is ok, boots. But I am booting through any livecd/partedmagic and starting the hashdeep -r [mountpoint].

[B]Hashdeep works for a while and holds. I have wait more than 7 days to check this. On different files - small ones, dat files, rather windows system files.
[/B]What is common - that are files with long paths, with whitespaces in the dirnames also.
I supposed the links problem, but that is happenning on C:\users\profile\appdata\roaming directory too, when hashdeep enters the C:\users path.
When the hashdeep holds the process is still live but it not consume the CPU.

ntfsfix not helps - I have thought about ntfs problems.
I can read this file, I also can remove it, but after the next starts, hashdeep holds on other similar file in the other directory.

I have spot this problems on all (I suppose) VM's configurations :

mounted hdd withd disabled cache
bios uefi/non-uefi

-Fu and -j0 switches on the hashdeep runs.

I have not changed the controller due the physical hosts has the SATA drives on SATA controllers.



**Did the someone has any idea what should I do more ?**



BTW - today Ive tried cvf - another CLI tool, It has similar behaviour.

---

### Post by alex346 on 2018-06-16
I suppose the problem with ntfs support in linux (in ubuntu also) - is that possible?

---

