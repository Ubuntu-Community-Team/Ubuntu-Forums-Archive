---
title: "hdd failed to mount on boot"
date: 2021-01-11
forum: General Help
---

### Post by humanoidcomplaints on 2021-01-11
The tin says it all.
where do I start? I can't find anything of use in the log files, or am I looking at the wrong ones?(/var/log/boot.log,dmesg,syslog,etc.)

I have made sure it ain't the fstab as I tried 'defaults' and 'rw' even went ham and added everything I thought would yield, but alas, 'tis was a failed venture!

I can manually mount it in rw after I get into the recovery root shell and proceed with normal boot, but this is a serious hastle and I have no idea on how to solve it.

So please, guide me in the right direction, I'd rather solve this without any help, but I just can't find a single lead!

Any hrlp is apreciated!
with regards, I'll be waiting.

---

### Post by CelticWarrior on 2021-01-11
A consequence of this [https://ubuntuforums.org/showthread.php?t=2456383](https://ubuntuforums.org/showthread.php?t=2456383) perhaps? But if so why did you start a new thread with even less information than the previous?

---

### Post by humanoidcomplaints on 2021-01-12
Dang, you right. I should've removed that one, I started this thread because I wanted some ideas on where to start looking rather than a straight solution, but looking at that thread imma try changing the fstab to uuid from /sda2/ although I can't remember what the value was and I don't have my confuser on hand.

Thanks for the help tho!

P.S. despite my best efforts I'm bad at asking for help so I avoid it at all cost

---

