---
title: "External Hard Drive Suddenly Won't Mount"
date: 2024-11-10
forum: General Help
---

### Post by junglejh on 2024-11-10
SOLVED - see below

I have a Seagate External 2TB hard drive called Outback.

I have used it with Linuxmint, Kubuntu and Windows operating systems for a few years. 
Flawless mounting and use until a few days ago. 

An error occurred while accessing 'Outback' in both Kubuntu and LinuxMint, ..... 

"the system responded: The requested operation has failed: Error mounting /dev/sdc1 at /media/jungle/Outback: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error."

I closed down again and tried again and got the same error message. 
I closed down again and restarted with LinuxMint (current version) and got exactly the same error message.
I closed down again and restarted with Windows 10 and this portable drive opened just fine.
I tried both Linuxmint and Kubuntu again and continue getting the same error message.

I use this as a backup hard drive, and quite desperately want both Linuxmint and Kubuntu to regain access. 
I have had some help from the Linuxmint Forum and can now access this external hard drive following this advice...
1. Run Disks app.
2. Select problematic disk.
3. Click the cog wheel.
4. Edit Mount Options&#8230;.
5. Turn off User Session Defaults.

I still get the same error message in Kubuntu. It doesn't have a similar Control Panel with a Disks app. 

Very much appreciate some advice on how to access this SSD when in Kubuntu.

---

### Post by junglejh on 2024-11-11
Problem solved. 

I downloaded and installed Disks which is a disk management utlity used by Ubuntu and LinuxMint .
I followed the instructions above (no cog wheel just a play symbol on the left hand side which leads you to 'Edit Mount Options' where you can turn off the User Session Defaults and it solves the problem.

---

### Post by julian552 on 2024-11-20
Hi, thanks for the reply, it helps me too !


[RIGHT][SUB][[COLOR=#a9a9a9][SIZE=1]snaptube[/SIZE][/COLOR]]("https://snaptube.cam/") [[COLOR=#a9a9a9][SIZE=1]vidmate[/SIZE][/COLOR]]("https://vidmate.bid/")[/SUB][/RIGHT]

---

