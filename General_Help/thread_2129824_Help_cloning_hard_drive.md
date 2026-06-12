---
title: "Help cloning hard drive"
date: 2013-03-27
forum: General Help
---

### Post by 1stnoob on 2013-03-27
I posted in another forum, but got no response.  I will repost here, hope someone can help:

[COLOR=#333333][FONT=Lucida Grande]1. 2013-03-22 09:31:01 PDT[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I probably won't get an answer in time, but here goes.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I'm running Ubuntu, and created a CD from an iso. I wanted to clone a 64Gb SSD to a 256Gb SSD. I didn't get how disc image worked, so I selected copy drive or partition to drive or partition. Magically, it worked. Unfortunately, the contents of the cloned drive is made up of a 64Gb partition, and a 192Gb partition. I tried using Ubuntu disk utility to get rid of the partition, but of course all the data went with it. This can't be that difficult, how do I clone my OS and data onto one partition in the new drive?[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]

robertdaleweir [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]2013-03-22 09:50:08 PDT[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Hi glo48[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Download the Gparted iso (also available at Source Forge) and burn it to a CD. Open and resize the first partition to the full 256 gigs. Works for me... Cheers...[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]glo48 [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]2013-03-22 14:24:53 PDT[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I tried that using PartedMagic OS. Didn't work, I simply could not get it to resize. I went back to Ubuntu on my original 64Gb drive, deleted all the partitions, made them one partition, then formatted the drive, and now I'll try again. This can't be that hard...[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]glo48 [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]2013-03-22 21:52:51 PDT[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Ok, I finally did get it to clone to the whole drive, without any partitions. Which is just as well, since I could delete a partition in Gparted, but not convert it to one partition. If I remember right, I formatted the drive, mounted it, then selected option three in Clonezilla (which is incorporated into PartedMagic OS). However, then it would not boot, I just got a blinking cursor after the Bios screen. I searched around in Gparted and found something called Restore Grub bootloader. Then my 256Gb drive was able to load. Unfortunately, some things were missing, like everything in Dash Home; all my applications. All the data seemed to be there, though. Does anyone know what's going on? When I cloned the working drive to the new, larger drive, why didn't the bootloader clone as well? There's obviously something else going on, but I came from the Windoze world, so I can't figure out what it is, or how to fix it. Hope someone can help...[/FONT][/COLOR]


[COLOR=#333333][FONT=Lucida Grande]So that's still where I'm at. I just did a sector-by-sector clone - which takes hours, btw - and have one partition in my 256Gb (which ended up as only 239Gb, go figure), which is what I wanted. But I'm still getting the message that Clonezilla could not install Grub, which means that I will still get a blinking cursor, and if I use Grub doctor in PartedMagic OS, my Dash will still be gone, although I actually haven't tried it yet. Does anyone know what is happening, and more importantly, how to fix it?  It occurred to me that I could just upgrade to the latest Ubuntu version, but I would still like to know how to fix this.[/FONT][/COLOR]

---

### Post by Dragonbite on 2013-03-27
With Gparted, you would want to delete the partition you don't want, then move/resize the partition you want to fill the space.  You can also set the "flag" to the partition to boot.

I've used Clonezilla to copy partition-to-partition directly (not partition-to-image, though that may work as well) and usually it works for me.  I haven't had a problem booting up the new device with partition-to-partition (or is it bit-to-bit), which I assume is because it also grabs the MBR?

---

### Post by oldfred on 2013-03-27
Are you keeping old SSD installed in system? 
If so you will have issues of duplicate UUIDs and have to change one or the other, reinstall grub and edit fstab with new UUIDs.

I generally prefer clean installs, reinstall software from exported list, and just copy /home over to have your data and user configuration. 

From liveCD post this to see if you have duplicate UUIDs? (use code tags - # in advanced editor to preserve format.)
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by 1stnoob on 2013-03-27
> **oldfred said:**
> Are you keeping old SSD installed in system? 
If so you will have issues of duplicate UUIDs and have to change one or the other, reinstall grub and edit fstab with new UUIDs.

I generally prefer clean installs, reinstall software from exported list, and just copy /home over to have your data and user configuration. 

From liveCD post this to see if you have duplicate UUIDs? (use code tags - # in advanced editor to preserve format.)
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list

Even I'm not that dumb.  No, I was removing the cloned drive from my 2 hard drive bay laptop, installing the new drive in the proper bay, and then rebooting.  I just can't understand why Dash was empty, though all the data seemed to be there.  At this point I would pay someone to help me with it, but not everyone knows Linux.

---

### Post by oldfred on 2013-03-27
Run this to see details, You can just install into any liveCD/DVD/Flash Linux install you have. You should have a current version of Ubuntu anyway for repairs, if you do not.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by 1stnoob on 2013-04-25
Thank you all for your help, I finally got my drive cloned, using Clonezilla.  I'm sorry, I can't tell you exactly what I did differently the last time I tried, but I did try quite a few combinations before it worked. Of course, I should have been writing everything down. I even used the gparted program to expand my data partition to one partition.  When everything seemed to be ok on the new SSD drive I updated to Ubunti 12.04, from 11.X.

---

