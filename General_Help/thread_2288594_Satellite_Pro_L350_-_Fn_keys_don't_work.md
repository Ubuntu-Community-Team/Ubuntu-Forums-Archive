---
title: "Satellite Pro L350 - Fn keys don't work"
date: 2015-07-28
forum: General Help
---

### Post by Ghune on 2015-07-28
I installed xubuntu on this pretty old laptop and everything is going well; I installed Xubuntu easily; everything works, I love it.

 There is just one little thing I wish I could do: controlling the brightness using Fn keys as they don't work. I don't care about all of them except the brightness control. Is there an easy way to do it?

---

### Post by Ghune on 2015-08-01
Nobody?

---

### Post by Vladlenin5000 on 2015-08-01
No, there isn't an easy way to fix. AFAIK, there are some parameters to be added to Grub and although those certainly don't qualify as easy, in the end, it isn't so hard and needs to be done only once (per OS installation).

I suggest you do a Google search with your model number + ubuntu + backlight (or variations around this theme, I'm sure you know what to do). In a nutshell, you'll find instructions on how to add the "acpi_backlighti=vendor" parameter to the GRUB_CMDLINE_LINUX_DEFAULT at /etc/default/grub, of course, followed by *sudo update-grub* to make changes effective and permanent.

---

### Post by kerry_s on 2015-08-01
if that don't work you can try & create keyboard shortcuts using those fn keys using the xbacklight program.

i think this is page i used a long time ago:
[http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script](http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script)

---

### Post by Ghune on 2015-08-01
Thanks, I will check this out. And it doesn't work, well, it won't be a big deal...

---

