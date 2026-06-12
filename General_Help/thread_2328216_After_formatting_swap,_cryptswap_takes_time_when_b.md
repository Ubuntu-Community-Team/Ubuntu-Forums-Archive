---
title: "After formatting swap, cryptswap takes time when booting up"
date: 2016-06-18
forum: General Help
---

### Post by rez-dj on 2016-06-18
[COLOR=#111111][FONT=Ubuntu]My HDD partition looks like this: (please point out if my partition method is wrong)

[/FONT][/COLOR][IMG]https://dl.dropboxusercontent.com/u/52250958/Screenshot%20at%202016-06-05%2022%3A25%3A16.png[/IMG]

[COLOR=#111111][FONT=Ubuntu]sda6 was unallocated at first so I created it in Windows 7 then afterwards my Ubuntu MATE could not use sda5 (swap) anymore so I formatted the partition as swap in Gparted, then copied the *UUID* to /etc/fstab then removed the # to activate it.

But n[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]ow every time I boot in my Ubuntu MATE I get a very long boot up time to complete those 2 jobs at the bottom of the picture (1 min 30 sec to be precise) which looks like this:[/FONT]

[/COLOR][IMG]http://i.stack.imgur.com/vMwXa.jpg[/IMG]

[COLOR=#111111][FONT=Ubuntu](notice it says "A start job is running for cryptswap1.device and nother .device i cannot read)


[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]eventually when Ubuntu does boot, i find that the swap is active. I assume that the boot up process tries to fix this issue every time it boots up.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]so I tried booting in recovery mode to check and repair using fsck and I get this:

[IMG]http://i.stack.imgur.com/M7mXa.jpg[/IMG]

but it does not get fixed.

can anyone please help me fix this issue? thanks in advance...[/FONT][/COLOR]

---

