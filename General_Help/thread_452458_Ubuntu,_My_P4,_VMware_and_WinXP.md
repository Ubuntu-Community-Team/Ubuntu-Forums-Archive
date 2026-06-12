---
title: "Ubuntu, My P4, VMware and WinXP"
date: 2007-05-23
forum: General Help
---

### Post by lhuser on 2007-05-23
This one's a little complicated.

I have Cedega that I can install for Wow. 

Now, last time I did it with my P4, Radeon 9600Pro, 1GB RAM, AW200, it locked up in Cedega. It ran 6.06, so I don't know if it will be fixed in this one.

Now, let's assume my P4 locks up in Wow in 7.04.

I will use VMware and run XP (Probably a lite version) and I will run my game from there.

Now, here's two questions:

Will I be able to play with decent settings? (Maxed out, I run 9-15FPS. I don't find it annoying)
Will my system lock up? Since Cedega is a problem, I don't think XP would in VMware, but I'm wondering if I will be able to run it properly.


If you're wondering how it locks up in Cedega, here's how:

I run the game. It shows 106 FPS. That is WAY much faster than Windows, which locks at 60. As soon as I move the mouse, or scroll down a bit for the EULA, it will lock up. The sound will freese, nothing will move. The only way to get out of this, is by pressing Reset.

It had no problems without my GPU drivers, but ran horibly slow. I think it had to do with the drivers I used.

---

### Post by saravanan_india on 2007-05-23
I am using ubuntu 7.0.4 as my Primary OS, and I am using VMWare to run windows xp  (for office applications) I experience two problems with ubuntu 
1. Wireless is not that good in UBuntu, and even the range of wireless sensitiveness is also less
2. My windows xp from vmware doesn't picks up either the wired network or the wireless network.
    This seems to be annoying......  There should be a some way around it to make work

Could anyone let me know about it

I need a detailed explanation on this issue

---

### Post by lhuser on 2007-05-23
For the Wireless problem, you should make sure that you hve installed the restricted drivers.

For the Windows XP problem, look in device manager. It looks like you don't have the drivers installed.

---

### Post by pointone on 2007-05-23
The virtual machine will have access to less system memory and other resources, so your games will run slower in that environment. How slow? Hard to tell--only way to find out is to try it, really.

---

### Post by lhuser on 2007-05-23
Well, I'm supposed to have 256MB RAM more. I might put VMware to use 768 and Ubuntu will have 512 remaining. I might add another 256MB stick.

---

### Post by Tuxbee on 2007-05-23
accelerated grachics support is not stable in vmware player, I read on install
so I guess it's not the way to go

---

