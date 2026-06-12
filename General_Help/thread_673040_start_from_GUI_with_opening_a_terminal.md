---
title: "start from GUI with opening a terminal"
date: 2008-01-20
forum: General Help
---

### Post by frogotronic on 2008-01-20
How do I click on a GUI manu item and have it open from within a terminal?

In other words, can I click a GUI that opens a terminal and then uses a command line?

some programs I'd like to keep an eye on the terminal output.

Thanks,
CH

---

### Post by dabang on 2008-01-20
If you're running gnome, you could run gnome-terminal with "-e" option like this:
```
gnome-terminal -e <command>
```
If you substitute <command> for example with "digikam", a gnome terminal will be launched and from within the terminal digikam with all its output.
To make this permanent just change the starter in gome menu.

---

### Post by aphirst on 2008-01-20
Go to preferences > main menu.

You can edit the options for each menu listing so that it can open in a terminal (it's a check-box).

---

### Post by dabang on 2008-01-20
OK, aphirst had the better idea! :)

---

### Post by frogotronic on 2008-01-20
> **aphirst said:**
> Go to preferences > main menu.

You can edit the options for each menu listing so that it can open in a terminal (it's a check-box).

Awesome, thanks!  I remember knowing this a while ago, but I'd forgotten where the option was!

- CH

---

