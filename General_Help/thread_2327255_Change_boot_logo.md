---
title: "Change boot logo"
date: 2016-06-09
forum: General Help
---

### Post by HoseongSon on 2016-06-09
Hi.

I tried to change my Lubuntu boot logo with plymouth And it had been changed.

But, the boot logo was displayed after be shown some console message on my monitor.

How to show ONLY boot logo without the message?

---

### Post by Zanden on 2016-06-09
What message? is it from the bios on boot?

---

### Post by HoseongSon on 2016-06-09
Nope.

Maybe it was dmesg (Messages on display when RPi boot)

Also, I use Lubuntu on ARM board. not PC.

---

### Post by ckotichas on 2016-06-14
If it's messages from grub (not the menu itself), try adding this to /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

---

### Post by ckotichas on 2016-06-21
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=2034500")HoseongSong, don't forget to mark this thread as "SOLVED" if your issue was resolved.

---

