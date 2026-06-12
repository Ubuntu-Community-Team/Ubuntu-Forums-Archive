---
title: "Chaining aliases"
date: 2007-12-23
forum: General Help
---

### Post by zephyrus17 on 2007-12-23
How do you chain the aliases?

Basically I want a simple keyword to change the brightness of my Dell 1501.

I need to log in as root first,
[COLOR="Red"]sudo -i[/COLOR]

then change the brightness,
[COLOR="Red"]echo -n 25 > /proc/acpi/video/VGA/LCD/brightness[/COLOR]

How can I chain these up? Also, can I make it so that in this case, the password is automatically entered for me when I enter root?

---

### Post by zephyrus17 on 2007-12-25
Bump.

---

### Post by dagnabit dang doohickey on 2007-12-25
```
alias bright25="sudo sh -c 'echo -n 25 > /proc/acpi/video/VGA/LCD/brightness'"
```

---

### Post by zephyrus17 on 2007-12-25
Brilliant stuff! Thanks!

Oh, what does 'sh' and '-c' do?

---

### Post by nick_h on 2007-12-25
sh runs a shell and the -c option allows you to specify a command to run in it.

---

### Post by zephyrus17 on 2007-12-25
Cool. Thanks a lot, nick. And for the quick reply.

---

