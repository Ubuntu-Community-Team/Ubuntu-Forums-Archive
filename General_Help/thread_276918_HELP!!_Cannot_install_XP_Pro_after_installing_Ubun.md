---
title: "HELP!!: Cannot install XP Pro after installing Ubuntu!!!!!!!!!!"
date: 2006-10-13
forum: General Help
---

### Post by Thomas.sln.johnson on 2006-10-13
I just installed Ubuntu on my main internal SATA hard drive. 
I'm trying to install XP Pro on my USB Hard Drive or on the remaining space left on the partition in which Linux is installed in. 

After loading the XP boot disc and clicking install in a certain partition, it says that it cannot access the disk. It says that its not neccesarily an error but rather a software issue. It says that you need special software to install in that partition.. 

Any help?

---

### Post by Kateikyoushi on 2006-10-13
> **Thomas.sln.johnson said:**
> I'm trying to install XP Pro on my USB Hard Drive or on the remaining space left on the partition in which Linux is installed in.

You can not install windows on a linux partition.
You have to create a new partition resize the existing one if it takes up the whole disc.

---

### Post by orb9220 on 2006-10-13
And also when xp install it will overwrite the mbr so you will no longer be able to dual boot with ubuntu until you redo the grub setup.

Also xp wants to be the first partion of the first HD to run. There are ways around this.

In my dual boot system I installed XP first so ubuntu could see it and add it to the grub menu.

1st HD hda1==XP,hda2=/,hda3 /home,and then swap

This setup allows xp to have it it's way and ubuntu then can see xp during the install and modify grub menu to include it.

---

### Post by PriceChild on 2006-10-13
As far as i know you can't boot xp off of a usb drive either... if you get it installed.

---

