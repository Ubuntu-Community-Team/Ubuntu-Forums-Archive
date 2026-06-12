---
title: "Checkmail Problem"
date: 2007-01-14
forum: General Help
---

### Post by tsav87 on 2007-01-14
I installed kcheckmail using Synaptic and I get this error when I run the program. (see attched image)

---

### Post by bruenig on 2007-01-14
Do
```
cat /usr/share/applications/kcheckgmail.desktop
```
and paste the output here.

If I read that error correctly, what it looks like is that the menu entry is bad, so when you try to launch it from the menus, you get that error. You should still be able to run it from the terminal and from the alt + f2 run dialog thing by entering "kcheckmail" without the quotes. If running "kcheckmail" from the terminal gives you that error, then you have a serious problem, but I don't think it will.

---

### Post by tsav87 on 2007-01-14
```
cat: /usr/share/applications/kcheckgmail.desktop: No such file or directory
```

That's the output.

```
[Desktop Entry]
Encoding=UTF-8
Name=KCheckGmail
Name[it]=KCheckGmail
Name[xx]=xxKCheckGmailxx
Comment=A Kicker applet to display how many email messages you have in your Gmail account.
Comment[it]=Un applet del pannello per visualizzare quanti messaggi sono contenuti nel tuo account Gmail.
Comment[xx]=xxKicker applet to display how many email messages you have in your Gmail accountxx
Exec=kcheckgmail
Icon=kcheckgmail
X-KDE-StartupNotify=true
Type=Application
Categories=Qt;KDE;Network

```

That's the output of "cat /usr/share/applications/kde/kcheckgmail.desktop".  I thinkg you forgot the kde/ before kcheckmai.desktop.

---

### Post by bruenig on 2007-01-14
Run "kcheckgmail" in the terminal and see what happens.

---

