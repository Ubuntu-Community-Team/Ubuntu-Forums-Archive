---
title: "After Ubuntu 14.04 upgrade, Gnome3 keyboard shortcuts not working"
date: 2014-04-20
forum: General Help
---

### Post by ephemerian on 2014-04-20
I've just upgraded from 13.10 to 14.04. Quite a few problems along the way, but I've managed to get everything working again except that my keyboard shortcuts in Gnome are not working. For example, I have ctl-alt-/ bound to the terminal launcher. Nothing now happens when I use that shortcut. I've gone into Settings > Keyboard > Shortcuts, and re-assigned the shortcut. Still not working. I've tried different key combinations, also not working, and tried creating a custom shortcut in case the launch terminal command is borked somehow. Standard keyboard actions like alt-tab, etc, are working fine, it's just my custom settings that are not working.

Any suggestions gratefully received.

Thanks,
Ian

---

### Post by antonio_molinaro on 2014-04-21
I have the same problem plus the keyboard configuration is lost after the login: as short time remedy I'm using 

$ [FONT=courier new]**sudo dpkg-reconfigure keyboard-configuration**[/FONT]

 but as soon I reboot the system and I do the log in, the configuration  is lost again. This may be a bug, but to be honest I'm not that  confident with system level stuff, so for now I'm waiting for some help  before fileing it as such. I tried to remove the other languages from  the ***Text Entry Settings***, but it did not work. TIA

antonio

---

### Post by nutsyben on 2014-05-07
> **antonio_molinaro said:**
> I have the same problem plus the keyboard configuration is lost after the login: as short time remedy I'm using 

$ [FONT=courier new]**sudo dpkg-reconfigure keyboard-configuration**[/FONT]


antonio

Thank you for the tip, I have the same problem. 
However your command is only to reconfigure the keyboard and in my case it does not fix the keyboard shorcut issue. 

If any has a solution ....

---

### Post by warsev on 2014-05-10
Just in case anyone is counting, I also have the same problem.

---

### Post by Matt12334 on 2014-05-13
I'm having the same issue. The odd thing is that it works in a guest session, but not in my main user account. Can anybody confirm whether their guest account has working shortcuts?

---

### Post by tomtom12 on 2014-05-15
> **Matt12334 said:**
> Can anybody confirm whether their guest account has working shortcuts?
Other account works for me. Only in my own account I can not use Keyboard shortcuts. I could before but not since a few days. weird.

---

### Post by tomtom12 on 2014-05-15
> **antonio_molinaro said:**
>  ...as short time remedy I'm using $ [FONT=courier new]**sudo dpkg-reconfigure keyboard-configuration**[/FONT]o
Does not work for me.

---

### Post by neumann-g on 2014-05-26
I have the same problem.
Deleting the ~/.gconf file and logging out and back in fixes it for me until the next reboot, after which I have to do it again.

---

