---
title: "Window pops up repeteadly with msg &quot;Address book authentication request&quot;"
date: 2013-04-02
forum: General Help
---

### Post by llazarte on 2013-04-02
A window keeps popping up every few minutes with the message "Address book authentication request" and asking for a password.

Googling this string, I see that it belongs to "evolution-data-server". I don't know which password it is expecting and I would like to know if I can safely uninstall this program.

Thanks in advance for any help,
Leonardo

---

### Post by Isamu715 on 2013-04-02
Evolution is a GNOME mail client. If you're not using it it's save to remove.

---

### Post by llazarte on 2013-04-03
Thanks for your answer. As this string belongs to evolution DATA SERVER, I am not sure by which other programs it might be used, neither why it suddenly begun asking for a password (neither which password it is expecting, by the way).

---

### Post by Isamu715 on 2013-04-04
It seems that the data server is indeed separate from Evolution itself. I checked and I have this package installed on my system and it came by default. It's a dependency of the clock applet so removing it might not be a good idea after all. After a quick search I found that it stores some data from calendar, address book, etc. Since it's a GNOME thing my guess is some GNOME app is trying to use it.

Could you provide some additional information about:
1. What Desktop Environment/Shell are you using (GNOME Shell/Unity/KDE/Xfce/LXDE).
2. Do you have any additional GNOME apps installed.
3. If you use anything for calendar, contacts management, what is it.

Since you don't know why it started behaving like this and don't know yourself what password you need to enter it may be a good idea to restore evolution-data-server to default settings.

---

### Post by Guido_A._Paliot_jr. on 2013-08-17
The issue may be caused by deleting an online account, e.g. Google but some configuration remains in evolution or rather evolution data server.
Check ~/.config/evolution/sources for the account that keeps popping up and delete it.

---

