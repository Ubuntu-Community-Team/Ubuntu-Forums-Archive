---
title: "root privileges to edit menu.1st"
date: 2006-12-26
forum: General Help
---

### Post by McBlue on 2006-12-26
Would some kind and tolerant soul take pity on a Windows user and explain in detail how I can get access to the menu.1st file so I can edit it. (to add another boot entry for Vista on the 1st partition on the boot drive).

I’ve tried what I can find about “sudo passwd root” etc and I am obviously missing something. I think I can pretty much follow the instructions here [http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx](http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx) for the change I need to make to Menu.1st file, but I just can’t get that far.

Thanks all.

---

### Post by jincast90 on 2006-12-26
> **McBlue said:**
> Would some kind and tolerant soul take pity on a Windows user and explain in detail how I can get access to the menu.1st file so I can edit it. (to add another boot entry for Vista on the 1st partition on the boot drive).

I’ve tried what I can find about “sudo passwd root” etc and I am obviously missing something. I think I can pretty much follow the instructions here [http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx](http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx) for the change I need to make to Menu.1st file, but I just can’t get that far.

Thanks all.

You need to write this command:

sudo gedit /Path to the file.

I'm sorry, but I am not sure were menu.1st is located. Sudo is to get root rights and gedit is the text editor.

---

### Post by hexion on 2006-12-26
sudo gedit /boot/grub/menu.lst

or...

sudo pico /boot/grub/menu.lst

or any other file editor like vi, emacs, kate, (...)

---

### Post by McBlue on 2006-12-26
Thanks ever so jincast90. Once I figured out it was lst and not 1st, then your suggestion worked a treat. Multiboot now all configured with Grub in the MBR. 

Cheers Mate.
McBlue.

Edit:
Thanks Hexion. I might try and do something else with Ubuntu now I've found a helpful Linux forum.

---

### Post by McBlue on 2006-12-26
I’ve got a couple of other questions guys about Grub. (should I start a new thread in a different section maybe?)

I can indeed see Grub on the sectors in the first track after the MBR, but is it loading my Windows OSse from there, or does it pass control to another part of Grub on the ubuntu partition, which then loads the Windows PBR?

Also is there a way to autohide partitions? I have 3 Windows on primaries and I’d like to set Grub to hide the other two from which ever one is booted.

Cheers.

---

### Post by hexion on 2006-12-26
Grub lines are just links to the boot code of your windows partitions.

You can just comment or even delete the lines of the o.s. you don't want to load.

In example:

> title           Ubuntu
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=es_ES
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Windows 98
root            (hd0,1)
savedefault
makeactive
chainloader     +1


That will show 3 options during boot, but if you comment (or delete) the last option, it will show just 2:

> title           Ubuntu
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=es_ES
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

#title           Windows 98
 #root            (hd0,1)
 #savedefault
#makeactive
 #chainloader     +1


---

### Post by McBlue on 2006-12-26
Hi Hexion, I understand what you describe, what I was curious about is whether Grub runs entirely from the MBR or if a part of it is always on the Ubuntu partition. That is, does the MBR part of Grub simply pass control to another part of itself on the Linux partition, which then boots the Windows partition? The ‘chainloader’ line in menu.lst made me suspect this.

I’ve answered my own question by deleting the Ubuntu partition. On reboot Grub falls down and offers no boot menu – just error 22. This is a bit of a surprise for me as I did not realise that Grub operated in this way. Is it possible to have Grub entirely in the MBR? So that your bootmanager is not dependant on the integrity of a particular partition?

It’s not a crucial issue for me as I would not personally use Grub. I’m just running tests with Vista and its compatibility with MBR bootmanagers.

Thanks
McBlue.

---

### Post by hexion on 2006-12-26
I think it's not possible... grub needs to read menu.lst each time it boots to display options.

To read that file, your Ubuntu partition has to be there to be mounted.

It would be great to be able to load the entire grub in MBR (as an option), but in that case each time you update your list of o.s. (in example, each time you upgrade your kernel, you need to edit that list) you'd need to reinstall grub again.

I think that's the reason why it's configured that way. Anyway, that's what I think, I can be wrong ;)

---

### Post by rsambuca on 2006-12-26
Grub is separated into different "stages".  From what I understand, the space allocated on the MBR is not large enough to contain all of the information required for all of the bootloader options (and perhaps it would not be desireable to be changing the MBR with every kernel update?).  Thus the first stage is located in the MBR, which then tells the machine where to find stage 1.5 or 2 or whatever that next step is in the chain of command.

---

### Post by hexion on 2006-12-26
> **rsambuca said:**
> From what I understand, the space allocated on the MBR is not large enough to contain all of the information required for all of the bootloader options

The menu.lst file could be included, it's just text and we have 512 KB of space avaiable for MBR (and another 512 KB for the backup). That way, we could keep on booting into Windows if the partition of the system from which grub was installed is deleted.

In fact I don't know wheter that's possible or not with actual grub design :-k

---

### Post by fragos on 2006-12-26
Grub does change the MBR and uses a Linux partition to store the boot script, menu.lst.  Grub can be configured for any Linux or Windows for that matter to be the default boot.  Linux plays nice with Windows.  If you have a dual boot system and reinstall Windows the MBR will be changed to Windows only -- they don't play nice with others.  There is a process to restore grub without reinstallin Linux.

---

