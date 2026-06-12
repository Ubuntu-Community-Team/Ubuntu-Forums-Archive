---
title: "Midnight commander viewing problem"
date: 2007-05-15
forum: General Help
---

### Post by semka on 2007-05-15
[IMG]http://t.foto.radikal.ru/0705/28/0232ec5ec71a.jpg[/IMG]


Help me please with language...(ubuntu server 6.06 LTS)

---

### Post by stylishpants on 2007-05-15
Probably a bad terminal setting.  

Are you in a Linux virtual console (ie. you pressed something like Ctrl-Alt-F5 and logged in to get a full-screen text-only terminal) or are you using an x terminal program ? (eg. gnome-terminal, konsole, xterm, etc.)

If you're using an X terminal program, which one?

 What is the result of this command:
```
echo $TERM
```

---

### Post by semka on 2007-05-15
i have just installed ubuntu 6.06 LTS , and i have not installed any commander i dont now other commander, help me please with this affichage

---

### Post by semka on 2007-05-15
You can help me with good installation server? Please! i send you login, and password in your Private Messages...

---

### Post by semka on 2007-05-16
Help me please!!!

---

### Post by semka on 2007-05-16
Please HELP ME!!!! :((((((((((((

---

### Post by westli on 2007-05-16
Okay, you're getting a little bit silly here, Semka.  Sometimes answers don't come as quickly as we'd like.  We're users like you, you know.

First, try using Nautilus instead of Midnight Commander.  I think it is automatically installed with your version.  Check under Applications > Accessories or the equivalents in your language.  Or just type Nautilus in a terminal window.

Also check under System > Administration > Language Support.  You can set the default language there, if that is the issue.  I see some corrupted file names in your screenshot.  Maybe that's what you are asking about.

---

### Post by kerry_s on 2007-05-16
Mc was made to run in xterm, it doesn't look like your running it in xterm. Press alt+F2 than type in xterm than in xterm type mc. I think you can also ctrl+alt+F1 and run mc there, ctrl+alt+F7 to get back to gui.

---

### Post by semka on 2007-05-16
i cant type this comman Alt + F2 , because i have connecte via putty (SHELL)...

---

### Post by stylishpants on 2007-05-17
You need to modify the LANG environment variable to use mc over putty.

[http://ubuntuforums.org/showthread.php?p=2673406#post2673406](http://ubuntuforums.org/showthread.php?p=2673406#post2673406)

---

