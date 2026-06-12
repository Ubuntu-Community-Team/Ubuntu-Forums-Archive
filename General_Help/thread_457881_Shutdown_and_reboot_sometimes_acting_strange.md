---
title: "Shutdown and reboot sometimes acting strange"
date: 2007-05-29
forum: General Help
---

### Post by aldhar on 2007-05-29
Hello,
I have the following issue:

When I try to shutdown my laptop (either using the icon or case button), the screen sometimes stays black but the machine doesn't power off. Also rebooting sometimes results in powering off instead of restarting.

I had this issue from the very beginning of using Ubuntu (Edgy Eft). None of the updates together with migrating to Feisty fixed this problem. Together with [[COLOR="Blue"]this problem[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2611310#post2611310") these are the only two remaining concerning my laptop. 

A solution suggesting adding -P switch to shutdown in /etc/acpi/powerbtn.sh didn't help.

Here are my current specs:
Asus A8H laptop
Feisty Fawn with 2.6.20-16 kernel

I don't know what else could be helpful... probably some logs. If you need any I will provide you with them.

Regards,
Adam

---

### Post by liberalist on 2007-05-29
I am new to Linux, but experienced similar problems on my laptop with Dapper Drake (6.06.1 LTS). My problems were resolved, however, when I updated to Feisty Fawn (7.04). 

A clean reinstall might help, but please wait for other (more experienced) users to respond on this thread. 

I would advise you **to back-up any important documents**, since your computer is acting strange. Furthermore, I don't know about the logs, they might be useful, so save them somewhere safe. 

Good luck.

---

### Post by aldhar on 2007-06-02
anybody?

---

### Post by jjacobs2 on 2007-06-02
You could try this:

edit /boot/grub/menu.lst
add
acpi=off noacpi 
to the end of the line that begins with the word kernel

---

### Post by aldhar on 2007-06-02
> **jjacobs2 said:**
> You could try this:

edit /boot/grub/menu.lst
add
acpi=off noacpi 
to the end of the line that begins with the word kernel

This disables the battery indicator, special keys on laptop, thermal sensors and pushing the power button causes the hard power-off which is not acceptable.

---

### Post by aldhar on 2007-06-05
bump

---

