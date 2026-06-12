---
title: "Get x to boot to command line"
date: 2012-12-08
forum: General Help
---

### Post by qazxsw21000 on 2012-12-08
I have two sisters who like using my laptop without permission. I have a password set, but they know what it is. Sometimes I let them use it and I give them the password (because I'm too lazy to type it myself).

I found [this](http://ubuntuforums.org/showthread.php?t=1505769) which is basically what I need. However, that does not drop me to command line automatically. After the text stops changing on the screen, I have to ctrl+alt+F1 to the command line.

Do I have to live with it, or is there an easy fix for it?

---

### Post by Bashing-om on 2012-12-08
The recommended method works flawlessly in my case, I have to ask, Have you followed the directions, running the terminal command;
```
sudo update-grub
``` afterward ?
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by qazxsw21000 on 2012-12-08
Yes, I've done that. Is there a different option I could use besides "text" in the following line that can do what I need?
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

---

### Post by Cheesemill on 2012-12-08
You can use this method instead:

[http://ubuntuforums.org/showpost.php?p=12383337&postcount=2](http://ubuntuforums.org/showpost.php?p=12383337&postcount=2)

---

### Post by JKyleOKC on 2012-12-08
BTW, if you use Cheesemill's suggestion, note that during the login when you type your password, nothing at all will echo to the screen. This gives you the impression that the typing isn't being accepted -- but it is, so just type it in blind and hit Enter. This, in itself, should drive your sisters up the wall, if you never let them discover that it's really working.

---

### Post by Bashing-om on 2012-12-08
I find on my 12.04 the command "startx' does load X, but not the desk top manager;
I have to use from the cli the terminal command:
```
sudo start lightdm
``` followed by my password to start my GUI desktop.

---

### Post by Cheesemill on 2012-12-08
> **Bashing-om said:**
> I find on my 12.04 the command "startx' does load X, but not the desk top manager;
I have to use from the cli the terminal command:
```
sudo start lightdm
``` followed by my password to start my GUI desktop.
What are the contents of your xinitrc file?
```
cat ~/.xinitrc
```

---

### Post by qazxsw21000 on 2012-12-10
> **Cheesemill said:**
> You can use this method instead:

[http://ubuntuforums.org/showpost.php?p=12383337&postcount=2](http://ubuntuforums.org/showpost.php?p=12383337&postcount=2)

That worked. It drops me to the command line automatically now. Thank you.

---

