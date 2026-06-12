---
title: "Stuck on power off"
date: 2017-12-31
forum: General Help
---

### Post by viktor03 on 2017-12-31
Hi all,

I'm running 17.10 vanilla Ubuntu but changed DE to stock gnome.
Machine is a Y700 lenovo ideapad. i7 processor, 16 gb ram. Home folder and swap were encrypted at installation. 

When i power off i end up with a consule-like screen with one line of text (sometimes 2, the second almost identical). It's stuck like that for up to 10 min before it eventually powers off (unless i hold down the power button)

The before mentioned line:
[10758.519534] wlp8s0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-22)

If there's a second line it differs only in the number between [] and 1 before the ff's becomes 2.

Occasionally the problem doesn't occur and the computer powers off in under 10 seconds.

No idea what to do about it. 

Thanks for any suggestions

---

### Post by dragonfly41 on 2017-12-31
Google search ...
[https://askubuntu.com/questions/967441/17-1-wlp6s0-failed-to-remove-key-1-ffffffffffff-from-hardware-22](https://askubuntu.com/questions/967441/17-1-wlp6s0-failed-to-remove-key-1-ffffffffffff-from-hardware-22)

---

### Post by viktor03 on 2018-01-01
tried solution 2 and spend over an hour tinckering before i could boot up again
also, it didn't work

---

### Post by dragonfly41 on 2018-01-01
Don't blame the tools. You do not offer any information on the kernel you are using.
Other posts refer to 17.10 modifying Lenovo BIOS so I would research that topic.
Search "Lenovo BIOS".  e.g. [https://ubuntuforums.org/showthread.php?t=2381317&highlight=Lenovo+BIOS](https://ubuntuforums.org/showthread.php?t=2381317&highlight=Lenovo+BIOS)

Others have used boot-repair.

So no more guessing.   Post the pastebin link after running boot-repair.

---

### Post by viktor03 on 2018-01-01
you're right. i shouldn't blame the tools. and i appreciate the time you take to reply me.

the kernel i have now is:
viktor@ubuntubox:~$ uname -a
Linux ubuntubox 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


which is safe as per the thread you send me. i didn't have any problems with bios, so, as i'm not sure what bios-repair does, maybe better not to fix something that's not broken?

as i was in recovery mode i ran "fix broken packages" and that fixed another problem i was having which i posted in another thread, regarding dpkg not working. sory if i'm unclear, i don't remember exactly what i did.

anyway, i set /etc/default/grub back to what it was before. the "alt+F7" solution does work. and if i power off with a delay, 10 more min doesn't really matter.

one thing that's off about the BIOS (i think it's a design flaw rather then corruption), if i set a BIOS password it's still possible to enter boot menu and boot a live OS, which kinda defeats the purpose. i could set a power on password, but then i'd have to insert it every time. 
but maybe this question belongs in a different thread? or on a lenovo forum?

---

