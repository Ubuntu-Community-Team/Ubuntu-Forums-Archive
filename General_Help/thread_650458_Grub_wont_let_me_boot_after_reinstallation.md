---
title: "Grub wont let me boot after reinstallation"
date: 2007-12-26
forum: General Help
---

### Post by Hubster on 2007-12-26
Hi (And happy xmas and new year, that kinda thing)

I reinstalled Ubuntu on my PC this afternoon, along with XP, but now I can't boot at all! I just get an error message. 

The first time I reinstalled all seemed to go well - first XP and then Ubuntu, but when I rebooted GRUB listed XP twice and wouldn't boot anything. I tried to re reinstall again, making sure that I deleted all partitions on the whole disk first, then re reinstalling XP followed by Ubuntu, only to end up with XP listed three times and still nothing working, just the error message 'Grub error 17' or something like that.

So again I wiped the disk and started the whole thing again, this time using the XP set up disk formating utility, which seemed to boot fine - no sign of GRUB - until I got greedy and tried to put Ubuntu back on the second partition. Now I get a blackscreen and 'error loading operating system'

The computer has two drives in, with the second drive being partitioned twice with one partition to hold each OS. Maybe I need to nuke GRUB or the MBR? Any suggestions how please?

Thanks

---

### Post by LaRoza on 2007-12-26
I am not sure exactly what the problem is, but you can restore the Windows MBR with the Super Grub Disk (see thie link in my sig)

You boot from it, and chose:

Advanced->Windows (Advanced) and the option to restore the MBR (I think it is the first)

After you get Windows working, we'll worry about getting a dual boot working.

---

### Post by Hubster on 2007-12-26
Hey, thanks for the advice :)

I got that program and have the disk working now but I still can't get it working. 

For Ubuntu I get ' Error `7: cannot mount partition'

For Xp I get : Invalid or unsupported format
and for the second XP listed is says Error 12: Invalid device reuested.

The weird thing is I can run XP on its own fine as long as I have no ubuntu on here, its just when I try to dual boot. I wipe the disk clean of all partitions and install XP - works great. 

When I finish installing Ubuntu though, at the install Grub loader screen it says it can detect XP twice, even though it should only be on there once. It still says there is XP on the drive even when I install Ubuntu with no XP on the drive at all. :confused:

---

### Post by Hubster on 2007-12-26
.. and when i try to select Ubuntu to run I get the message:

Filesystem type unkown, partition 0x7
/boot/vmlinuz-2.6.22.14-generic root=UUID********** ro quiet splash

---

