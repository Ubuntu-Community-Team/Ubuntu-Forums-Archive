---
title: "Partitioning Mistake"
date: 2007-01-18
forum: General Help
---

### Post by Lubear on 2007-01-18
I've had ubuntu for about a week now and I decided that I didn't want it on my system anymore but I would install it onto my laptop. I thought that the easiest way to uninstall would be to delete the partitions and merge the left over unallocated spaces to my windows drives. So... this is what I did.

Before "Uninstall"
hda 1 - Windows XP
hda 2 - all the other stuff
-hda 5 - Important files for Windows XP
-hda 6 - Ubuntu
-hda 7 - Linux Swap

So I deleted hda 6 and hda 7, and merged it to hda 5. I thought this would uninstall Ubuntu. I'm pretty sure I didn't reformat hda 6 and hda 7 before I deleted it.

After "Uninstall"
hda 1 - Windows XP
hda 2 - all the other stuff
-hda 5 - Important files for Windows XP, and possibly Ubuntu and the Linux Swap

I didnt know this at first so I restarted my computer and realized that GRUB wasn't uninstalled. Not finding Ubuntu, GRUB failed to start. Since GRUB failed to start, I couldn't get to windows. So I tried to reinstall Ubuntu and got a lot of errors when I tried to make new partitions for the install. I'm pretty sure that GRUB is in hda 0... which I can't find using GParted.

So,
1. I can't get to Windows
2. I can't reinstall Linux
3. I'm pretty sure that everything is mixed up and is going to take forever to fix everything in hda 5.
4. I have a lot of important crap on hda 5.
5. I am using the LiveCD as a temporary OS.

Please help me out. I don't have any money to take my system to the computer shop anymore.

---

### Post by bodhi.zazen on 2007-01-18
For your boot problem:

In Windows XP, you can permanently uninstall GRUB as follows:

[list=number][*]Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console.
[*]Select your Windows XP installation from the list and enter the administrator password.
[*]At the input prompt, enter the command "FIXMBR" and confirm the query with "y".
[*]The MBR will be rewritten and GRUB will be uninstalled.
[*]Press "exit" to reboot the computer.[/list]


In Windows 2000, you can permanently uninstall GRUB as follows:

[list=number][*]Boot from the Windows 2000 CD and press the "R" key during the setup and the "K" key in the following menu in order to start the Recovery Console.
[*]Select your Windows 2000 installation from the list and enter the administrator password.
[*]At the input prompt, enter the command "FIXMBR" and confirm the query with "y".
[*]The MBR will be rewritten and GRUB will be uninstalled.
[*]Press "exit" to reboot the computer.[/list]

[color=blue]Thanks to bswilson[/color]


As far as getting a look at your data, in a terminal:```
sudo mount /dev/hda5 /mnt
gksudo nautilus
```

Browse to /mnt and see what you have :)

---

### Post by Lubear on 2007-01-18
thanks a lot. I got rid of GRUB, and all my files are fine. But somehow, there's about 10GB that disappeared from my computer. Besides from that, all is good. Thanks again.

---

