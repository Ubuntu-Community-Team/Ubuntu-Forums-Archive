---
title: "Grub/kernel update problem"
date: 2006-08-04
forum: General Help
---

### Post by spockz on 2006-08-04
Tommorrow I updated my kernel-image (Just an apt-get update), the last few times exactly the same problem occured. 

After updating the kernel I reboot, but grub doesn't boot the kernel. 

Grub starts (hidden), but when the timeout is over the system restarts. 


I know what causes this problem, update-grub adds a 'savedefault' command to the boot option. 

To be able to boot, I need to remove the savedefault command trough the grub console. 

After that I remove it in menu.lst

So well, it is temporarily fixed, but I hate doing this whole procedure over and over again ;) And this isn't really nice to people new to linux/ubuntu. 

I can't find anything about this in the bugtracker, so I wanted to ask if there are people with the same problem, or do I just have useless hardware (maybe the motherboard or something?)

If others experience this too I can be sure that it's real bug.

---

### Post by mlind on 2006-08-04
What do you have as **# default** on /boot/grub/menu.lst ?
If it's *saved*, change it to 0

---

### Post by spockz on 2006-08-04
default is already set to 0

---

### Post by mlind on 2006-08-04
I though that savedefault entries are effective only if you use *saved* as **# default** on menu.lst. 
Press ESC before Ubuntu boots to see the grub menu and check what actually happens.

---

### Post by spockz on 2006-08-04
> **mlind said:**
> I though that savedefault entries are effective only if you use *saved* as **# default** on menu.lst. 
Press ESC before Ubuntu boots to see the grub menu and check what actually happens.
If I open the menu and press enter without removing the savedefault option trough the console, the system restarts booting. 

So you see the memory check again etc, until it comes to grub again.

---

### Post by TFX360 on 2006-08-04
I'm having a similar problem. After an ```
 sudo apt-update; sudo apt-upgrade; sudo apt-get dist-upgrade 
``` I get error 22 in grub. When I remove savedefault. Everything works just fine. The setting seems correct according to me. Very wierd. Default = 0


Kind regards,


TFX

---

### Post by TFX360 on 2006-08-04
I'm having a similar problem. After an ```
 sudo apt-update; sudo apt-upgrade; sudo apt-get dist-upgrade 
``` I get error 22 in grub. When I remove savedefault. Everything works just fine. The setting seems correct according to me. Very wierd. Default = 0


Kind regards,


TFX

---

### Post by mlind on 2006-08-04
Either of you using a RAID array?
You should probably report this bug to [launchpad]("https://launchpad.net/distros/ubuntu") too.

---

### Post by spockz on 2006-08-04
> **mlind said:**
> Either of you using a RAID array?
You should probably report this bug to [launchpad]("https://launchpad.net/distros/ubuntu") too.
I'm not using a RAID array. It's a somewhat older computer with just a plain IDE harddisk. 

I reported the bug. I just wanted to know if others experienced this too (I though that maybe the old harware caused grub to do something strange with the savedefault option) 

And well, it seems at least one other user could suffer from the same problem. 

Bug report can be found here: [https://launchpad.net/distros/ubuntu/+source/grub/+bug/55190]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/55190")

---

