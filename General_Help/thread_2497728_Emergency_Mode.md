---
title: "Emergency Mode"
date: 2024-05-15
forum: General Help
---

### Post by daniell59 on 2024-05-15
What is Emergency Mode and how do I get out of it?

Thanks in advance

---

### Post by Bashing-om on 2024-05-15
Hey daniell59

> 
What is Emergency Mode and how do I get out of it?


Well - emergency mode happens - when the kernel ooopps or you can not boot anything else - or that boot parameter is set.
Where you are at now and how you got there depends on how to get out of it.
We need the back ground details in order to advise on what to do. what specifically happens when you boot up ?

-ain't where I can look over your shoulder :D -

---

### Post by daniell59 on 2024-05-16
> **Bashing-om said:**
> Hey daniell59



Well - emergency mode happens - when the kernel ooopps or you can not boot anything else - or that boot parameter is set.
Where you are at now and how you got there depends on how to get out of it.
We need the back ground details in order to advise on what to do. what specifically happens when you boot up ?

-ain't where I can look over your shoulder :D -
Thanks for input.
Yesterday for many hours my internet was down. The problem occurred when  it was restored. Since I wanted to upgrade form Ubuntu 22.04 to 24.04, this is what I will do. Reluctantly I admit that I don't have the capacity to remedy the problem otherwise.

---

### Post by daniell59 on 2024-05-16
I had some difficulty installing Ubuntu 24.04. The OS would not install on my solid state drive. I tried an old hard drive. It installed without a problem. Does this mean that the solid state drive is no longer functional?

---

### Post by Bashing-om on 2024-05-16
daniell59; Yukkie :(

> 
Does this mean that the solid state drive is no longer functional?

Maybe yes - maybe no;
we need some diagnostic information,
For starters does Bios see the SSD when booting up the system ?
From the Hard drive install what shows:
```

sudo fdisk -lu

```

-all we are doing is looking to know-

---

### Post by daniell59 on 2024-05-17
Disk /dev/loop0: 55.66 MiB, 58363904 bytes, 113992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 74.24 MiB, 77844480 bytes, 152040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 269.63 MiB, 282722304 bytes, 552192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 10.72 MiB, 11239424 bytes, 21952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 505.09 MiB, 529625088 bytes, 1034424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 10.32 MiB, 10821632 bytes, 21136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.05 GiB, 160041885696 bytes, 312581808 sectors
Disk model: WDC WD1600AAJS-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8DB5B5D3-D72F-443E-9214-3B967B43693D

Device     Start       End   Sectors  Size Type
/dev/sda1   2048      4095      2048    1M BIOS boot
/dev/sda2   4096 312578047 312573952  149G Linux filesystem


Disk /dev/loop8: 38.73 MiB, 40615936 bytes, 79328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 476 KiB, 487424 bytes, 952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 137.29 MiB, 143962112 bytes, 281176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 321.1 MiB, 336699392 bytes, 657616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
daniel@daniel-N68SA-M2S:~$ 

Yes the BIOS did detect the SSD. There were numerous errors being generated.
The installed drive is very old. It will serve me until my new system is up and running.

---

### Post by Bashing-om on 2024-05-17
daniell59; ouch

Only seeing the one drive - does not look good for the home team.
Anything from:
```

sudo blkid -c /dev/null -o list

```
Where The switch "-c /dev/null" ensures the command is not using any cached values and polls all of your hardware directly. The "-o list" switch is an option to order the output for easier reading.

If the kernel does not see the drive

[INDENT]we got a problem
[/INDENT]

---

### Post by daniell59 on 2024-05-17
> **Bashing-om said:**
> daniell59; ouch

Only seeing the one drive - does not look good for the home team.
Anything from:
```

sudo blkid -c /dev/null -o list

```
Where The switch "-c /dev/null" ensures the command is not using any cached values and polls all of your hardware directly. The "-o list" switch is an option to order the output for easier reading.

If the kernel does not see the drive

[INDENT]we got a problem
[/INDENT]
Thanks for your informative reply.
I had been using the SSD for several years. Then I developed a problem. Emergency mode. After that I could not reinstall the OS.

---

### Post by daniell59 on 2024-05-17
> **Bashing-om said:**
> daniell59; ouch

Only seeing the one drive - does not look good for the home team.
Anything from:
```

sudo blkid -c /dev/null -o list

```
Where The switch "-c /dev/null" ensures the command is not using any cached values and polls all of your hardware directly. The "-o list" switch is an option to order the output for easier reading.

If the kernel does not see the drive

[INDENT]we got a problem
[/INDENT]
/dev/loop1 squashfs         /snap/bare/5   
/dev/loop8 squashfs         /snap/snapd/21465 
/dev/loop6 squashfs         /snap/gtk-common-themes/1535 
/dev/loop4 squashfs         /snap/firmware-updater/127 
/dev/loop11
           squashfs         /snap/vlc/3777 
/dev/loop2 squashfs         /snap/core22/1380 
/dev/loop0 squashfs         /snap/core18/2823 
/dev/loop9 squashfs         /snap/snapd-desktop-integration/157 
/dev/loop7 squashfs         /snap/snap-store/1124 
/dev/sda2  ext4             /              09fb685f-6f03-4e0f-a434-9b9fb491d82a
/dev/sda1                   (not mounted)  
/dev/loop5 squashfs         /snap/gnome-42-2204/176 
/dev/loop3 squashfs         /snap/firefox/4173 
/dev/loop10
           squashfs         /snap/thunderbird/470

---

### Post by Bashing-om on 2024-05-17
daniell59; Ouch X10 - yukkie poo !

As even blkid does not see the drive - it is beyond my skill set to advise on what one can do to rescue the SSD.
Perhaps others here have some experience in such a situation.

[INDENT]a know-it-all I am not
[/INDENT]

---

### Post by daniell59 on 2024-05-17
> **Bashing-om said:**
> daniell59; Ouch X10 - yukkie poo !

As even blkid does not see the drive - it is beyond my skill set to advise on what one can do to rescue the SSD.
Perhaps others here have some experience in such a situation.

[INDENT]a know-it-all I am not
[/INDENT]

Thanks
It's an inexpensive drive and soon I will buy another SSD.

---

### Post by Bashing-om on 2024-05-18
daniell59; After thought !

How about a bad SATA cable ? How tough is it to open the box and swap the SATA cables between the drives - and maybe swap to a different SATA port - if there are other ports not used?


[INDENT]Maybe Yes
[INDENT]could be not so yes
[/INDENT][/INDENT]

---

### Post by daniell59 on 2024-05-18
> **Bashing-om said:**
> daniell59; After thought !

How about a bad SATA cable ? How tough is it to open the box and swap the SATA cables between the drives - and maybe swap to a different SATA port - if there are other ports not used?


[INDENT]Maybe Yes
[INDENT]could be not so yes
[/INDENT][/INDENT]

Worth a try
Is there anyway to evaluate the SSD without it having an installed OS?

---

### Post by Bashing-om on 2024-05-18
daniell59;

Got me there - I have never considered looking at a drive that has no installed OS.
I seriously doubt that any tool can work so long as Bios can not see that SSD.

[INDENT]your guess here is as good as mine
[/INDENT]

---

### Post by daniell59 on 2024-05-25
I just had success installing Ubuntu 24.04 into my SSD. I used a different SATA port and a different cable. As has been the case, I would not have thought of it without the assistance of the Ubuntu forum.

---

