---
title: "Ubuntu and grub error 17"
date: 2007-11-04
forum: General Help
---

### Post by cs_maan on 2007-11-04
Well my dad wanted Ubuntu on his laptop so I installed it for him and, he didn't like it all that much so I had to reinstall Windows, I used Gparted to change the partition file system to NTFS instead of ext3, and when I rebooted with the Vista CD I got the following message "Grub Loading....error 17 Grub 1.5" something like that, and we've tried nuking his hard drive, we've tried rebooting with the Live CD, we tried rebooting with the Vista CD, but no matter what I get that error, what should I do, this is an emergency because the laptop is used at the place of work and is quite important. Please help :), TIA.

---

### Post by johnn1949 on 2007-11-05
Hi,

If you installed ubuntu as a dual boot, you may just need to fix the master boot record to get vista back up. try this.

"Yes, use either your Vista or XP CD to remove grub.Boot off of the cd, Select R for repair, and then type fixmbr in the console, and you'll get a message saying a new MBR was successfully written, then type exit, and reboot."

If you used the whole disk to install ubuntuI think you will need to do a complete reinstallation of vista.

john

---

### Post by johnn1949 on 2007-11-05
When you are booting from cd are you changing your boot sequence to start from the cd?  If you are just turning on the computer you would get the grub error I think.  

when you turn on the computer a message will flash by with a " F12 to change boot order " or something like that. sometimes esc.  You need to start tapping that key when the computer starts and then you should get an option to boot from cd instead of hard drive.

Sorry if you knew all that, just a try,
john

---

