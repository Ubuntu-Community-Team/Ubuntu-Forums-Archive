---
title: "Ubuntu 17.10 Frozen at boot"
date: 2018-04-12
forum: General Help
---

### Post by Hungry Man on 2018-04-12
I ran the 17.10 from 16.04 upgrade last night. Now, when the system boots, it hangs at the login screen. Mouse/keyboard input does nothing.

 
lenovo p71

[COLOR=#555555][FONT=Arial]Intel Core i7-7820HQ Processor (8MB Cache, up to 3.90GHz)
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]16GB DDR4 2400MHz SODIMM
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]NVIDIA Quadro P3000 6GB
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]1TB SSD PCIe TLC OPAL2
[/FONT][/COLOR]

---

### Post by Hungry Man on 2018-04-12
Title is wrong - 17.10 is what I installed.

---

### Post by Hungry Man on 2018-04-12
The System Time updated, so it isn't frozen. But no mouse/ keyboard input is taken. When booting upthe arrow keys certainly work - I can hit left/ right to change from bootlogo to whatever you call that list of startup tasks.

---

### Post by Hungry Man on 2018-04-12
In recovery mode...

OK I can boot in gfx safe mode, and get a TTY. Is there a way to just roll forward to 18.04?

---

### Post by Hungry Man on 2018-04-12
OK. I apt-get upgraded and the login page now works. But when I log in, the screen goes black and it hangs OR it kicks me back to the login page.

---

### Post by Hungry Man on 2018-04-12
In the TTY I see nouveau errors. Any way to switch back to proprietary from terminal?

edit: ok, boots in failsafe gfx mode

---

### Post by Hungry Man on 2018-04-12
Moving back to nouvaeu drivers lets me log in. Solved.

---

### Post by cruzer001 on 2018-04-12
Hello again :)

17.10 defaults to Wayland.  So first thing to do is switch back to xorg.  Sounds like you can get to the login screen so go there and click on the gear to switch to xorg.

Before switching drivers, be sure nvidia was removed.

```
sudo apt remove nvidia*
```

Nouveau will get you by for the moment.

Upgrading to 18.04 will probably just create more problems.  You already have a upgrade problem and may need a fresh install.

EDIT
Are you in panic mode?  Time to chill.

---

### Post by Hungry Man on 2018-04-12
Wasn't panicking. Just documenting as I worked through it. This issue is resolved.

Nouvaeu was actually at least one component of the problem, once I could boot into failsafe and reenable the binary drivers the last of the issues was resolved.

---

### Post by cruzer001 on 2018-04-12
Excellent

Guest this thread is solved then.

Later

---

### Post by oldos2er on 2018-04-12
Hungry Man, would you please mark the thread 'Solved' under Thread Tools at the top of the page? Thank you!

---

### Post by Hungry Man on 2018-04-12
Ah, I could have sworn I'd done that. Must not have saved it.

---

