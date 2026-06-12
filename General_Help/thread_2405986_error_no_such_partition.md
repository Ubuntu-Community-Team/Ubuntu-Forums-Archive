---
title: "error: no such partition"
date: 2018-11-14
forum: General Help
---

### Post by bhavick30 on 2018-11-14
Hi,

Am new here and have just signed up to the forum, sorry if this post is not in the right section. Basically what's happened is i have a Lenovo T61 laptop and it was running Windows 7. We decided recently that we wanted to sell the laptop so we decided to delete everything off it. When you try and boot up the laptop now i get the following message:
[B]
error no such partition
Entering rescue mode...
grub rescue>
[/B]
I have tried the following commands to try and fix the laptop. I first typed in:

[B]ls

(hd0) (hd0,msdos2) (hd0,msdos1)

[/B]Then i typed this:

set root=(hd0,msdos2)
set prefix=(hd0,msdos2)/boot/grub
insmod normal
error: unknown filesystem 

I tried this exact same line of code, i just swapped it from msdos 2 to msdos1 and i got the same unknown filesystem message.

I really don't know what else to do now so any help you guys can provide would be really helpful! Also I don't have the Windows 7 installation CD anymore.

Thanks

---

### Post by kc1di on 2018-11-14
Hello bhavick30  and Welcome to Ubuntu forums,

I'm not sure from your description what exactly you did.  was this a dual boot ubuntu /windows 7?  is ubuntu installed?  if it was a windows only machine it sounds like you deleted the boot info.  Try to give us little more information.

---

### Post by Impavidus on 2018-11-14
What was on the laptop and what do you want to be on the laptop? That grub rescue prompt is typical of computers that had some linux installed, after deleting the partition of the system in control of grub. I.e., it suggests you had Ubuntu installed and deleted the Ubuntu partition.

If you can't tell what you did exactly, you can try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Create the summary and show us the link, so that we can see what bootloaders, operating systems and partitions are present.

---

### Post by bhavick30 on 2018-11-14
Hi,

Sorry guys i haven't been very clear with what exactly happened to my laptop. Basically i have a Lenovo T61 Thinkpad laptop. After owning it for sometime i decided i wanted to sell it because i hardly use it. So i decided to erase everything on the laptop and now when i try and boot it up it comes up with an error, no such partition and it's in grub mode. 

I rang Microsoft to find out what operating system was on the laptop originally and they informed me that it was Windows Vista Business which they no longer support so am screwed if i want to re install Vista again. The bottom line of this situation is i want to install another version of Windows back on the laptop and get it to boot back up again as normal. Something like Windows 10 would be ideal. But am not sure how i would install it on the laptop being in the current state that its in?

Thanks

---

### Post by kc1di on 2018-11-14
if you can get hold of a window 7 or 8 or 10 disc it will make no difference what was on it before.  it will reformat the partition anyway.  You could also down ubuntu or any varient of linux and install it.  if you use ubuntu you can boot to the live usb/disk and show us the output of gparted which is included in the live disk and it will show us what you already have on the HD.  in any event a new install will format whatever partition is on there.  Good Luck. if it were me I'd just format the partition that is left on there and let whoever buys it choose what operating system they want to install, Just advertise it as sold with no OS.   

I would  use the gparted to create a partition and the format it to NTFS or Ext4 and that will wipe most of what was on there off. if you got a grub screen then Linux of some sort was installed on there at sometime because windows does not use grub.

---

### Post by Impavidus on 2018-11-15
Formatting the hard drive will remove all files, but the actual data will remain on disk, so if the new owner wants to spend a few days searching the hard drive, he might find something interesting. There are more secure methods to wipe a drive clean.

If I bought a computer from a random stranger, I wouldn't care whether an operating system was present or not. I'd wipe the hard drive anyway, just to be sure there's no malware.

---

