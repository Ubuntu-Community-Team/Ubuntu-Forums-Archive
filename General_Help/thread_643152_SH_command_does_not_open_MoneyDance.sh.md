---
title: "SH command does not open MoneyDance.sh"
date: 2007-12-17
forum: General Help
---

### Post by WkenCouser on 2007-12-17
Hello,
I am a Windows user converting to Linux/Ubuntu and I love Linux.  I have used Quicken in the past and I have tried KmyMoney, GNOCASH and Grisbi. I want to try MoneyDance now but I can not install it. Here is the error.  

wken@wken-MoWest:~$ sh moneydance_linux_x86wj.sh
sh: Can't open moneydance_linux_x86wj.sh

Gutsy Gibson on a HP Pavilion laptop.

Thanks,  all help is welcome.
W.Ken Couser

---

### Post by Technoviking on 2007-12-17
It probably needs to be executable. Try this:
```
chmod +x  moneydance_linux_x86wj.sh
sh moneydance_linux_x86wj.sh
```

Mike

---

### Post by Lostincyberspace on 2007-12-17
You could also just type ./moneydance_linux_x86wj.sh . that should do the same think, but I think it flows a little better.

---

