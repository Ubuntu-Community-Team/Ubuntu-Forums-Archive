---
title: "[SOLVED] Naughty forgetful GRUB/error 17"
date: 2008-03-25
forum: General Help
---

### Post by Everwanderer on 2008-03-25
Hi,

I've recently partitioned my HD using Acronis. My laptop usually dual-boots Vista/Ubuntu 7.10. Before partion, I had no issues with the GRUB. But I split Vista chunks of HD in different extensions and also extended the space available in the Ubuntu partition. Now I can only boot in Vista. When I select Ubuntu, I get the "error 17, cannot mount selected partition   press any key to continue", which sends me back to the GRUB menu. 

I've looked at the different posts and tried restoring said GRUB as posted ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)). All seems to work, I get yesses for finding the stage parts, but when I reboot and go back to GRUB, I get the same error again. I'm also very ashamed to say I just can't seem to find the menu.lst file in order to modify it according to other posts (very beginner with linux.. I might be lookind in the wrong places). 

Anyone can help me out?

---

### Post by Everwanderer on 2008-03-25
UPDATE

I tried using Supergrub.. the fix boot of GNU/Linux (GRUB) option from this page :[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

All seem to be ok, I rebooted (with spergrub CD in CD drive, then selected Grub=> MRB & Linux!(1) Auto, which sent me to me boot menu, I chose to boot Ubuntu and see if it worked. I got this msg :

root (hd0,5)
filesystem type unknown, partition type 0xdd
kernel /boot/vmlinuz-2.6.22-44-generic root=UUID=283ae073-b7fb-4770-9b0b-2080b
61cd3f1 ro quiet splash locale=en_CA

Error 17 Cannot mount selected partition
Press any jey to continue

Now, when I use the find command, to see where linux'd be, I get (hd0,6).  Hope this helps...

---

### Post by teryowen on 2008-03-25
Alright, basically what i think has happened is that you altered your partition table and this changed the location of the partition so now when grub says boot ubuntu at place X place X is not there, so we need to specify the place.

Heres what to do, boot up when at the grub part
hight light the Ubuntu entry
press 'e' to edit it
press 'e' over the root (hdx,x) part
and where it says (hdx,x) type (hd0,6)
and press enter and then 'b' to boot up.

if all goes well in other words you boot up successfully into ubuntu edit the menu.lst file permanently by doing this in terminal:

gksudo gedit /boot/grub/menu.lst

where ever you see stuff for ubuntu entries make sure that the hdx,x part says hd0,6

hopefully this works if it doesnt let me know we'll analyze further.

---

### Post by Everwanderer on 2008-03-25
You, good Sir, are a king amongst Ubuntuers.

Made the changes as described, all were set to hd0,5.. now hd0,6. I saved menu.lst and rebooted. It works! *happy dances*

Thank you.

---

### Post by teryowen on 2008-03-25
Good stuff, im glad it worked. Mark the thread as solved if you dont mind, just so others know.

Cheers.

---

