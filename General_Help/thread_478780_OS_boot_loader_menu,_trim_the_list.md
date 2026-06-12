---
title: "OS boot loader menu, trim the list?"
date: 2007-06-19
forum: General Help
---

### Post by PendragonUK on 2007-06-19
I have had ubuntu installed for a while now, a long with WinXP. The list of options I get each time I boot has become a little unweildly. Is there a way to edit the Grub menu to trim it down to the latest ubuntu kernel and WinXP?

---

### Post by floke on 2007-06-19
sudo nano /boot/grub/menu.lst

put a # before any line you don't want to appear in the menu

IMPORTANT - back up the file first

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_DATE (where DATE = today's date eg 190607)
to restore if anything goes wrong - simply reverse the last command

---

### Post by kimusabi on 2007-06-19
Sure. Open the grub boot loader as sudo an edit out the exfess listings you don't want. But first make a back up by typing in the terminal ```
sudo cp -p /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then to edit the grub menu, open it using your favourite text editoras sudo, we'll use gedit in this example.
```
 sudo gksudo gedit /boot/grub/menu.lst
```

Scroll down to the end of the file and edit out the listings you don't want to appear when you boot up. Although make sure you keep the recovery of the current kernel. Always handy to have. 

Hope that helped.

Edit: Steve.K beat me to it.

---

### Post by aJayRoo on 2007-06-19
You need to edit your grub menu file, type the following command into a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
and then type in your password when prompted. Find the part of the file that looks like this:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1
```
and set howmany to 1 (as in the example above). This will limit grub to showing the newest kernel (with recovery option) and windows. Make sure you leave the '#' at the start of the line, this is very important. Doing this will ensure that the menu keeps this layout when you upgrade kernels. Hope that helps.

EDIT: I see two others have already beaten me to this! I forgot to mention the essential step of backing up the menu.lst file before editing so make sure you do that. Commenting out the entries you don't want will achieve the same result in the short term but the next time you upgrade kernels the grub menu will be reset to its original form, however the method I used will make sure the change is persistent even after kernel upgrade.

---

### Post by floke on 2007-06-19
I personally wouldn't do this since you'll be buggered it we get another borked kernel update that won't boot!

I like to keep 3 kernels - just to be extra safe ;)

---

### Post by aJayRoo on 2007-06-19
Good point, I guess setting howmany to 2 or 3 would be a safer option.

---

### Post by floke on 2007-06-19
8)

---

### Post by kimusabi on 2007-06-19
I prefer just keeping GRUB as it is. No need to mess with something that has the potential of causing me a mini headache if all goes wrong :)

---

### Post by PendragonUK on 2007-06-20
Thanks for the help guys...

---

### Post by Drakkor on 2007-10-09
Ok, I am hereby resurecting this post,lol 
Just upgrading to Gutsy, do I need all these entries ?

title		Ubuntu gutsy (development branch), kernel 2.6.22-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu gutsy (development branch), kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu gutsy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by Forlong on 2007-10-09
If you have tested thoroughly, if the new kernel works for you, it's safe to remove the old one via Synaptic.

The menu.lst will get updated automatically.

---

### Post by Drakkor on 2007-10-09
Thanks,Forlong much better now,lol :)
And your blog actually got CompizFusion up and running for me ! Thanks ! 

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=0b988614-be3a-48d4-84dc-25fe5a66e0a7 ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

