---
title: "[SOLVED] how to add a startup script"
date: 2007-06-01
forum: General Help
---

### Post by uroskriznar on 2007-06-01
I am using feisty fawn Ubuntu.

I would like that this script [COLOR="Blue"]sudo ethtool -s eth0 speed 10 duplex full autoneg off[/COLOR] starts up every time I run Ubuntu.

Is there a graphical interface where I could change this settng (wired network connection)?

I don't have permission to write to init.d folder.

---

### Post by raja on 2007-06-01
You can write it as a bash script and add it to session startup programs. But I guess it will prompt for a password because you have the sudo there.

---

### Post by uroskriznar on 2007-06-02
I am new to Ubuntu so could you please be more specific.

What is a bash script?

---

