---
title: "New Configuration of USB Flash Drives"
date: 2013-08-12
forum: General Help
---

### Post by royph on 2013-08-12
Since I live in the sticks in the Philippines I am most likely behind the times but I just bought a new 8Gb Sandisk USB flash drive and discovered that it appears as a hard drive and not as a removeable device. After much searching I found an announcement from Sandisk stating that to comply with Microsoft (I hate that word) requirements all new Sandisk flash drives are configured to appear as Hard Drives on your computer. This was a surprise to me and to the store I bought it from.

Ignoring my personal feelings about this forced change I am wondering how everyone is dealing with the problem of making these flash drives bootable? Unetbootin will not install an iso on my flash drive and does not recognize it as a hard drive either. If all flash drive manufactuerers start using this configuration are we stuck with burning all iso's to Cd's or DVD's?

Any solutions or thoughts on this would be appreciated.

Roy

---

### Post by Gossar on 2013-08-13
> **royph said:**
> Ignoring my personal feelings about this forced change I am wondering how everyone is dealing with the problem of making these flash drives bootable?
…are we stuck with burning all iso's to Cd's or DVD's?
That's what I did: burned the liveCD, booted from that, and installed directly to my 8 GiB SanDisk flash drive. But then I needed the burned copy anyway.
> Any solutions or thoughts on this would be appreciated.
The directions from [help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot") may work for you.  Especially the part about mounting the iso via loopback.
```
sudo mkdir /mnt/iso # Optional - the ISO file can be mounted on an existing mount point if desired.
sudo mount -o loop /<path>/<filename>.iso /mnt/iso
```copy files over to flash drive and then```
sudo umount /mnt/iso # When finished inspecting the contents.
``` and use gparted to flag the flash drive as bootable?

---

### Post by royph on 2013-08-13
That may prove to be an interesting workaround and I will have to play with it as soon as I have time.

I guess what really makes me mad is that Microsoft has apparently forced this change to configuration that makes it very difficult to boot from any new flash drives for example to install linux from a USB flash drive which in my opinion is so much better than usung CD's or DVD's.

I read in a Sandisk Forum where someone questioned this and the reply from Sandisk was basically "Tough, tell the software makers to change their programs to live with this change". They at least could provide a way to flip the drive so it would appear as Removable. Lexar used to have a program to flip their flash drives to make them appear as hard drives if you wanted to do so, so I'm sure it would be possible to flip them the other way around.

So be I guess. Microsoft rules the world, except no one wants their new Fisher-Price OS or their Surface tablets.

Thanks for the input,
Roy

---

### Post by mastablasta on 2013-08-14
well that's strange. how do you safely remove it in MS then?

also i have a nice small USB key i simply can not boot from. upon asking their support how come i can not boot from the usb they told me that their devices are not made to be boot from. i think company was SP or something like that.

---

### Post by carl4926 on 2013-08-14
Why does windows have a USB writer then and Windows 7 and 8 can be installed from a bootable USB

---

### Post by Gilad_Pellaeon on 2013-08-14
I hope this doesn't become the standard for all USB flash drive makers in the future besides Sandisk. I have bought several 16gb USB flash drives from The Source  and they have always worked great in Windows and Lubuntu and seem to be made by PNY and rebranded as Nexxtech. You could also resort to a USB flash card reader if the PC doesn't have a card reader and use SD and MicroSD cards to make bootable drives from. In fact I installed Lubuntu off a 2gb MicroSD card with a USB Flash card reader with no problems.

---

### Post by Slug71 on 2013-08-14
> **carl4926 said:**
> Why does windows have a USB writer then and Windows 7 and 8 can be installed from a bootable USB

This is what I'm thinking.

I see no reason why that workaround Gossar mentioned, shouldn't work though.
This kinda pisses me off though, as I liked Sandisk. They shouldn't force stuff on people because of one company, that's losing ground btw, and then have an attitude like that. Guess I may be buying Flash Drives from someone else from now one.

And I happen to be looking...

---

### Post by carl4926 on 2013-08-14
> **Slug71 said:**
>  I liked Sandisk. 
And I happen to be looking...
I have no trouble with them.
I do delete the garbage they put on them for windows users

---

### Post by royph on 2013-08-15
Okay, it's not as bad as I thought it was and I have managed to get the flash drive to boot even though it shows as a hard drive. In case anyone is interested heres how I did it and it worked at least to create a bootable Mint 13 installation on the drive.

!. Format the flsh drive as Ext4

2. Mount the Drive

3. Use Unetbootin to copy iso to USB Drive: /1dev/sdc1 (At least in my case)

4. Reboot and select Sandisk Cruizer as the 1st boot drive

It's almost the same as the old way and the biggest difference I can see is that the flash drive has to be formatted as Ext4 and Mounted before you run Unetbootin. On my computer at least the bios does not show the flash drive under Hard Drives but it does show up as a boot device under Boot Priority. I selected that as the 1st boot device and it worked.

Now Microsoft is happy, San disk is happy and I'm happy except I still hate Microsoft and hope they go broke with their Fisher-Price OS for kiddies.

Thanks to all,
Roy

---

### Post by Ultra Cronic on 2013-08-17
> **mastablasta said:**
> well that's strange. how do you safely remove it in MS then?

also i have a nice small USB key i simply can not boot from. upon asking their support how come i can not boot from the usb they told me that their devices are not made to be boot from. i think company was SP or something like that.

I guess there is a Home Biz opertunity here to buy T-Drives that are bootable from 3rd world countries and re-sell them here in the states. Figures Only in America. I blame the hardware companies for prostituting themselves with this Boviene Soverienity. However I am the type to search and try.

---

