---
title: "OS loading Question"
date: 2006-10-20
forum: General Help
---

### Post by wheli on 2006-10-20
Hi Guys,

Quick question that i couldnt find the answer to:

I am going to be installing Ubuntu on a machine that doesnt have a CD rom drive....so im moving the harddrive over into another machine that does and using that cd rom drive to install the OS.

Heres the question:
When are the drivers loaded?  Are the drivers for my "cd-rom machine" going to be loaded onto the harddrive or when i swap the harddrive into my "non-cd-rom machine" and start up the operating system is that when the drivers are loaded up?

I dont want to go through all this hastle if my video card and stuff wont work when i swap the hard-drive.

thanks in advance for the help.....

---

### Post by streeto on 2006-10-20
Why not swap the CD-ROM drive instead?

---

### Post by wheli on 2006-10-20
The power supply in the other computer does not have an extra power plug to power another device......i guess theortically i could use two power supplys and leave the hard-drive in the computer that it is going to live in and just use an IDE cable to connect them....but i was curious about this issue either way.

---

### Post by Kateikyoushi on 2006-10-20
This isn't going to work out well, get a power cable splitter for 2 USD then can add the cdrom to the system. The drivers are in the kernel but ubuntu  will be configured to the other system which might result in massive config file editing for several devices.

---

### Post by wheli on 2006-10-20
ok cool man, thanks for the advice, i appreciate it

---

### Post by JamesB on 2006-10-20
> **wheli said:**
> Hi Guys,

Quick question that i couldnt find the answer to:

I am going to be installing Ubuntu on a machine that doesnt have a CD rom drive....so im moving the harddrive over into another machine that does and using that cd rom drive to install the OS.

Heres the question:
When are the drivers loaded?  Are the drivers for my "cd-rom machine" going to be loaded onto the harddrive or when i swap the harddrive into my "non-cd-rom machine" and start up the operating system is that when the drivers are loaded up?

I dont want to go through all this hastle if my video card and stuff wont work when i swap the hard-drive.

thanks in advance for the help.....

This can be done, install the server version, transfere the harddrive over and then apt-get install ubuntu-desktop ubuntu-standard. Re-boot. This should do it. On the re-boot the systen searches for and loads the relevant drivers. There are threads in the forums somewhere explaining in greater detail. Let us know how you get on.

---

### Post by wheli on 2006-10-25
hey guys,

i got it to work!

just had to use two power supplies and power the cd rom drive on the same IDE cable as my hard-drive and then connect it to the board of the computer that i wanted to install ubuntu on.

only thing that isnt working is the ethernet ports....but i should be able to figure that out.

thanks for the help.

---

### Post by wheli on 2006-10-25
actually....still having trouble getting the internet working..](*,) 

any ideas on how to troubleshoot?

Thanks!

---

