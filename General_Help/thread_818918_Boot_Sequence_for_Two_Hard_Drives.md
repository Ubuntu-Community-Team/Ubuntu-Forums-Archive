---
title: "Boot Sequence for Two Hard Drives"
date: 2008-06-04
forum: General Help
---

### Post by uboodumdum on 2008-06-04
Hi All

I have two hard drives, disk 0 is XP and disk 1 is ubuntu and the grub program. I don't need to remove Ubuntu but is there anyway I can change the boot sequence? Rebooting takes me into Grub(I think) and I must scroll down to get into XP or it will time out and I'm in Ubuntu. Since I still mostly use XP, this is a bit annoying. To add to it, my new USB keyboard will not scroll down to make the XP selection, so to get into XP I have to be using the old PS/2 keyboard, weird methinks.

Could I fix this by changing the boot sequence from bios or not?

Any idea why the USB keyboard will not scroll down to make the selection of XP after a reboot?

regards all

---

### Post by drs305 on 2008-06-04
System > Admin > StartUp-Manager. You can select the default operating system on the Boot Options page.

If you don't have StartUp-Manager on your menu, install it with:
```
sudo aptitude install startupmanager
```

For more on grub options, including how to set windows as default:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by uboodumdum on 2008-06-04
Ok, thanks.

So I can't do it from windows bios by putting disk 0 ahead of disk 1?

---

### Post by drs305 on 2008-06-04
> **uboodumdum said:**
> Ok, thanks.

So I can't do it from windows bios by putting disk 0 ahead of disk 1?

It depends where the boot menu is loaded. I think windows needs it in the MBR and that would mean moving the boot menu, not just switching the grub menu. I don't remember much about windows so someone else will have to answer your question. But if you make windows the default via StartUp-Manager it should automatically take you to windows without you having to type anything.

---

### Post by rbmorse on 2008-06-04
You can do this is GRUB very easily.

Open a terminal window and then

gksudo gedit /boot/grub/menu.lst

Look for the line that reads 

## ## End Default Options ##

Now, from that line and with the first instance counted as zero, count the number of times you see the word "title" as the first word in a group of entries until you get to the group that defines your XP installation, i.e., if XP is the fourth group in the list the number you will have counted will be 3. Remember that number. 

Scroll back to the top of the menu.lst file and then look down around 14 lines until you find

default       0

Change the "0" to what ever number you counted above, i.e:

default     3

Save the file, close gedit.  In the terminal window run

sudo update-grub

When that's done close the terminal and the next time you boot the machine it should default to XP instead of Ubuntu.

---

