---
title: "Wine + Gnome integration problem"
date: 2007-08-21
forum: General Help
---

### Post by Andrey Ponomarev on 2007-08-21
Hi,

I've installed Ubuntu Feisty on both my work laptop and home PC. Actually all works fine but with some differences:
[LIST=1]
[*]If I double click on exe file on my laptop, wine starts automatically. But it don't on PC.
[*]When I install a windows program, it's added to the application menu on my laptop, but it isn't on the PC.
[/LIST]

Do anybody know why it so?

---

### Post by Zylar on 2007-08-21
I've had the same problems before, and they usually seem to be fixed by a logoff/logon, or a restart.  Did you recently upgrade wine? 

Good luck,

---

### Post by Andrey Ponomarev on 2007-08-21
Thanks for reply

I found the source of my problem. There are some directories in my home were created by root. I changed the owner and know it works

---

