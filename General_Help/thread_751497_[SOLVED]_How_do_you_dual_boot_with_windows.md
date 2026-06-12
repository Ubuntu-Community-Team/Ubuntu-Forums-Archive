---
title: "[SOLVED] How do you dual boot with windows?"
date: 2008-04-10
forum: General Help
---

### Post by omglol741 on 2008-04-10
I installed Ubuntu first. Then I used Parted Magic to resize the partition and created a new one for Windows. I installed XP Pro fine, but it said it deactivated the other partition so it wouldn't interfere with windows. Now it will only boot to XP. How do I make it so I can choose between the two? 

I'm using an Ubuntu live CD right now btw. I couldn't connect to the internet in XP, but Ubuntu does it automatically when I open firefox lol (ugh Windows is annoying)

---

### Post by warp99 on 2008-04-10
You need to make the partition for Ubuntu the boot partition, not XP. You can use Partition Magic if you like to fix that, just make the Ubuntu partition the boot partition and turn off the boot parameter for XP.

You may have to re-install Grub if the master boot record was damaged by the XP install. This guide will help you sort things out:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by omglol741 on 2008-04-10
OK I'm following the link, but it's not working like it says it will.

How do I start grub as root?

edit; anyway, I did the find thing and it gave hd0,0. So I did setup hd0,0. It looks like it installed it. I'll reboot now and see if it worked.

---

### Post by seeker1458 on 2008-04-10
The windows partition has to be the last partition created...with nothing else after it.  I use rEFIt as a boot manager.  Nice little gui to choose what OS you want to boot to, also gives you a boot to shell option.

---

### Post by omglol741 on 2008-04-10
k well I used the partition editor to flag the ubuntu partition as boot. I tried this earlier though and it didn't work. Maybe it will work now that i did that grub thing.

But isn't hd0,0 and stuff like that for IDE drives? Mine is SATA. GParted says says ubuntu is /dev/sda1, windows is /dev/sda2, extended is /dev/sda3, and swap is /dev/sda5

---

### Post by omglol741 on 2008-04-10
Now it boots to grub, but only ubuntu, ubuntu (recovery), and memtest are available from the menu.

I'm adding an entry to the grub list like in that link. I have

> title 		Windows XP
rootnoverify 	(hd0,0)
makeactive
chainloader +1

I think the Ubuntu partition is (hd0,0). Would Windows be (hd0,1) or what?

---

### Post by omglol741 on 2008-04-10
uhoh. It worked fine with (hd0,1), and I booted into windows from the grub menu. But now I can't get back into Ubuntu. The grub menu doesn't show up anymore. Now I'm back where I started.:confused:

It looks like WIndows made itself the boot again. How do I stop that from changing when I choose windows? Is it the makeactive or chainloader +1 part that is doing that?

---

### Post by zvacet on 2008-04-10
If you have windows on sda2 then rootnoverify (h0,1).

---

### Post by omglol741 on 2008-04-10
OK I got rid of the makeactive part, and it works fine now. 

Thanks for the help

---

