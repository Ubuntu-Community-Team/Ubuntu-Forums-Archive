---
title: "Uninstalling Linux...."
date: 2005-10-14
forum: General Help
---

### Post by Mazza558 on 2005-10-14
I've had a play with Ubuntu, but it doesn't support my wireless card, so I'm trying to uninstall it. Note that the MBR has the boot loader that came with Ubuntu on it. This means that if I try to delete the partition with Ubuntu on it I get an "Error 22" message. I have XP Home Installed on my primary partition and Ubuntu is on a logical partition. So, how do I unintall Ubuntu, or possibly restore the MBR to Windows default?

---

### Post by rikai on 2005-10-14
1. Boot to MS-DOS, and then type the following:
fdisk /mbr
2. Restart your computer.
3. Delete the linux partiton using fdisk, recreate it, and format it in windows.

and you're done.

---

### Post by Mazza558 on 2005-10-14
I have nothing to boot to MS-DOS with. Are you saying that It will format the HDD as well?

---

### Post by egnaro on 2005-10-14
Put in your XP cd. Boot off of it. Enter the Repair console when available. From the repair console type fixmbr. now the windows xp loader will be back.

---

### Post by Mazza558 on 2005-10-15
There's a problem in that I don't actually have a windows XP CD because my PC has a seperate partition with "HP PC System Recovery" on it. I've been trying to find an XP boot CD. If I restore the MBR, will I still be able to boot linux if I wanted to try a different distro?

---

### Post by metoo on 2005-10-15
Mazza558,

you should be able to create a start-disk from you running Windows System. If you cannot find it in Explorer/Systemsettings/right click on desktop + properties... search the web where this function is actually located. Well this is, if you still have a floppy drive in your computer.

However, if you want to try a different linux distribution anyway  (SuSE 10.0 came out recently, they usually have good hardware support + a web database showing supported hardware to check first), why de-installing at all? Leave everything as it is.
You can still boot into Windows and when you found another distribution, just install it over ubuntu. The installer of the other distribution will clean/format ubuntu's partition and update grub accordingly.

---

### Post by joelito on 2005-10-15
Just for curiosity, what's the make and model of your wireless card? That way i know what not to buy. You may also try something called ndiswrapper that allows you to install windows drivers(not the best solution but *sometimes* works, i must also state that I've never used it so I don't know much furter)

---

### Post by chamaeleon on 2005-10-15
If you want to clean the mbr go to:

 >start>programs>acessories>system utilities (or something like that)>command line (or dos shell or whatever), then

c:\fdisk /mbr

then you're done! MBR is cleaned. 

Don't worry about Windows because it'll start, you just clean the MBR. Then you could use a partition program to get the space from the linux install.

---

### Post by Mazza558 on 2005-10-15
Well I've got out of this mess finally. I've decided to leave installing another linux distro till sometime in the future. I found a nifty program to restore MBR back to default. I then used partition magic to format and remove the linux partition. I'm keeping it back as it was for now because I know I'll screw my system up if I try to install another linux distro.

---

### Post by shrik on 2005-11-25
[QUOTE=Mazza558]Well I've got out of this mess finally. I've decided to leave installing another linux distro till sometime in the future. I found a nifty program to restore MBR back to default. I then used partition magic to format and remove the linux partition. I'm keeping it back as it was for now because I know I'll screw my system up if I try to install another linux distro.[/QUOTE]

Could you please tell me what this nifty program was? I've had Ubuntu 5.10 on my system for quite a while now without it being used, and want to get rid of it for now.

Thanks.

---

### Post by leetcharmer on 2005-11-25
[www.bootdisk.com](www.bootdisk.com)

get a win98se bootdisk, then pop it in and fdisk /mbr

---

### Post by shania98 on 2006-01-26
[QUOTE=leetcharmer][www.bootdisk.com](www.bootdisk.com)

get a win98se bootdisk, then pop it in and fdisk /mbr[/QUOTE]
Hi
i've been trying to repartition my master drive. have done the "fdisk/mbr
but still will not partition with FAT32. any ideas? Thanks all!

---

### Post by shania98 on 2006-01-26
oh forgot to mention i think some remains of grub may be the culprint
is grub infecting my mbr?

---

### Post by manicka on 2006-01-26
Grub can't 'infect' anything. 
What problems are you having with your partitioning? What are the error messages?

---

### Post by shania98 on 2006-01-26
[QUOTE=manicka]Grub can't 'infect' anything. 
What problems are you having with your partitioning? What are the error messages?[/QUOTE]

this is in relation to winSE fdisk i'm trying fdisk my hd0 master
i can partition but it comes out w/ no fat32 
thank for looking at my question

---

### Post by Robor on 2006-01-26
[QUOTE=shania98]this is in relation to winSE fdisk i'm trying fdisk my hd0 master
i can partition but it comes out w/ no fat32 
thank for looking at my question[/QUOTE]
It sounds like you're trying to format rather than partition.

---

### Post by shania98 on 2006-01-26
[QUOTE=Robor]It sounds like you're trying to format rather than partition.[/QUOTE]
Yes that's it! sorry

---

### Post by shania98 on 2006-01-26
[QUOTE=shania98]Yes that's it! sorry[/QUOTE]

well i can partition but there's no FAT32, so I can format
I need fat32 to format

---

### Post by Robor on 2006-01-27
Is your system able to boot into Windows?  If so, just go to Disk Management and delete the partition there.  After that, create a new partition/volume and format it as desired.

---

### Post by martialartist81 on 2007-01-24
So, I have WinXP as my "main" drive, so if I go into Disk Management and delete the Linux particition... will I be able to boot directly into windows and GRUB disappears?

---

