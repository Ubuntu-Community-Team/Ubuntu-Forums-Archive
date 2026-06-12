---
title: "[SOLVED] &amp;quot;Firefox not installed&amp;quot; after downgrade from 3 to 2"
date: 2008-05-11
forum: General Help
---

### Post by potatan on 2008-05-11
Hi

I have removed Firefox 3 beta completely, then reinstalled Firefox 2 on Hardy 8.04.

Now when I click on a URL in Thunderbird, no browser launches.  I've checked System/Preferences/Preferred Applications, and Web Browser is set to Custom, with "firefox %s" as the command.  However, typing "firefox" into a terminal comes back with:
```
paul@antec:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
paul@antec:~$ 
```

Is there a way to re-associate firefox (v2) with URLs?

Thanks

---

### Post by Vivaldi Gloria on 2008-05-11
My

```
/etc/gnome/defaults.list 
```

file contains the lines

```
...
text/html=firefox.desktop
...
text/xml=firefox.desktop
...

```

If yours is like

```
...
text/html=something_else.desktop
...
text/xml=something_else.desktop
...

```

then try changing "something_else" to "firefox".

---

### Post by potatan on 2008-05-11
No, it's not that - these are the (partial) contents:

```
text/csv=ooo-calc.desktop
**text/html=firefox.desktop**
text/plain=gedit.desktop
text/richtext=abiword.desktop
text/rtf=ooo-writer.desktop
text/spreadsheet=ooo-calc.desktop
text/tab-separated-values=ooo-calc.desktop
text/x-comma-separated-values=ooo-calc.desktop
text/x-chdr=gedit.desktop
text/x-csrc=gedit.desktop
text/x-dtd=gedit.desktop
text/x-java=gedit.desktop
text/mathml=gedit.desktop
text/x-python=gedit.desktop
text/x-sql=gedit.desktop
**text/xml=firefox.desktop**
```

Any further ideas?

By the way, firefox itself works okay - I'm using it now - and the panel icon launches it fine.

Thanks.

---

### Post by potatan on 2008-05-11
Ahh - answered my own question there.  The panel icon properties launch 
```
firefox-2 %u
```

I have changed the Preferred Applications to 
```
firefox-2 %s
```

and it's all back to normal now.

Thanks

---

### Post by Vivaldi Gloria on 2008-05-11
> **potatan said:**
> Ahh - answered my own question there.  The panel icon properties launch 
```
firefox-2 %u
```

I have changed the Preferred Applications to 
```
firefox-2 %s
```

and it's all back to normal now.

Thanks

ur welcome. nice catch there with %s. have fun.

---

