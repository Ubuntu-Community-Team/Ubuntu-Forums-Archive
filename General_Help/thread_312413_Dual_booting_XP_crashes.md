---
title: "Dual booting: XP crashes"
date: 2006-12-04
forum: General Help
---

### Post by tradet on 2006-12-04
I figured that I would tr ubuntu for a change from from XP. And now after 1 day of use I've encountered BIG problems

Since I'm dual booting with win XP I wan't to access it too sometimes but when I get to the boot menu I can choose between 4 types of ubuntu and 2 win XP.

I would likw to cut these down to 2-3 choises.

But my main problem is that when I choose the win XP (one of them is "empty", does not contain a OS :confused: ) it starts over again and reaches the boot menu again.

Plz someone help!?!?

I'm in a real hurry now but I'll come back with more specs later.

Using Ubuntu Dapper 6.06 LTS

Booting them on the same hdd

Partition 1) Win XP
          2) Ubuntu swap
          3) Ubuntu root / ext3

And i found some wierd stuff on my hdd, where all the windows files are "WINDOWS", "DOCUMENTS AND SETTINGS" and so on
I found files named "boot.ini" and other wierd things

Now I'm a real noob so please have patiance and help me! ](*,)

---

### Post by scrupul0us on 2006-12-04
> **tradet said:**
> I figured that I would tr ubuntu for a change from from XP. And now after 1 day of use I've encountered BIG problems

Since I'm dual booting with win XP I wan't to access it too sometimes but when I get to the boot menu I can choose between 4 types of ubuntu and 2 win XP.

I would likw to cut these down to 2-3 choises.

But my main problem is that when I choose the win XP (one of them is "empty", does not contain a OS :confused: ) it starts over again and reaches the boot menu again.

Plz someone help!?!?

I'm in a real hurry now but I'll come back with more specs later.

Using Ubuntu Dapper 6.06 LTS

Booting them on the same hdd

Partition 1) Win XP
          2) Ubuntu swap
          3) Ubuntu root / ext3

And i found some wierd stuff on my hdd, where all the windows files are "WINDOWS", "DOCUMENTS AND SETTINGS" and so on
I found files named "boot.ini" and other wierd things

Now I'm a real noob so please have patiance and help me! ](*,)

well the grub menu can be edited: /boot/grub/menu.lst
and boot.ini is the boot/partition/os controller for windows only

either way make backups of both files b4 fudging with them

---

### Post by tradet on 2006-12-04
And how do i backup them?
If something goes wrong how do i reset them?

And what should i write??

Thanks in advance

---

### Post by tradet on 2006-12-05
now I've tried playing around with menu.lst using this guide: [http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot](http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot)

But XP still deosn't reboot.

GRUB finds the OS alright but it crashes and reaches the windows menu with "start as normal" and with "safety mode"

After a short period of hope it crashes and returns to GRUB...
Even with the "safety mode"

My bootup code for win XP looks like this now;

titel         Win XP
root          (hd0,0)
savedefault
makeactive
chainloader   +1

And I've tested with:

map   (hd0)(hd1)
map   (hd1)(hd0)

Ideas please? :confused:

AND!!! I couldn't boot with the simple tools with Super Grub!!!
It boots win XP but...!!
I crashes again..

Please help!! I'm desperate!!

---

### Post by bulldog on 2006-12-05
As I read this,it's not a GRUB thing,your windows is corrupted.
You can try to install windows again,which will overwrite your GRUB so you can't boot Ubuntu anymore,but that's a minor thing to solve.

Grub only points to the partition where your windows lives,than windows will take it over.
It crashes before you get to the desktop,but you see windows booting I suppose.

So it has nothing to do with GRUB,but all with windows I'm afraid.

If you have valuable data on your XP partition you can copy it with your ubuntu install,if done,reinstall windows.

---

