---
title: "lost data after reboot"
date: 2007-06-02
forum: General Help
---

### Post by art vandelay on 2007-06-02
Hi, I have a feisty installation on a desktop pc. I had to reboot the computer manually several times because the mouse would stop working (on XP it works fine), Every time I did this I saw that some problems were fixed by the system during the booting process, and after that it would restart itself one more time before coming up normally. But the last time I did this a lot of information was lost: the thunderbird settings and mails, the firefox favorites and the pidgin account. So I wanna know if there's some way to prevent this from happening again in the future.

Thanks in advance.

---

### Post by Rajiv_Nair on 2007-06-02
is it JUST the mouse that stops working or does the system hang up. Try pressing numlock  and check whether the numlock light turns on/off.

---

### Post by art vandelay on 2007-06-02
It is just the mouse, I was able to close all the programs before rebooting, but I didn´t know how to restart from the keyboard, so that's why I rebooted with the button on the cpu.

---

### Post by louieb on 2007-06-02
Ctrl+Alt+Backspace should kill x and give you the command line. then ```
sudo reboot 
```should get you started again. 
 
I've had trouble with Feisty freezing up Finally said screw it and went back to Dapper.

---

### Post by art vandelay on 2007-06-02
So it's not a very good idea to reboot manually. So if one day let's say there's a power outage, it is very posible for important data to be lost again...isn't there any kind of fix for this? just backup?

---

### Post by art vandelay on 2007-07-28
I found a simple solution to the root of this problem(the mouse would stop working), and it is to unplug and plug the mouse again. It is a temporary fix, but at least now I don't have to reboot each time this happens :)

---

