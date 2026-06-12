---
title: "Getting Grub to boot to USB"
date: 2008-03-30
forum: General Help
---

### Post by Chessmaster on 2008-03-30
Hi.

My main OS is Ubuntu, but I have also recently downloaded Puppy Linux to play around with and it is a lot of fun. I am running it Puppy Linux off a live CD. I am going to install it onto a USB stick. 

My question is this: how do I add the USB stick to the GRUB menu so at start up I can choose to boot off the USB stick should I want to?  (at the moment I can choose either Unbuntu or Windows as I am dual booting). 

I take it I have to add it to the grub menu which will involve: gksudo gedit  /boot/grub/menu.lst

But what do I add to this? 

I have some idea what to do but I thought that I should check with the forum before I mess around with the Grub. 

PS: I do not want to make Puppy Linux my main OS, only add a USB option to the grub so in future I can run other Distros from my USB should I want to. Which raises another question. If I add USB to my Grub, can I then run any OS from that USB stick? If so, that would be a nice way to upload different distros.  

Cheers

---

### Post by keeler1 on 2008-03-30
I am not quite sure, but you will probably need to reinstall grub (not necessarily a reinstall but get a new device.map and everything so that the new drive is recognized).  Then basically copy one of the ubuntu entries, rename it, change the root to be the usb drive / partition, and find the correct files and point the kernel and initrd variables to it  The only problem with this is that I am not quite certain what will happen if the drive isnt in.

One way which, I would use to solve this, is to have the bios of your laptop, boot the USB stick directly.  Change the boot priority so that it boots USB before Hard Disk.  That way whenever you plug in the usb stick it boots Puppy Linux.  If you need to access something on the drive simply insert it after Ubuntu starts to boot.

---

### Post by keeler1 on 2008-03-30
I reread the second part of your post and came up with another solution.

When you boot Windows from within GRUB you simply pass off control of the bootloader to another bootloader.  On my computers they are on separate drives.  My windows configuration looks like this

XP is installed on hd1, the bootloader is on hd0

```
title Windows XP
map (hd0) (hd1)           
map (hd1) (hd0)
root (hd1,0)
makeactive
chainloader + 1
```

I do not know why you map hd0 to hd1 then hd1 to hd0 and still have the root be hd1,0 but it works.

So essentially what your configuration should look like would be

```
title <your title>
map (hd0) (<USB>)
map (<USB>) (hd0)
root (<USB>, 0)
makeactive
chainloader + 1
```

replace USB with the drives number hd1, hd2, etc.. give it a title and it should be good to go.  For this you also have to install grub on the USB stick.  However, because you dont need to know the location of any specific file it doesnt matter if you install a new OS or not.

For this all to work however you will need to rerun something (I dont know the command) to get a new device map, so that grub knows about the drive and has assigned it a number.  Until you do that this way is out of the question.

---

